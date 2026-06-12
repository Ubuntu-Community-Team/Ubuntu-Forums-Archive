---
title: "Portable Photoshop CS2"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Skootle on 2007-04-07
Hi. 

I downloaded Portable Photoshop CS2 and tried installing it with Wine. It extracted all the files correctly to Wine's "c:\Program Files\" but when I try to execute "PhotoshopPortable.exe", I get the following error:

```
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\PortaShopCS2\\Photoshop\\Photoshop.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\PortaShopCS2\\Photoshop\\Photoshop.exe" failed, status c0000135

```

Although "ImagereadyPortable.exe" works perfectly and starts up in literally 4-5 seconds. I've tried clicking on the "Edit In Photoshop" button to see if I could open it up that way, but it starts loading and kind of freezes (it doesn't totally freeze because I can cancel it, but it won't load up PS).

Since ImageReady works, I'm really hoping that it's something really stupid and since I'm a newbie, I don't know how to fix it... :( 

Thanks. :)

---

### Post by xopher on 2007-04-07
> **Skootle said:**
> 
```
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\PortaShopCS2\\Photoshop\\Photoshop.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\PortaShopCS2\\Photoshop\\Photoshop.exe" failed, status c0000135

```

As it tells you, you're missing 'MSVCP71.dll', download it from here:

[http://www.dll-files.com/dllindex/dll-files.shtml?msvcp71](http://www.dll-files.com/dllindex/dll-files.shtml?msvcp71)

---

