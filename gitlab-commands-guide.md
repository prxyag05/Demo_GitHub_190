# GitLab Commands Guide - Step by Step for Beginners

## Prerequisites
- Git installed on your system
- GitLab account with a repository
- Repository cloned locally
- Command line/Terminal open in your project directory

---

## 1. Push New Branch

### Step 1: Create a new branch locally
```bash
git checkout -b feature/new-feature
```
Replace `feature/new-feature` with your desired branch name.

**What it does:** Creates and switches to a new branch locally

### Step 2: Make changes and stage them
```bash
git status
```
This shows which files have been changed.

### Step 3: Add changes to staging area
```bash
git add .
```
The `.` means add all changes. Or add specific files: `git add filename.txt`

### Step 4: Commit your changes
```bash
git commit -m "Add your commit message here"
```
Example: `git commit -m "Add login feature"`

### Step 5: Push the branch to GitLab
```bash
git push origin feature/new-feature
```
Replace `feature/new-feature` with your branch name.

**What it does:** Sends your branch to the GitLab remote repository

---

## 2. Create Merge Request in GitLab

### Option A: Using Web Interface (Easiest for Beginners)

**Step 1:** Go to your GitLab project in the browser

**Step 2:** Click **Merge requests** in the left sidebar

**Step 3:** Click the **New merge request** button

**Step 4:** Select your branch in the "Source branch" dropdown
- Example: `feature/new-feature`

**Step 5:** Select the target branch in the "Compare" dropdown
- Usually `main` or `master`

**Step 6:** Click **Compare branches and continue**

**Step 7:** Fill in the merge request details:
- **Title:** Brief description of changes
- **Description:** Detailed explanation (optional)
- **Assignee:** Who will review (optional)
- **Labels:** Add labels for organization (optional)

**Step 8:** Click **Create merge request**

### Option B: Using Command Line

```bash
git push origin feature/new-feature
```
Then follow Option A steps 1-8 from the browser.

Note: The MR (Merge Request) must be created in GitLab's web interface. Git commands can't create MRs directly.

---

## 3. Merge Branch

### Option A: Using Web Interface (Recommended for Beginners)

**Step 1:** Go to **Merge requests** in your GitLab project

**Step 2:** Open the merge request you want to merge

**Step 3:** Review the changes and comments

**Step 4:** Click **Merge** button (green button at bottom)

**Step 5:** Optionally check these options:
- **Delete source branch** - Removes the branch after merging
- **Squash commits** - Combines all commits into one

**Step 6:** Click **Merge** to confirm

### Option B: Using Command Line

**Step 1:** Switch to the main branch
```bash
git checkout main
```

**Step 2:** Update main with latest changes
```bash
git pull origin main
```

**Step 3:** Merge your branch into main
```bash
git merge feature/new-feature
```

**Step 4:** Push the merged changes
```bash
git push origin main
```

---

## 4. Delete Branch

### Option A: Delete Remote Branch (on GitLab)

After merging (recommended), delete from GitLab:

```bash
git push origin --delete feature/new-feature
```

**What it does:** Removes the branch from the remote GitLab repository

### Option B: Delete Local Branch

```bash
git branch -d feature/new-feature
```

**What it does:** Removes the branch from your local machine

**Note:** Use `-D` instead of `-d` to force delete without confirmation:
```bash
git branch -D feature/new-feature
```

### Delete Both Local and Remote

```bash
git push origin --delete feature/new-feature
git branch -d feature/new-feature
```

---

## Complete Workflow Example

Here's a complete example from start to finish:

```bash
# 1. Create and switch to new branch
git checkout -b feature/add-login

# 2. Make your changes (create/edit files in your editor)

# 3. Check status
git status

# 4. Stage changes
git add .

# 5. Commit changes
git commit -m "Add login functionality"

# 6. Push branch to GitLab
git push origin feature/add-login

# 7. Create Merge Request in GitLab Web Interface
# (Visit GitLab website and follow "Create Merge Request" steps)

# 8. After merge request is approved and merged in GitLab:

# 9. Delete remote branch
git push origin --delete feature/add-login

# 10. Delete local branch
git branch -d feature/add-login

# 11. Update your local main branch
git checkout main
git pull origin main
```

---

## Useful Commands for Reference

| Command | What it does |
|---------|-------------|
| `git branch` | List all local branches |
| `git branch -a` | List all branches (local and remote) |
| `git status` | Show current changes |
| `git log` | Show commit history |
| `git diff` | Show differences in files |
| `git pull` | Download and merge remote changes |
| `git push` | Upload local changes |

---

## Common Branch Naming Conventions

- `feature/feature-name` - New features
- `bugfix/bug-name` - Bug fixes
- `hotfix/hotfix-name` - Critical urgent fixes
- `docs/doc-name` - Documentation changes
- `test/test-name` - Test additions

Example: `feature/user-authentication`

---

## Tips for Beginners

✅ **Always** create a new branch for each feature/fix
✅ **Write clear** commit messages
✅ **Test** your changes before pushing
✅ **Delete** branches after merging to keep repository clean
✅ **Pull** from main before starting new work: `git pull origin main`
✅ **Review** the merge request before merging

---

## Troubleshooting

**Q: I pushed but don't see the branch in GitLab**
- Wait a moment and refresh
- Check: `git push origin feature/new-feature`

**Q: I made a mistake in my commit**
- Undo last commit: `git reset --soft HEAD~1`
- Then make changes and commit again

**Q: I can't delete a branch**
- It might be your current branch. Switch first: `git checkout main`
- Then delete it

**Q: I forgot to create a branch first**
- Don't worry! Create one now: `git checkout -b feature/name`
- This will capture your changes in a new branch
