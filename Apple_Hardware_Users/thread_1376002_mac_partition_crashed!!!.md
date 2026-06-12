---
title: "mac partition crashed!!!"
date: 2010-01-08
forum: Apple Hardware Users
---

### Post by yfn16 on 2010-01-08
My Mac partition just crashed and I would like to backup my documents using my Ubuntu partition. I am able to mount the partition but it says I do not have permission to access the files. Any ideas? I am not able to startup the Mac partition to changes the permission settings. Help!

---

### Post by linuxopjemac on 2010-01-09
as root you can access and copy stuff. Then just copy that whole stuff you need with the -p parameter (to preserve ownership and timestamps, so you can put it back later).

---

