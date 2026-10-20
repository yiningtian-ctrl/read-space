# 将完整 ReadSpace 提交到现有 GitHub 仓库

这个完整包包含所有 179 个项目文件，包括 `.openai/hosting.json` 和 `.github/workflows/check.yml`。不需要再使用之前的补丁包。

## 推荐：GitHub Desktop，一次提交完整项目

你已经有仓库 https://github.com/yiningtian-ctrl/readspace ，请更新这个仓库，不必重新创建。

1. 从 https://desktop.github.com/ 安装 GitHub Desktop，登录你的 GitHub 账号。
2. 在浏览器打开 https://github.com/yiningtian-ctrl/readspace ，点击绿色 Code → Open with GitHub Desktop。选择一个新的空目录用于克隆，再点击 Clone。不要选择本压缩包的解压目录或原来正在开发的项目目录。
3. 在 GitHub Desktop 确认 Current Repository 是 readspace、Current Branch 是 main。点击 Repository → Show in Explorer，打开刚克隆的仓库文件夹。
4. 解压 ReadSpace-Complete-20261020.zip，打开里面的 readspace 文件夹；这一层能直接看到 package.json、app、components 等。
5. Windows 资源管理器中打开“查看 → 显示 → 隐藏的项目”。在解压出来的 readspace 文件夹内部 Ctrl+A、Ctrl+C，再进入第 3 步的仓库根目录 Ctrl+V；选择替换同名文件。复制的是 readspace 里面的全部内容，不是外层 readspace 文件夹。保留克隆目录原有的 .git 文件夹。
6. 回到 GitHub Desktop，在 Changes 中检查并保留选中本次项目文件的更改。若 .openai/hosting.json 原来缺失，应显示为新增；若先前已经补好，则可能没有这项差异。填写 Summary：Restore complete ReadSpace source。
7. 点击 Commit to main，然后点击上方 Push origin。Commit 只保存到本机，Push 才会上传 GitHub。
8. 刷新 GitHub 的 Code 页面：根目录直接有 package.json，.openai 文件夹内有 hosting.json，.github/workflows 内有 check.yml。在 Actions 页面查看最新一次 Check。

如果 Desktop 显示 Fetch origin 而不是 Push origin，请先确认是否已经提交；没有文件差异时，无需制造一次空提交。

## 完整性检查

必须能在仓库中找到：

- package.json、package-lock.json、vite.config.ts
- .openai/hosting.json（不是根目录的 hosting.json）
- .github/workflows/check.yml
- lib/reading.ts
- hooks/use-discovery-feed.ts
- components/word-english.tsx

hosting.json 的正确内容已包含在这个包中：

```json
{
  "d1": null,
  "r2": null
}
```

## 几个容易混淆的地方

- ZIP 是完整项目的交付文件。仅把 ZIP 上传到 GitHub 不会展开源码，Actions 也不能因此运行项目。先解压，再使用上面的 Desktop 流程提交。
- 本项目超过 100 个文件。GitHub 网页每次最多上传 100 个文件，因此这次建议直接使用 Desktop；不必分批拖拽，也不要在 Actions 页选择模板上传源码。
- Check 工作流会安装依赖、运行单元测试、检查类型并构建。绿色通过表示检查成功，尚未代表网站部署成功。
- 项目含文章订阅、词典和导入等服务端接口，不能直接把完整功能部署到纯静态的 GitHub Pages。
- Queued 表示尚在等待运行；补齐文件并不能保证立刻分配到运行器。只需关注最新一次运行，无需反复提交同样文件。
- 包内不含依赖目录、Git 登录凭据、原站点部署身份或你的个人阅读记录。学习记录可在原站“我的”页面单独导出 JSON 备份。

## 本地运行（可选，提交 GitHub 不要求先做）

安装 Node.js 24，在包含 package.json 的项目文件夹打开终端：

```text
npm ci
npm run dev
```

检查命令：npm test、npm run typecheck、npm run build。

## 官方操作说明

- 克隆到 Desktop：https://docs.github.com/en/desktop/adding-and-cloning-repositories/cloning-a-repository-from-github-to-github-desktop
- Commit 和 Push：https://docs.github.com/en/desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project-in-github-desktop
- 网页上传限制：https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository