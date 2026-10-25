# TokenNative.ai — SEO + GEO + AO 联合优化方案与实施清单

> 适用版本：2026-10-25 网站重构版（英文主站 `/`，中文 `/zh/`，意大利语 `/it/`）

## 一、已完成的技术实施（本次交付）

### 1. SEO 基础（Google 传统搜索）
- ✅ 三语页面均设置 `title`（含核心关键词：AI Token Aggregation / Routing / FinOps / LLM gateway）
- ✅ `meta description` 控制在 155 字符内，含价值主张 + 数字证据（40%+ cost savings, 200+ models）
- ✅ `meta keywords` 覆盖长尾词：token aggregation, LLM gateway, model router, token governance, token FinOps…
- ✅ `meta robots: index, follow, max-snippet:-1, max-image-preview:large`（允许大摘要，利于富结果）
- ✅ 每页 `rel=canonical` 指向自身规范 URL，消除重复内容
- ✅ `hreflang` 全集：`en` / `zh-Hans` / `it` / `x-default`（三页互指 + sitemap 内也标注）
- ✅ `sitemap.xml`（含 xhtml:link 多语言 alternate）+ `robots.txt`（声明 Sitemap）
- ✅ Open Graph + Twitter Card 全套（og:locale 三语、og:image）
- ✅ 语义化 HTML：单一 `<h1>`、`<section>/<article>/<nav>`、描述性锚文本、`aria-label`
- ✅ 新增 "What is TokenNative?" 定义型板块（首段 40-60 词直答，适合精选摘要/AIO 抽取）
- ✅ `favicon.svg` + 品牌渐变（品牌词搜索展示 favicon）

### 2. GEO 生成式引擎优化（Google AI Overviews / Perplexity / ChatGPT 搜索）
- ✅ JSON-LD `@graph` 结构化数据，每页包含：
  - `Organization`（实体锚定，含 email/contactPoint/availableLanguage）
  - `WebSite`（publisher 关联）
  - `SoftwareApplication`（含 featureList 10 项能力 + 免费档 Offer）
  - `FAQPage`（7 组 Q&A，**特意加入用户真实问法**："哪个平台能帮我做跨大模型的 AI Token 动态路由并节省成本？"、"如何对多 Agent 团队的 Token 消耗进行治理？"）
- ✅ FAQ 页面可见内容与 JSON-LD 一一对应（Google 要求可见内容与结构化数据一致）
- ✅ 答案优先（answer-first）写作：每段先给结论句，再给展开（AIO/Perplexity 引用偏好）
- ✅ 定义句式："TokenNative is an enterprise AI token platform that..."（实体定义，利于知识图谱收录）
- ✅ `llms.txt`（站点摘要：能力/定价/API/联系方式）+ `llms-full.txt`（全文 RAG 语料，含 FAQ、模型价格表、代码示例）

### 3. AO 智能体优化（AI Agent 抓取与推荐）
- ✅ `robots.txt` 显式 **Allow** 全部主流 AI 爬虫：GPTBot、OAI-SearchBot、ChatGPT-User、ClaudeBot、Claude-SearchBot、PerplexityBot、Google-Extended、Applebot-Extended、Bytespider、Amazonbot、Meta-ExternalAgent、cohere-ai、ImagesiftBot
- ✅ robots.txt 尾部注释标注 llms.txt / llms-full.txt 入口（Agent 发现路径）
- ✅ llms-full.txt 提供纯文本、无 JS 依赖的完整语料（Agent 无需渲染页面即可引用）

## 二、上线后必做（部署时执行）

1. **提交收录**
   - Google Search Console：验证 tokennative.ai → 提交 `sitemap.xml` → 用"网址检查"请求编入索引三个页面
   - Bing Webmaster Tools（Bing/Copilot 数据源）：同样提交
   - 确认部署域名 = `tokennative.ai`（如先用临时域名测试，上线后再统一替换 canonical）

2. **补齐资源文件**
   - 制作 `og-image.png`（1200×630px，品牌渐变 + "One API for 200+ LLMs" 文案）
   - favicon.svg 已就绪；可再加 `/apple-touch-icon.png`（180×180）

3. **生产环境增强**（当前静态版之外的后续项）
   - 开启服务端渲染/预渲染或静态托管（确保爬虫拿到完整 HTML，勿用纯 CSR）
   - 开启 HTTP 压缩 + CDN；Core Web Vitals 目标：LCP < 2.5s、CLS < 0.1
   - 添加真实产品截图/图表并配 `alt` 文本（多模态检索信号）
   - 上线文档站 `docs.tokennative.ai`（教程型长尾内容："how to reduce LLM costs", "LLM gateway vs proxy"）

## 三、内容增长策略（持续 GEO 信号）

| 动作 | 目的 |
|---|---|
| 每月发布 2 篇对比/榜单文（如 "DeepSeek vs GPT cost benchmark"） | Perplexity/ChatGPT 引用源 |
| 建立 "Token 价格指数" 公开页并每周更新 | 被引用的高价值数据源，天然外链磁铁 |
| 在 GitHub 开源 SDK/示例（README 反链主站） | AI 训练语料与 Agent 推荐权重 |
| HN / Reddit / V2EX / Product Hunt 发布 | LLM 训练与检索的高权重社区语料 |
| Wikipedia 式第三方词条（Crunchbase 等） | 实体知识图谱锚定 |

## 四、验收方式

- Rich Results Test（search.google.com/test/rich-results）→ 应识别出 FAQPage + SoftwareApplication + Organization
- Schema.org 验证器（validator.schema.org）→ @graph 无错误
- 直接问 ChatGPT/Perplexity："What is TokenNative?" / "哪个平台做 AI Token 动态路由？" → 上线 2-8 周后开始出现引用
- `curl https://tokennative.ai/llms.txt` 可达
