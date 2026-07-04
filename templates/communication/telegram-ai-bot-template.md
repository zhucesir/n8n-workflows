

# 🤖 Telegram AI 机器人模板

# 概述
一个完整的 Telegram 机器人模板，集成了 OpenAI，为用户消息提供智能回复。该模板展示了 n8n 工作流集合中最流行的通信自动化模式。

# 特性

- ✅ **实时消息** 结合 Telegram 集成

- ✅ **AI 驱动的回复** 使用 OpenAI GPT 模型

- ✅ **输入指示器** 以提供更好的用户体验

- ✅ **消息预处理** 用于干净的数据处理

- ✅ **可配置的 AI 设置** (温度、tokens、系统提示词)

- ✅ **错误处理** 和响应管理

# 前置要求

## 所需凭证

1. **Telegram Bot Token**

 

  - 通过 [@BotFather](https://t.me/botfather) 创建机器人

   - 安全地保存您的机器人令牌

2. **OpenAI API Key**

 

  - 从 [OpenAI 平台](https://platform.openai.com/) 获取您的 API 密钥

   - 确保您有足够的额度

## 环境设置

- n8n 实例 (1.0+ 版本)

- 用于 API 调用的网络连接

# 安装指南

## 第 1 步：导入模板

1. 下载 `telegram-ai-bot-template.json`

2. In n8n, go to **Workflows** → **Import from File**

3. 选择下载的模板文件

## 第 2 步：配置凭证

### Telegram 机器人设置

1. 在工作流中，点击 **Telegram Trigger** 节点

2. 转到 **Credentials** 选项卡

3. 使用您的机器人令牌创建新凭证

4. 测试连接

### OpenAI 设置

1. 点击 **OpenAI Chat** 节点

2. 转到 **Credentials** 选项卡

3. 使用您的 API 密钥创建新凭证

4. 测试连接

## 第 3 步：自定义设置

### 机器人行为
Edit the **Bot Settings** node to customize:

- **System Prompt (系统提示词)**: 定义机器人的个性和角色

- **Temperature (温度)**: 控制响应的创造力 (0.0-1.0)

- **Max Tokens (最大Tokens)**: 限制响应长度

### 系统提示词示例
```text

text

# Customer Support Bot
"You are a helpful customer support assistant. Provide friendly, accurate, and concise answers to customer questions."

# Educational Bot
"You are an educational assistant. Help students learn by providing clear explanations, examples, and study tips."

# Business Assistant
"You are a professional business assistant. Provide accurate information about company policies, procedures, and services."
```text

text

## 第 4 步：测试和激活

1. 使用测试按钮 **测试工作流**

2. 在 Telegram 上 **发送消息** 给您的机器人

3. **验证回复** 是否正常工作

4. 满意后 **激活工作流**

# 自定义选项

## 添加命令
要添加斜杠命令 (例如 `/start`, `/help`)：

1. 在 **Preprocess Message** 后添加一个 **Switch** 节点

2. 为不同的命令配置条件

3. 为每个命令创建单独的响应路径

## 添加图像生成
启用图像生成：

1. 添加一个 **OpenAI Image Generation** 节点

2. 为 `/image` 创建一个命令处理程序

3. 通过 **Telegram Send Photo** 节点发送图片

## 添加记忆
要记住对话历史：

1. 添加一个 **Memory Buffer Window** 节点

2. 存储对话上下文

3. 在 AI 提示词中包含之前的消息

## 多语言支持
要支持多种语言：

1. 在 **Preprocess Message** 中检测用户语言

2. 根据语言设置适当的系统提示词

3. 配置 OpenAI 以用户的语言响应

# 疑难解答

## 常见问题

### 机器人无响应

- ✅ 检查 Telegram 机器人令牌是否正确

- ✅ 验证机器人已在 Telegram 中激活

- ✅ 确保工作流在 n8n 中处于激活状态

### OpenAI 错误

- ✅ 验证 API 密钥有效且有额度

- ✅ 检查速率限制和使用配额

- ✅ 确保模型名称正确

### 响应缓慢

- ✅ 减小 max_tokens 以加快响应速度

- ✅ 使用 GPT-3.5-turbo 代替 GPT-4

- ✅ 优化系统提示词长度

## 性能优化

### 响应速度

- 使用 **GPT-3.5-turbo** 以获得更快的响应

- 将 **max_tokens** 设置为 200-300 以进行快速回复

- 缓存常用的回复

### 成本管理

- 监控 OpenAI 使用量和成本

- 设置 token 限制以控制开销

- 使用较短的系统提示词

# 安全考量

## 数据保护

- 🔒 生产环境中 **切勿记录用户消息**

- 🔒 对于 API 密钥 **使用环境变量**

- 🔒 **实施速率限制** 以防止滥用

- 🔒 在处理前 **验证用户输入**

## 隐私

- 🔒 **不要存储个人信息** (除非必要)

- 🔒 **遵守 GDPR** 和隐私法规

- 🔒 向用户 **告知** 数据的使用情况

# 用例

## 客户支持

- 自动处理客户查询

- 常见问题回复

- 工单路由和升级

## 教育

- 学习辅助

- 作业帮助

- 学习伙伴

## 商业

- 潜在客户资格审核

- 预约排期

- 信息提供

## 娱乐

- 互动游戏

- 讲故事

- 问答和测验

# 高级功能

## 分析集成
添加跟踪节点以监控：

- 消息量

- 响应时间

- 用户满意度

## 多渠道支持
扩展支持：

- WhatsApp Business API

- Slack 集成

- Discord 机器人

## AI 模型切换
实现动态模型选择：

- GPT-4 用于复杂查询

- GPT-3.5 用于简单回复

- 针对特定领域的自定义模型

# 支持和更新

## 获取帮助

- 📖 查看 n8n 文档

- 💬 加入 n8n 社区论坛

- 🐛 在 GitHub 上报告问题

## 模板更新
此模板定期更新：

- 新功能和改进

- 安全补丁

- 性能优化

- 兼容性更新

--

-

*Template Version: 1.0

*  
*Last Updated: 2025-01-27

*  
*Compatibility: n8n 1.0+

*
