# 🚀 How to Push Code from VS Code to GitHub

A quick reference guide for creating a repo and pushing/committing files directly from the VS Code terminal using Git and GitHub CLI.

---

## 📋 Prerequisites

- [Git](https://git-scm.com/downloads) installed
- [GitHub CLI (`gh`)](https://cli.github.com/) installed
- A GitHub account

**Install GitHub CLI:**
```bash
# Windows
winget install --id GitHub.cli

# Mac
brew install gh
```

---

## 🔑 Step 1: Login to GitHub (one-time setup)

```bash
gh auth login
```

Follow the prompts:
1. Choose **GitHub.com**
2. Choose **HTTPS**
3. Choose **Login with a web browser**
4. Copy the one-time code shown in terminal
5. Paste it in the browser window that opens

<!-- 📸 SCREENSHOT: gh auth login terminal output -->
![GitHub CLI Login](screenshots\gh-auth-login.png)
![GitHub CLI Connected](screenshots\githubconnected.png)


---

## 📁 Step 2: Open Your Project in VS Code Terminal

Open your project folder in VS Code, then open the terminal:

```
Ctrl + `  (backtick)
```

Navigate to your project folder if needed:
```bash
cd path/to/your/project
```

---

## 🆕 Step 3: Initialize Git (first time only)

```bash
git init
```

<!-- 📸 SCREENSHOT: git init output -->
![Git Init](screenshots/git-init.png)

---

## 🌐 Step 4: Create the GitHub Repository

This creates the repo on GitHub **and** links it to your local folder in one command:

```bash
gh repo create YOUR_REPO_NAME --public --source=. --remote=origin
```

> Replace `YOUR_REPO_NAME` with your desired repo name.
> Use `--private` instead of `--public` for a private repo.

<!-- 📸 SCREENSHOT: repo created confirmation -->
![Repo Created](screenshots\repo-created.png)

---

## 📤 Step 5: Push Your First File

```bash
git add filename.py
git commit -m "Add filename.py"
git branch -M main
git push -u origin main
```

> `git branch -M main` and `-u origin main` are only needed on the **first push**.

<!-- 📸 SCREENSHOT: first push success -->
![First Push](screenshots\push.png)

---

## 🔁 Step 6: Push Additional Files (repeat as needed)

For every new file (or set of changes) after the first push, just run:

```bash
git add filename2.py
git commit -m "Add filename2.py"
git push
```

<!-- 📸 SCREENSHOT: subsequent push -->
![Subsequent Push](screenshots\subsequent-push.png)

---

## ⚡ Quick Reference: Push All Files at Once

Instead of adding files one by one:

```bash
git add .
git commit -m "Initial commit"
git push
```

---

## 🧾 Full Example Sequence

```bash
cd my-project
git init
gh repo create cloud-observability-stack --public --source=. --remote=origin

git add app.py
git commit -m "Add FastAPI backend"
git branch -M main
git push -u origin main

git add dockerfile
git commit -m "Add Dockerfile"
git push
```

---

## 🛡️ Bonus: Add a `.gitignore`

Avoid pushing junk files like `node_modules`, `.env`, or `__pycache__`:

```bash
# Create .gitignore
echo "node_modules/
.env
__pycache__/
*.pyc
.DS_Store" > .gitignore

git add .gitignore
git commit -m "Add .gitignore"
git push
```

---

## 📌 Common Commands Cheat Sheet

| Command | Purpose |
|---|---|
| `git status` | Check what's changed |
| `git add <file>` | Stage a file for commit |
| `git add .` | Stage all changed files |
| `git commit -m "message"` | Save staged changes |
| `git push` | Upload commits to GitHub |
| `git pull` | Download latest changes from GitHub |
| `git log --oneline` | View commit history |

---

### 📷 Adding Screenshots to This README

1. Create a `screenshots/` folder in your repo
2. Save your screenshots there (e.g. `git-init.png`)
3. Reference them like this:
   ```markdown
   ![Description](screenshots\)
   ```
4. Push the screenshots folder along with this README:
   ```bash
   git add screenshots/ HOW_TO_PUSH_TO_GITHUB.md
   git commit -m "Add GitHub push guide with screenshots"
   git push
   ```

---

**Author:** Yuvraj Singh
**Purpose:** Personal reference / explainer for pushing code to GitHub via VS Code terminal