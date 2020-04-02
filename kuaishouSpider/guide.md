## 快手爬虫使用说明

### 环境说明

- 安装postman
- 安装mongodb
- 安装newman

### 操作步骤

1.  抖音集合文件（kuaishou.postman_collection.json）导入postman
2.  执行获取作者视频列表接口，将视频列表信息导入mongodb（此处调用的是另外一个项目liteserver提供的接口）
3.  导出postman runner所需的执行文件

```
mongoexport -d kuaishou -c photos -f pid --type csv -o ~/working/testdata/pids.csv
```
4. 启动集合的runer，data属性中导入执行文件

> 备注：如无新的视频变更，执行文件无需变化，可省略2、3步骤。

也可以直接通过newman命令，直接执行：


```
newman run -d pids.csv douyin.postman_collection.json
```


参考链接：
>
> [在Postman脚本中发送请求(pm.sendRequest)](https://www.jianshu.com/p/9481387c7cd7)