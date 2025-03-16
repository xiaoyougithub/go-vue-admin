# go-vue-admin

go-vue-admin is an open-source backend management system based on Go language. Features reference [RuoYi website](http://www.ruoyi.vip/), with frontend and backend separation.

## Introduction

- Frontend uses Vue3, [Element Plus](https://element-plus.org/zh-CN/), [RuoYi-Vue3](https://gitee.com/y_project/RuoYi-Vue)
- Backend uses GoFrame framework, MySQL, Redis, JWT
- Implements one-click generation of frontend and backend code for efficient development.

##  Built-in Features

1. User Management: Users are system operators, this feature mainly completes system user configuration.
2. Department Management: Configure system organizational structure (company, department, team), tree structure display supports data permissions.
3. Position Management: Configure positions held by system users.
4. Menu Management: Configure system menus, operation permissions, button permission identifiers, etc.
5. Role Management: Role menu permission assignment, setting role-based data scope permission division by organization.
6. Dictionary Management: Maintain frequently used, relatively fixed data in the system.
7. Parameter Management: Maintain commonly used dynamic configuration parameters for the system.
8. Notifications and Announcements: System notification and announcement publishing and maintenance.
9. Operation Logs: System normal operation log recording and querying; system exception information log recording and querying.
10. Login Logs: System login log recording and querying, including login exceptions.
11. Online Users: Monitor active user status in the current system.
12. Scheduled Tasks: Online (add, modify, delete) task scheduling including execution result logs.
13. Code Generation: Generate frontend and backend code (Go, JS, Vue) with CRUD download support.
14. System Interface: Automatically generate relevant API documentation based on business code.
15. Service Monitoring: Monitor current system CPU, memory, disk, stack, and other related information.
16. Cache Monitoring: Query system cache information, command statistics, etc.
17. Online Builder: Drag form elements to generate corresponding HTML code.
18. Connection Pool Monitoring: Monitor current system database connection pool status, can analyze SQL to identify system performance bottlenecks.

##  System Requirements

Golang: Go 1.18+ 

Database: MySQL 5.7+

Cache: Redis 3.0+

Node: 12+

## Project Addresses

GitHub:

https://github.com/guyan0319/go-vue-admin

Gitee (China):

https://gitee.com/jason0319/go-vue-admin

## Quick Start

1. Clone project source code

`git clone https://github.com/guyan0319/go-vue-admin`

2. Install Yarn

```
npm install -g yarn 
```

3. Create a database named "gvadmindb" and import the file from manifest/sql/gvadmindb.sql

Database and Redis configuration in manifest/config/config.yaml:

```
# Database.
database:
  logger:
    level:   "all"
    stdout:  true
    Path: "resource/log/sql"

  default:
    link:   "mysql:root:123456@tcp(127.0.0.1:3306)/gvadmindb?charset=utf8mb4&parseTime=true&loc=Local"
    debug:  true
    charset: "utf8mb4" #Database encoding
    dryRun: false #Dry run
    maxIdle: 10 #Maximum idle connections in connection pool
    maxOpen: 10 #Maximum open connections in connection pool
    maxLifetime: "30s" #(In seconds) Time duration for connection object reuse
# Redis configuration example
redis:
  # Single instance configuration
  default:
    address: 127.0.0.1:6379
    db: 1
    pass:    "password" # Configure password here, remove if none
    idleTimeout: "60s" #Maximum idle time for connection, use time string e.g. 30s/1m/1d
    maxConnLifetime: "90s" #Maximum connection lifetime, use time string e.g. 30s/1m/1d
    waitTimeout: "60s" #Timeout for waiting for a connection from the pool, use time string e.g. 30s/1m/1d
    dialTimeout: "30s" #TCP connection timeout, use time string e.g. 30s/1m/1d
    readTimeout: "30s" #TCP Read operation timeout, use time string e.g. 30s/1m/1d
    writeTimeout: "30s" #TCP Write operation timeout, use time string e.g. 30s/1m/1d
    maxActive: 100

```

4. Start the backend server

```
go run main.go
```

For development environment with hot reload, use:

```
gf run main.go
```

5. Start the frontend, open the RuoYi-Vue3 directory

```
yarn dev 
```

6. Open in browser

```
http://localhost/login?redirect=/index
```

Login test account information:

Account: admin

Password: admin123

## Acknowledgements

- GoFrame <https://github.com/gogf/gf>

- RuoYi-Vue3 https://gitee.com/y_project/RuoYi-Vue

## Notes

In developer mode, login does not verify captcha, any characters can be used.

For production environment, remove the comment before //gmode.SetProduct()