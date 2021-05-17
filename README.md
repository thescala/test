# 项目推送多个仓库

初始化项目`git init`后添加第一个仓库
```shell
git remote add gitee https://gitee.com/xxx/test.git

```
然后添加第二个仓库
```shell
git remote add githubb https:/github.com/xxx/test.git

```

`git remote add `后面的`gitee`和`github`只是为了区分两个仓库地址代号，可以随便命名

推送代码时，就可以分别推送了 
```shell
git push gitee master
```
```shell
git push github master
```

或者初始化项目后直接在`.git/config`文件里直接修改为下面所示：

```text
[remote "github"]
	url = https://github.com/xxx/test.git
	fetch = +refs/heads/*:refs/remotes/github/*
[remote "gitee"]
	url = https://gitee.com/xxx/test.git
	fetch = +refs/heads/*:refs/remotes/gitee/*
[branch "master"]
	remote = github
	remote = gitee
	merge = refs/heads/master
```
这样就是可以推送代码了