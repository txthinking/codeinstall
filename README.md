# CodeInstall (Beta)

```
User --> https://your.website.com/download.your.app?code=xxx --> Install APP --> APP gets the code
```

> Contact cloud@txthinking.com to get the APPID

## Web

1. import codeinstall.js

    ```
    <script src="https://cdn.jsdelivr.net/gh/txthinking/codeinstall@master/codeinstall.js"></script>
    ```

2. Example

    ```
    <html>
        <head>
            <script src="https://cdn.jsdelivr.net/gh/txthinking/codeinstall@master/codeinstall.js"></script>
        </head>
        <body>
            <button id="download" style="font-size:100px;">Loading...</button>
        </body>
        <script>
           async function a(){
                try{
                    var link = await CodeInstall('APPID');
                    document.querySelector('#download').innerText = "Download";
                    document.querySelector('#download').addEventListener('click', ()=>{
                        location.href = link;
                    });
                }catch(e){
                    alert(`${e}`);
                }
            }
            a();
        </script>
    </html>
    ```

## Android

1. Download SDK: [codeinstallsdk.aar](codeinstallsdk.aar)

    Tips：targetSdkVersion <= 29

2. Example

    ```
    import codeinstallsdk.Codeinstallsdk;
    import android.os.Build;

    ...

    try{
        Codeinstallsdk.init();
        String code = Codeinstallsdk.get("APPID", Build.VERSION.RELEASE, Build.MODEL);
        // code comes from the web; or empty string if expired or not found; please cache it
    } catch (Exception e) {
        //
    }

    ```

## iOS

1. Download SDK: [Codeinstallsdk.framework](Codeinstallsdk.framework.zip)

2. Example

    ```
    import Codeinstallsdk
    import UIKit

    ...

    CodeinstallsdkInit()
    var err: NSError? = nil
    var code = CodeinstallsdkGet("APPID", UIDevice.current.systemVersion, "iPhone", &err)
    if err != nil {
        //
        return
    }
    // code comes from the web; or empty string if expired or not found; please cache it
    ```

## Demo(Android)

> 1234 can be any string

[https://txthinking.github.io/codeinstall/demo.html?code=1234](https://txthinking.github.io/codeinstall/demo.html?code=1234)
