- 请求读写权限
```
termux-setup-storage
```

- 创建软链接
```
ln -s sourceDir destDir
```

- 更换清华源
```
sed -i 's@^\(deb.*stable main\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main@' $PREFIX/etc/apt/sources.list
sed -i 's@^\(deb.*games stable\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/game-packages-24 games stable@' $PREFIX/etc/apt/sources.list.d/game.list
sed -i 's@^\(deb.*science stable\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/science-packages-24 science stable@' $PREFIX/etc/apt/sources.list.d/science.list
apt update && apt upgrade
````

- 安装vim-python
```
pkg install vim-python -y
```

- 安装git
```
pkg install git -y
```
```
git config --global user.email "邮箱"
```
```
git config --global user.name "名称"
```

仓库配置  
new repo  
git init  
git add README.md  
git commit -m "first commit"  
git branch -M main  
git remote add origin git@github.com:yzjdev/test.git  
git push -u origin main  

exists repo  
git remote add origin git@github.com:yzjdev/test.git  
git branch -M main  
git push -u origin main  

- 安装ohmyzsh
```
pkg install zsh -y
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

- 安装插件
```
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-completions ~/.oh-my-zsh/custom/plugins/zsh-completions
```

- 定制常用快捷键
```
vim ~/.termux/termux.properties
```
```
extra-keys = [\
	['ESC','/','-','HOME','UP','END','PGUP'], \
	['TAB','CTRL','ALT','LEFT','DOWN','RIGHT','PGDN'],\
	['BACKSLASH','QUOTE','$','`','=',':wq',':q!']\
]
```

- 配置环境变量
```
vim $PREFIX/etc/profile
```

- 压缩tar.xz包
```
XZ_OPT=-9e tar -cvJf xxx.tar.xz dir
```

- 解压tar.xz包
```
tar -xvJf xxx.tar.xz -C destDir
```

- 压缩tar.bz2包
```
tar -jcvf xxx.tar.bz2 dir
```

- 解压tar.bz2包
```
tar -jxvf xxx.tar.bz2
```

```
-f: 必须且为最后一个参数
-c: 建立压缩档案
-x: 解压
-t: 查看
-v: 显示所有过程
-z: 有gzip属性的
-C: 解压到指定目录
```

- 搭建hexo并部署到github
    - 创建仓库 yourname.github.io
    
    - 安装hexo
    ```
    npm install -g hexo-cli
    hexo init blog && cd blog && npm install && npm install hexo-deployer-git --save
    ```
    
    - 安装ssh，将生成的id_rsa.pub内容复制到github的SSH中
    ```
    pkg install openssh -y
    ssh-keygen -t rsa -C "邮箱"
    ```
    
   - 配置hexo
   ```
   vim _config.yml
   deploy
     type: git
     repo: Github仓库的ssh地址
   ```
