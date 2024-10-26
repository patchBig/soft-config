# github

## 本地推送配置

### 生成 SSH 密钥

`ssh-keygen -t rsa -b 4096 -C "your@email.com"`

### 添加 SSH 密钥到 GitHub
`cat ~/.ssh/id_rsa.pub`

### github ssh 密钥配置

打开 `github` 个人设置，点击 `SSH and GPG keys`，然后 `New SSH key`，填入 `title`，在 `key` 文本框里粘贴 `id_rsa.pub` 文件的内容，点击 Add SSH key。

### 推送配置

```bash
git remote add origin git@github.com:username/repository.git
git push -u origin main
```

## 问题

### 权限

`Permission to username/repository.git denied to username.`

```bash
git push -u origin main
remote: Permission to username/repository.git denied to username.
fatal: unable to access 'https://github.com/username/repository.git/': The requested URL returned error: 403
```

解决方案

```bash
git remote set-url origin git@github.com:username/repository.git
```
### 分支

`error: src refspec main does not match any`

```bash
git push -u origin main
error: src refspec main does not match any
error: failed to push some refs to 'git@github.com:username/repository.git'
```
解决方案：
```bash
git checkout -b main
git push --set-upstream origin main
```