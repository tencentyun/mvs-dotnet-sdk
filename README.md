# tencentyun-cos-dotnet-sdk
dotnet sdk for [腾讯云对象存储服务](http://wiki.qcloud.com/wiki/COS%E4%BA%A7%E5%93%81%E4%BB%8B%E7%BB%8D)

## 安装（直接下载源码集成）

### 直接下载源码集成
从github下载源码装入到您的程序中
调用请参考示例

## 修改配置
修改Program.cs内的appid等信息为您的配置

## 上传、查询、删除程序示例
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using QCloud.VideoApi.Api;
using QCloud.VideoApi.Common;
using Newtonsoft.Json;
using Newtonsoft.Json.Linq;

namespace QCloud.VideoApi
{
    class Program
    {
        const int APP_ID = 10000000;
        const string SECRET_ID = "SECRET_ID";
        const string SECRET_KEY = "SECRET_KEY";
        static void Main(string[] args)
        {

            try
            {
                var result = "";
                var bucketName = "test";
                var video = new VideoCloud(APP_ID, SECRET_ID, SECRET_KEY);
                var start = DateTime.Now.ToUnixTime();
                //result = video.GetFolderList(bucketName, "/", 20, "", 0, FolderPattern.Both);
                //result = video.CreateFolder(bucketName, "/sdk/");
                //result = video.UploadFile(bucketName, "/sdk/3863.MOV", @"C:\3863.MOV", "test video", "hahahaha", "houhouhou", "aaaaa");
                //result = video.UpdateFile(bucketName, "/sdk/3863.MOV", "test file");
                //result = video.GetFileStat(bucketName, "/sdk/3863.MOV");
                //result = video.UpdateFolder(bucketName, "/sdk/", "test folder");
                //result = video.GetFolderStat(bucketName, "/sdk/");
                //result = video.DeleteFile(bucketName, "/sdk/3863.MOV");
                //result = video.DeleteFolder(bucketName, "/sdk/");
                result = video.SliceUploadFile(bucketName, "/[电影天堂www.dy2018.net].720p.BD中英双字幕.Scared.Shrekless.rmvb", @"E:\QQDownload\[电影天堂www.dy2018.net].720p.BD中英双字幕.Scared.Shrekless.rmvb");
                var end = DateTime.Now.ToUnixTime();
                Console.WriteLine(result);
                Console.WriteLine("总用时：" + (end - start) + "毫秒");
                Console.ReadKey();
            }
            catch (Exception e)
            {
                Console.WriteLine(e.Message);
            }
            Console.ReadKey();
        }
    }
}


```