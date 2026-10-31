# Cardbox · Gmail 礼品卡 PIN 提取

本地运行的 Gmail 礼品卡提取工具，提供中文网页界面与 Python 后台。

- Google OAuth 只读登录，支持多个邮箱地址。
- 标题完整短语、整封邮件完整短语和高级 Gmail 搜索。
- 每批最多处理 100 封邮件，支持暂停和继续。
- PIN 分页展示、失败重试和 Excel 导出。

## 启动

安装 Python 3.12 或更新版本，下载仓库后双击 `giftcard/start.cmd`，打开 http://127.0.0.1:8876 。不需要安装第三方 Python 包。

首次使用需在 Google Cloud 创建自己的桌面应用 OAuth 客户端、启用 Gmail API，并在页面导入客户端 JSON。测试模式下，请将要登录的邮箱加入测试用户。

详细配置、匹配规则和数据处理说明见 [使用文档](giftcard/README.md)。

## 验证

```sh
python -m unittest discover -s giftcard -v
node giftcard/test_search.cjs
```

Node.js 仅用于前端搜索逻辑测试，运行程序不需要。

## 本地数据

OAuth 客户端配置存放在 `data/`；邮件快照、导出结果和凭据不随源码发布。授权令牌只存在后台内存中，重启后需要重新登录。关闭后台前请导出需要保留的结果。
