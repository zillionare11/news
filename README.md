# ☀️ 科技 × 金融早报

> 面向中文读者的「美股/港股/A股 + AI/半导体/机器人」每日晨报

自动生成的科技金融早报，通过 GitHub Actions 每日自动更新，托管于 GitHub Pages。

## ✨ 功能特性

- 🤖 **全自动更新**：GitHub Actions 每天北京时间 08:00 自动生成
- 📱 **响应式设计**：移动端自适应，阅读体验佳
- 📚 **历史存档**：自动保存每日早报，随时回看往期内容
- 🎨 **精美排版**：清晰的信息层级，3 分钟读懂关键变化
- 🔌 **可扩展**：支持接入新闻 API、AI 模型等扩展功能
- 📦 **零依赖**：纯静态 HTML，无需服务器

## 📁 项目结构

```
morning-brief/
├── index.html                  # 今日早报（首页）
├── archive/                    # 历史存档目录
│   ├── index.html              # 存档索引页
│   └── morning-brief-YYYY-MM-DD.html
├── scripts/
│   └── generate_brief.py       # 早报生成脚本
├── .github/
│   └── workflows/
│       └── daily-update.yml    # GitHub Actions 工作流
├── requirements.txt            # Python 依赖
└── README.md                   # 项目说明
```

## 🚀 快速开始

### 1. Fork 本仓库

点击右上角的 **Fork** 按钮，将本仓库复制到你的 GitHub 账号下。

### 2. 开启 GitHub Pages

1. 进入仓库 → **Settings** → **Pages**
2. Source 选择 **GitHub Actions**
3. 保存设置

### 3. 手动触发一次（可选）

进入仓库 → **Actions** → **每日早报自动更新** → **Run workflow** → 选择 main 分支 → 点击运行

### 4. 访问你的早报

部署完成后，访问地址为：
```
https://<你的用户名>.github.io/<仓库名>/
```

## ⚙️ 配置说明

### 修改更新时间

编辑 `.github/workflows/daily-update.yml` 中的 cron 表达式：

```yaml
schedule:
  - cron: '0 0 * * *'  # UTC 时间，北京时间 = UTC + 8
```

常用时间参考：
| 北京时间 | UTC 时间 | cron 表达式 |
|---------|---------|------------|
| 08:00   | 00:00   | `0 0 * * *` |
| 09:00   | 01:00   | `0 1 * * *` |
| 07:30   | 23:30 (前一天) | `30 23 * * *` |

### 接入真实新闻数据（可选）

脚本目前使用示例数据，如需接入实时新闻：

1. 注册 [NewsAPI](https://newsapi.org/) 或其他新闻服务
2. 在仓库 **Settings → Secrets and variables → Actions** 中添加 `NEWS_API_KEY`
3. 修改 `scripts/generate_brief.py`，添加 API 调用逻辑

## 🛠️ 本地开发

```bash
# 克隆仓库
git clone https://github.com/<你的用户名>/<仓库名>.git
cd morning-brief

# 运行生成脚本
python3 scripts/generate_brief.py

# 本地预览（任选其一）
python3 -m http.server 8080
# 然后访问 http://localhost:8080
```

## 📝 自定义

### 修改样式

所有 CSS 都在 `index.html` 的 `<style>` 标签内，修改 `:root` 变量即可快速换肤：

```css
:root{
  --bg:#f6f8fb;       /* 背景色 */
  --card:#ffffff;     /* 卡片背景 */
  --ink:#1a2330;      /* 主文字色 */
  --accent:#1f6feb;   /* 主题色 */
  --green:#1a9d5a;    /* 利好色 */
  --red:#d23b3b;      /* 利无色 */
}
```

### 修改内容结构

直接编辑 `index.html` 中的内容板块，可增删金融/科技新闻条目、市场数据等。

## 📄 许可证

MIT License

## ⚠️ 免责声明

本早报内容仅供信息参考，不构成任何投资建议。投资决策请咨询专业人士，风险自负。

---

⭐ 如果这个项目对你有帮助，欢迎点个 Star！
