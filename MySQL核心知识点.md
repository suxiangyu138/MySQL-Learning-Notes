# MySQL 核心知识点学习笔记
> 项目地址：https://github.com/suxiangyu138/MySQL-Learning-Notes
> 学习目标：Java后端开发必备MySQL知识体系，适配面试+业务开发

## 1. 数据库基础概念
### 1.1 什么是MySQL
- MySQL是开源关系型数据库，采用C/S架构，支持多平台，是Java后端最常用数据库
- 核心特点：开源免费、性能稳定、支持事务、适配大数据量业务场景

### 1.2 核心术语
- 数据库(DataBase)：数据集合，对应一个业务模块
- 数据表(Table)：二维表结构，存储实体数据
- 字段(Column)：表中列，对应实体属性
- 记录(Row)：表中行，对应实体对象

## 2. MySQL基础语法（企业高频）
### 2.1 DDL（数据定义语言）
```sql
-- 创建数据库
CREATE DATABASE IF NOT EXISTS java_shop DEFAULT CHARACTER SET utf8mb4;

-- 创建用户表（适配Java实体映射）
CREATE TABLE IF NOT EXISTS `sys_user` (
  `id` BIGINT PRIMARY KEY AUTO_INCREMENT COMMENT '主键ID',
  `username` VARCHAR(50) NOT NULL COMMENT '用户名',
  `password` VARCHAR(100) NOT NULL COMMENT '密码',
  `phone` VARCHAR(20) COMMENT '手机号',
  `create_time` DATETIME DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='系统用户表';

-- 插入数据
INSERT INTO sys_user (username, password, phone) 
VALUES ('zhangsan', '123456', '13800138000');

-- 更新数据
UPDATE sys_user SET phone='13900139000' WHERE id=1;

-- 删除数据
DELETE FROM sys_user WHERE id=1;

-- 基础查询
SELECT id, username FROM sys_user WHERE id>0;

-- 分页查询（Java后端高频）
SELECT * FROM sys_user LIMIT 10 OFFSET 0;

-- 排序查询
SELECT * FROM sys_user ORDER BY create_time DESC;
