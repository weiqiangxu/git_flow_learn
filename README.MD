# git flow

[git-workflow如何工作](https://morningspace.github.io/tech/git-workflow-4)


### develop 集成开发多种特性

### feature 基于develp的特性小分支且feature与master分支不会有交集

### release分支 基于develop的分支，主要用于版本发布，最终会合并入master发布版本，release代表的是当前版本，而develop继续往前迭代代表的是下一个版本

### hotfix分支 基于master的分支，主要用于BUG修复且直接合并进master

> feature 是基于 develp 且只能 rebase develop , develop 也会不定期 rebase master分支


# Start git flow tool

[git flow cli tool](https://github.com/nvie/gitflow)

```
apt-get update
apt-get install git-flow
```

```
# version tag prefix default 'v' && others default
# 初始化后除了master分支还会多了一个develop分支并且自动切换到develop分支
git flow init -f
```

### feature 特性分支

```
git flow feature start ${feature_name}

#coding

git commit 

git push origin feature/${feature_name}

# 自动将feature分支合并到develop分支
git flow feature finish ${feature_name}
```

### hotfix 

```
# start hotfix
git flow hotfix start ${hot_fix_name}
...

git commit 

# 会把 hotfix 分支节点合并到本地 master 分支和 develop 节点
# 然后自行手动删除hotfix分支并且切换至devlop分支
git flow hotfix finish ${hot_fix_name}

#注意:git flow 只允许有一个hotfix分支存在，需要删除分支才可以重新start

```

# release
```
git flow release start ${release_name}

# 会自动把release分支合并到master和develop并在master为当前版本加上tag
git flow release finish ${release_name}
```

