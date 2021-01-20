# 让Github的README.md完美显示大图

##  先看转换前后的效果对比

![before-txt](https://raw.githubusercontent.com/zhaoolee/replace_readme_md_image/master/README/16103285371581AYcXCjy.gif)

![after-txt](https://raw.githubusercontent.com/zhaoolee/replace_readme_md_image/master/README/16103285404102M7PFrwA.gif)

本项目永久更新地址

[https://github.com/zhaoolee/replace_readme_md_image](https://github.com/zhaoolee/replace_readme_md_image)

##  痛点: Github的README.md展示图片效果并不完美

为了让项目演示更生动形象, 我们可以往README.md中插入一些图片

但Github会对README.md中的站外图片会进行地址转换,如果图片尺寸很小,这种转换完全没有问题, 但如果图片尺寸稍大, github的只能转换出半张图, 图片展示的效果极差

比如 将`https://v2fy.com/asset/bilibili_wallpaper/3203841-ee56972a7e14ff43.png`转换为`https://camo.githubusercontent.com/e2b664d80ebe666681016c66d2b42ee9f8f9ec3e6c73d3a34accdaadba84b23a/687474703a2f2f763266792e636f6d2f61737365742f62696c6962696c695f77616c6c70617065722f333230333834312d656535363937326137653134666634332e706e67`

![re-img-kk](https://raw.githubusercontent.com/zhaoolee/replace_readme_md_image/master/README/1610273620185zKKRYDmG.gif)

## 原图

![image-20210110174446076](https://raw.githubusercontent.com/zhaoolee/replace_readme_md_image/master/README/1610273620196RMdHJK1N.png)



## 被github转换后的图片

![image-20210110174523700](https://raw.githubusercontent.com/zhaoolee/replace_readme_md_image/master/README/1610273620453w1B3jNPE.png)

## 如何解决README.md中大图展示不完美的问题?

将图片上传的到github即可!

我们可以将README.md中的图片存储到仓库根目录的README文件夹, 然后用图片在github的url, 替换原有的图片链接.

我分析了一下github 仓库中包含图片的url的规则

`https://raw.githubusercontent.com/` + `用户名` + `/` + `仓库名` + `/master/` + `相对仓库根目录的文件夹路径` + `/` + `图片名`;  



如果图片名称为**1610212776529GNazs3pP.gif**, 图片存储在 `zhaoolee`的 `EasyTypora` 仓库的 `README`文件夹下,那它的最终url为

```javascript
https://raw.githubusercontent.com/zhaoolee/EasyTypora/master/README/1610212776529GNazs3pP.gif
```

## 但是手工替换所有的图片太累了, 于是我写了一个自动化的程序

- 程序支持转换网络图片为github路径
- 程序支持转换本地路径图片为github路径
- 程序自动读取仓库下的`.git/config`,获取用户名和仓库名称
- 自动判断前缀, 对于已经转换的图片, 重复运行程序无需重新爬取,节约流量!


## 如何使用本项目

如果是Windows平台，将dist文件夹下的 `replace-readme-md-image-win.exe` 放入项目根目录，双击运行 ,即可；

如果是Mac平台，将dist文件夹下的`replace-readme-md-image-mac.command`  放入项目根目录，通过命令行进入项目，在命令行运行 `chmod 777 replace-readme-md-image-mac.command && ./replace-readme-md-image-mac.command` ,即可；

如果是Linux平台，将dist文件夹下的 `replace-readme-md-image-linux.sh` 放入项目根目录， 通过命令行进入项目，在命令行运行 `chmod 777 replace-readme-md-image-linux.sh && ./replace-readme-md-image-linux.sh` ,即可；


## 最终效果对比


#### 图片替换前: 图片显示有好有坏,能否显示,全凭运气


![re-img-kk](https://raw.githubusercontent.com/zhaoolee/replace_readme_md_image/master/README/1610273620185zKKRYDmG.gif)


#### 图片替换后: 所有大图正常显示!

![bilibili-wallpaper-005](https://raw.githubusercontent.com/zhaoolee/replace_readme_md_image/master/README/16102767579577iDsT3A4.gif)