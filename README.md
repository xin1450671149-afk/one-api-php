# One API PHP版

这是一个基于PHP开发的简易版 One API 系统，支持多渠道模型转发、用户额度管理、充值等功能。

## 安装说明

1. **环境要求**
   - PHP 7.4+ (推荐 8.0+)
   - MySQL 5.7+
   - Web服务器 (Nginx/Apache)

2. **数据库配置**
   - 创建数据库 `one_api` (或其他名称)。
   - 导入 `install.sql` 文件到数据库中。
   - 修改 `config/config.php` 文件，填入正确的数据库连接信息。

3. **Web服务器配置**
   - 将网站根目录指向 `public/` 目录。
   - 配置伪静态规则 (如果使用 Nginx)：
     ```nginx
     location / {
         try_files $uri $uri/ /index.php?$query_string;
     }
     ```
   - 如果使用 Apache，确保 `.htaccess` 生效 (虽然本项目使用了简单的 index.php 路由，但在根目录下直接访问 public 目录可能需要额外配置，建议将 DocumentRoot 指向 public)。

4. **默认账号**
   - 管理员账号：查看开发者文档

## 功能列表

- **前端**
  - 用户注册/登录
  - 仪表盘 (查看余额、额度)
  - 令牌管理 (创建、删除 API Key)
  - 充值 (模拟充值，1:1 比例)
  - 日志查看

- **后端**
  - 管理员登录
  - 渠道管理 (添加 OpenAI/Azure 等渠道，设置计费)
  - 用户管理 (编辑、删除、充值)
  - 日志管理 (查看所有消耗记录)
  - 系统设置 (网站名称、支付开关)

- **API**
  - `/v1/chat/completions`: 兼容 OpenAI 格式的对话接口
  - 支持流式输出 (Stream)
  - 支持按次或按 Token 计费

## 注意事项

- 本项目为纯本地代码，不依赖 CDN。
- 请确保 `public/assets` 目录可访问。
- 生产环境请修改默认管理员密码。
