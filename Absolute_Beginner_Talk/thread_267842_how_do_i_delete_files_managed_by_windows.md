---
title: "how do i delete files managed by windows"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-09-29
hi! i'm completely new to linux! i;m using Kubuntu...my question would be how to delete files created while being under Windows...a friend told me that the problem might be the fact that the windows partitions are mounted as roots and i don't have the proper priviliges...what is the solution?

---

### Post by Kilz on 2006-09-29
> **mendingo84 said:**
> hi! i'm completely new to linux! i;m using Kubuntu...my question would be how to delete files created while being under Windows...a friend told me that the problem might be the fact that the windows partitions are mounted as roots and i don't have the proper priviliges...what is the solution?
I seriously would recommend not deleting files on ntfs partitions. Someone will probably link to a way. But to my knowledge they are mostly beta software that is not ready to be used on production machines. If you can afford to lose the contents of the entire drive go ahead. If not , don't try it.
You could make a small fat32 partition to share files between safly. If not , just copy it over and delete the old one next time you boot to windows.

---

### Post by doggie on 2006-09-29
right now linux only supports ntfs reading... but... if you really want to enable the write support (do it at your own risk :twisted: ) you should read this guide...

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

