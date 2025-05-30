# Git Commands — All-in-One Survival Guide

## Setup

`git config --global user.name "Your Name"` – set your name  
`git config --global user.email "you@example.com"` – set your email  
`git config -l` – list config  
`git init` – start new repo  
`git clone <url>` – copy remote repo to your PC  

## Basic Workflow

`git status` – show what’s going on  
`git add <file>` – stage file  
`git add .` – stage everything  
`git commit -m "msg"` – save snapshot  
`git push` – send to remote  
`git pull` – get latest from remote  
`git fetch` – fetch remote changes without merging  
`git merge <branch>` – merge another branch into current  

## Branches

`git branch` – list branches  
`git branch <name>` – create branch  
`git checkout <name>` – switch branch  
`git checkout -b <name>` – create + switch  
`git branch -d <name>` – delete branch (safe)  
`git branch -D <name>` – delete branch (force)  
`git merge <branch>` – merge branch into current  
`git rebase <branch>` – rebase current onto another  

## Logs & History

`git log` – full history  
`git log --oneline` – short history  
`git log --graph` – see branches visually  
`git show <commit>` – see commit content  
`git diff` – unstaged changes  
`git diff --staged` – staged changes  
`git diff <branch1> <branch2>` – compare branches  

## Stashing

`git stash` – save current dirty state  
`git stash pop` – get it back  
`git stash list` – see saved stashes  
`git stash drop` – delete latest stash  
`git stash clear` – remove all stashes  

## Remote

`git remote -v` – list remotes  
`git remote add origin <url>` – link to remote  
`git push -u origin <branch>` – push & set upstream  
`git remote rename <old> <new>` – rename remote  
`git remote remove <name>` – delete remote  

## Tags

`git tag` – list tags  
`git tag <name>` – create tag  
`git tag -d <name>` – delete tag  
`git push origin <tag>` – push tag  
`git push origin --tags` – push all tags  
`git checkout <tag>` – switch to tag (detached HEAD)  

## Undo / Fix / Panic

### Unstage stuff  
`git reset <file>` – unstage file  
`git reset` – unstage everything  

### Undo last commit (keep changes)  
`git reset --soft HEAD~1`  

### Undo last commit (discard changes)  
`git reset --hard HEAD~1`  

### Recover deleted file  
`git checkout HEAD <file>`  

### Cancel all changes (not committed)  
`git restore .` – undo all  
`git restore <file>` – undo file  

### Cancel everything (back to last commit)  
`git reset --hard HEAD`  

### Revert commit (safe way)  
`git revert <commit>` – creates opposite commit  

## Rewriting History

⚠ Dangerous, don’t use on shared branches

`git commit --amend` – edit last commit  
`git rebase -i HEAD~n` – edit last n commits  
`git reset --hard <commit>` – hard reset to old state  

## Clean Up

`git clean -n` – preview files to delete  
`git clean -f` – delete untracked files  
`git clean -fd` – delete untracked files + folders  

## Collaboration

`git pull origin <branch>` – pull specific branch  
`git push origin <branch>` – push specific branch  
`git fetch origin` – fetch all remote branches  
`git merge origin/<branch>` – merge remote branch  

## Submodules

`git submodule add <repo>` – add submodule  
`git submodule init` – init submodules  
`git submodule update` – pull submodules  
`git submodule foreach git pull` – update all submodules  

## Cherry-pick

`git cherry-pick <commit>` – apply commit to current branch  

## Bisect (Find which commit broke stuff)

```bash
git bisect start
git bisect bad        # current commit is broken
git bisect good <sha> # old good commit
# Git checks commits one by one, you test and tell:
git bisect good
git bisect bad
# until it finds the bad one
git bisect reset      # clean up
