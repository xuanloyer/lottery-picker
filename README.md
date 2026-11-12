# 双色球 / 大乐透 选号器

一个纯前端、单文件的选号小工具。只有**双色球**和**大乐透**两个模式，每个模式固定 **5 组**号码。每个号码都能单独改、单独固定；随机时只替换没有固定的号码，抽完仍按升序排列；最后可一键复制成文本。

![界面](screenshots/ssq.png)

## 功能

- **双色球**：红球 6 个（1–33）+ 蓝球 1 个（1–16）
- **大乐透**：前区 5 个（1–35）+ 后区 2 个（1–12）
- 两个模式各 5 组，切换时各自保留，互不影响
- **改号**：点任意号码弹出数字面板；同区已用数字置灰，点数字即选中
- **固定**：
  - 点当前组号码右上角的小锁；
  - 或长按号码；
  - 或点开号码后打开「固定这个号」；
  - 每组还有「全锁 / 全解锁」一键切换
- **随机**：只重抽未固定的号码，固定号原样保留；抽完自动升序
- **收藏夹**：收藏某一组号码，一键写入当前组（写入后全部变为未固定）
- **复制**：详细 / 紧凑两种格式；有空位时自动随机补全再复制
- **自动保存**：号码、固定状态、收藏都保存在浏览器 localStorage
- 浅色主题，手机 / 桌面均可用，**无任何网络请求**

### 界面

| 大乐透选号 | 收藏夹 |
| --- | --- |
| ![大乐透选号](screenshots/dlt-picker.png) | ![收藏夹](screenshots/favorites.png) |

## 使用

直接双击 `index.html`，或部署后手机浏览器打开。

1. 顶部选「双色球 / 大乐透」
2. 点任意号码改号；长按号码或点小锁固定
3. 点「随机」只补未固定的；点「全部随机」一次生成 5 组
4. 满意的组点 ☆ 收藏；收藏夹里选目标组，点「写入」
5. 点「复制 5 组」，得到文本

### 复制格式

详细：

```text
双色球 5注
1. 红 01 05 12 18 23 30 + 蓝 07
2. 红 03 09 14 20 27 32 + 蓝 11
...
```

紧凑：

```text
01 05 12 18 23 30+07
03 09 14 20 27 32+11
...
```

大乐透对应为 `前 ... + 后 ...` 和 `...+...`。

## 项目结构

```text
.
├── index.html            # 应用本体（HTML/CSS/JS 全在一个文件里）
├── favicon.svg           # 浏览器标签图标
├── apple-touch-icon.png  # iOS 添加到主屏幕的图标
├── screenshots/          # README 用的界面截图
├── README.md
├── LICENSE
└── .gitignore
```

## 上传到 GitHub

### 方式一：网页上传（最简单）

1. 在 GitHub 右上角 **+ → New repository**，仓库名填 `lottery-picker`，选 **Public**，不要勾选初始化 README。
2. 进入空仓库，点 **uploading an existing file**。
3. 把本目录里的 `index.html`、`favicon.svg`、`apple-touch-icon.png`、`README.md`、`LICENSE`、`.gitignore` 和 `screenshots/` 一起拖进去。
4. 点 **Commit changes**。

> `index.html` 必须位于仓库**根目录**，不要多套一层文件夹，否则 Pages 首页会 404。

### 方式二：命令行

```bash
cd lottery-picker
git init -b main
git add .
git commit -m "feat: 双色球 / 大乐透选号器"
git remote add origin https://github.com/xuanloyer/lottery-picker.git
git push -u origin main
```

如果首次提交提示没有配置身份：

```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```

> 如果仓库名不叫 `lottery-picker`，把上面的远程地址和下面的 Pages 地址里的 `lottery-picker` 换成实际仓库名。

## 部署到 GitHub Pages

1. 新建一个 **Public** 仓库 `lottery-picker`（如果还没建）。
2. 把本目录的 `index.html`、`favicon.svg`、`apple-touch-icon.png`、`README.md`、`LICENSE`、`.gitignore` 和 `screenshots/` 放到仓库根目录。
3. 仓库 **Settings → Pages → Build and deployment**：
   - Source 选 `Deploy from a branch`
   - Branch 选 `main`，目录选 `/ (root)`
   - 点 **Save**
4. 等 1 分钟左右，访问 <https://xuanloyer.github.io/lottery-picker/>
5. 手机打开后，在浏览器菜单里选「添加到主屏幕」，用起来就像 App。

> 仓库名不是 `lottery-picker` 时，把上面地址里的 `lottery-picker` 换成实际仓库名。

## 数据说明

- 所有号码只存在当前浏览器的 `localStorage`（键名 `lottery-picker-v1`），不会上传。
- 换浏览器、清缓存、无痕模式会丢数据。
- 页面没有任何外部请求，断网也能用。

## 自定义

- 号码范围、每区个数：改 `index.html` 里的 `MODES` 配置。
- 主题色：改 CSS 变量 `--red` / `--blue` / `--orange` / `--accent` 等。
- 标题、提示文案、免责声明：直接在 HTML 里改。

## 免责声明

号码由本地随机生成，仅供娱乐参考，不构成任何购彩建议。请理性购彩。

## 许可证

[MIT License](LICENSE)。如果这是你的个人项目，可以把 `LICENSE` 里的版权人改成你自己的名字。
