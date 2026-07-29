---
title: Hexo写新文章+发布步骤
date: 2026-07-28 10:24:26
tags: [学习，Hexo]
---
一、新建博客文章
打开 CMD，定位在 D:\myblog
执行这条命令创建文章：
bash
运行
hexo new "文章标题"
文件位置
生成的文章在这里：
D:\myblog\source\_posts\你的文章标题.md
用记事本 / VS Code 打开这个 .md 文件。
书写规则
文件顶部是文章配置（不要删除）
markdown
title: 我的第二篇博客
date: 2026-07-29 18:00:00
tags: [学习,Hexo]
categories: 随笔
---

这里下面写正文内容，使用Markdown语法
可以写文字、插入图片、列表等
--- 上面是配置，下面才是网页展示的正文。写完保存文件。
二、本地预览（推荐！先看效果再发布）
CMD 执行：
bash
运行
hexo g && hexo s
浏览器打开 http://localhost:4000
查看你的博客，确认排版、图片没有问题。
三、生成静态网页 + 推送到 GitHub 上线（核心发布流程）
以防hexo d 会卡住，使用这套稳定命令
bash
运行
hexo clean && hexo g
cd public
git add .
git commit -m "新增文章：xxx"
git push -f origin gh-pages
![alt text](image-2.png)
终端最后一行：
* [new branch] gh-pages -> gh-pages
代表网页文件已经全部上传到 GitHub 仓库的 gh-pages 分支。
步骤拆解
hexo clean && hexo g：清理旧网页，重新生成全部网站文件
cd public：进入网页文件夹
git add .：记录所有改动
git commit -m "描述"：填写更新备注，随便写
git push -f origin gh-pages：强制推送到 GitHub 博客分支
1.点击页面上方 Settings
2.在左侧找到 Pages
3.配置：
   Source：Deploy from a branch
   Branch：选择 gh-pages
   Folder：/(root)
点击保存(save)。
![alt text](image-1.png)
四、等待网站更新
推送命令跑完没有报错，等待 3～10 分钟
无痕浏览器打开：你所建立的博客网址， 查看新文章。
常用小提示
如果想删除文章：
直接删除 source\_posts 对应的 .md 文件，再完整执行一遍发布命令；
tag 标签、分类写错，直接修改 md 文件内顶部内容；
不要手动修改 public 文件夹内文件！
public 是自动生成的，所有修改只能在 source\_posts 里操作。
五、更新博客固定流程（保存备用）
CMD 执行：
bash
运行
hexo clean && hexo g
cd public
git add .
git commit -m "更新文章"
git push -f origin gh-pages
推送完成后等待几分钟，网站自动更新。
