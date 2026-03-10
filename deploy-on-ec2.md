
* Read this doc if need deploy on EC2.
* This directory store example files that passed on EC2. **./deploy-on-ec2-example**

# Prepare Connection from local to EC2
* Execute in two separated terminal.

```sh
aws ssm start-session \
  --target i-0ab448dcfe2f85def \
  --document-name AWS-StartPortForwardingSession \
  --parameters '{"portNumber":["3000"],"localPortNumber":["3000"]}' \
  --region us-east-1

aws ssm start-session \
  --target i-0ab448dcfe2f85def \
  --document-name AWS-StartPortForwardingSession \
  --parameters '{"portNumber":["7002"],"localPortNumber":["7002"]}' \
  --region us-east-1
```

# Backend
* README.md


# Mysql
* gaming-marketing-db-prep/README.md

(strands-agent-mcp) [ec2-user@ip-172-31-44-24 gaming-marketing-db-prep]$ uv pip install mysql-connector-python
(strands-agent-mcp) [ec2-user@ip-172-31-44-24 gaming-marketing-db-prep]$ uv pip install faker


# MCP server - mysql

* https://github.com/designcomputer/mysql_mcp_server

# 进入 home 目录
cd /home/ec2-user

# 克隆或创建 mysql-mcp 目录
git clone https://github.com/designcomputer/mysql_mcp_server.git mysql-mcp

```sh
cd /home/ec2-user/mysql-mcp && source venv/bin/activate && pip install mysql-connector-python
cd /home/ec2-user/mysql-mcp && source venv/bin/activate && pip install -e .
```

```sh
export MYSQL_HOST=localhost
export MYSQL_PORT=3306
export MYSQL_USER=mcpuser
export MYSQL_PASSWORD=mcppassword
export MYSQL_DATABASE=gaming_marketing
```

```sh
pytest
```

# MCP configuration
* conf/user_mcp_config.json
```json
{
  "8a752b8e": {
    "mysql": {
      "url": "",
      "command": "uv",
      "args": [
        "--directory",
        "/home/ec2-user/mysql-mcp",
        "run",
        "mysql_mcp_server"
      ],
      "env": {
        "MYSQL_HOST": "localhost",
        "MYSQL_PORT": "3306",
        "MYSQL_USER": "mcpuser",
        "MYSQL_PASSWORD": "mcppassword",
        "MYSQL_DATABASE": "gaming_marketing"
      },
      "description": "mysql",
      "token": null
    }
  }
}
```

* User ID such as *8a752b8e*, get it from web page.


# System Prompt
```
You are a professional data analyst. Please generate a comprehensive report for the following topic:(topic). The data is resided in the mys! database, you need to explore the database and discover the table and schemas you need. By these schema you can discover several scenarios that are critical to the business. Also, before doing querying, you can search the web to see typical scenarios you can adopt to making this report. Finally, generate the report as a ma file to the file system.

use mysa! mcp, sequencial thinking mcp, brave search mcp and file system IO tools.
```

# Prompt
```
你有哪些mcp
```

```
那你查询一下mysql
```

```
游戏广告效果分析
```

