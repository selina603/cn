# 系统原理
## 概述
云数据库 MongoDB 支持副本集模式，自动搭建3节点的副本集供用户使用，用户可以直接操作 Primary 和一个 Secondary 节点。

## 业务架构
业务架构如下图：


|名称|描述|
| - | - | 
|控制服务|处理来自用户和后端的请求任务，主要有创建、删除、查询、配置变更、容灾切换、配置修改等任务。|
|监控服务|收集MongoDB实例信息（资源使用和数据库键统计信息等）和物理机信息（资源使用信息和评分等），前者供用户和控制台展现，后者用于管理系统使用。|
|Sentinel|哨兵监控MongoDB实例是否存活，多个哨兵同时工作，当发现实例down掉后，发送failover任务，自动创建新实例，并同步数据。|
|备份服务|自动定时备份，支持用户自定义备份。|
|日志收集|收集MongoDB日志信息。|
|数据迁移|当主从实例都不可用的时候，或者需要克隆在线运行的实例时生成实例。|

## 业务流程




