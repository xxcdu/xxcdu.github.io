+++
title = 'hugo'
date = 2024-07-27T01:23:46+08:00
draft = true
+++

条件：配置好git，下载hugo，将hugo所在目录放入环境变量

1、创建网站：hugo new site /path/to/site

2、克隆主题：git clone https://github.com/vaga/hugo-theme-m10c.git themes/m10c
主题网址：https://themes.gohugo.io/

3、启动：hugo server -t m10c --buildDrafts

4、新建文章：hugo new post/test01.md

5、部署到github： hugo --theme=m10c --baseURL="https://xxcdu.github.io/" --buildDrafts
生成一个public文件夹

6、进入public后，传入github：git init
git add .
git commit -m "     "

7、将public远程关联到github：git remote add origin https://github.com/xxcdu/xxcdu.github.io/

8、将public推上去:git push -u origin master

git add时提示“warning: LF(换行) will be replaced by CRLF（回车换行）”：
    1、成因：Dos和Windows平台： 使用回车（CR）和换行（LF）两个字符来结束    一行，回车+换行(CR+LF)，即“\r\n”；
    Mac 和 Linux平台：只使用换行（LF）一个字符来结束一行，即“\n”。。。
        许多 Windows 上的编辑器会悄悄把行尾的换行（LF）字符转换成回车（CR）和换行（LF），或在用户按下 Enter 键时，插入回车（CR）和换行（LF）两个字符
    2、解决：
        一、#提交时转换为LF，检出时转换为CRLF
        $ git config --global core.autocrlf true
        二、纯windows：#提交检出均不转换
        $ git config --global core.autocrlf false


初次运行git时SSL certificate problem: unable to get local issuer ： 
    1、certificate错误的成因：当通过HTTPS访问Git远程仓库的时候，如果服务器上的SSL证书未经过第三方机构认证，git就会报错。
    2、解决方法：需关掉sslverify ：git config --system http.sslverify false（当前用户）git config --global http.sslverify false（全局用户）
    git config http.sslverify false（当前仓库）      
    若嵌套git子模块时遇到：npm config set strict-ssl false