---
title: "steam with wine"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-07-06
according to [this](http://appdb.winehq.org/appview.php?versionId=1554), steam runs fine with wine, but keep on getting this error
```
fixme:ntdll:FILE_GetNtStatus Converting errno 19 to STATUS_UNSUCCESSFUL
err:virtual:NtMapViewOfSection map_file_into_view 0x760000 145000 000000000 failed

```
does anyone know how to fix this?

---

### Post by trinaryouroboros on 2007-07-06
> **supersonicdarky said:**
> according to [this](http://appdb.winehq.org/appview.php?versionId=1554), steam runs fine with wine, but keep on getting this error
```
fixme:ntdll:FILE_GetNtStatus Converting errno 19 to STATUS_UNSUCCESSFUL
err:virtual:NtMapViewOfSection map_file_into_view 0x760000 145000 000000000 failed

```
does anyone know how to fix this?

Not sure if this helps:

[http://forums.newsbin.com/viewtopic.php?p=122707](http://forums.newsbin.com/viewtopic.php?p=122707)

Different scenario, but, after they upgraded wine the error went away.

Another option is to play around with winecfg and set Steam.exe to use a different operating system.

---

