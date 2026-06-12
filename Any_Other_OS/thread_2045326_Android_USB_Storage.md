---
title: "Android USB Storage"
date: 2012-08-21
forum: Any Other OS
---

### Post by fuchini on 2012-08-21
Hello, I'm using 12.04

I've searched wuite a while and haven't found anyone with this problem. When I connect my Android phone to my pc and turn on USB storage on the phone Ubuntu mounts my SD and I can access the  files in my SD normally (no problem yet). 

However there is just /dev/sdb, there is no /dev/sdb1. When I connect it in my archlinux machine (and turn on USB storage on the phone) I can't access my files because I don't know how to mount the SD card without /dev/sdb1.

Does anyone know how Ubuntu mounts it or how can I mount it?

---

### Post by fuchini on 2012-08-21
Just tried [this]("http://forum.xda-developers.com/showpost.php?p=14627538&postcount=2"). But no luck.

---

### Post by Ranko Kohime on 2012-08-31
I'm not familiar with Arch, but USB storage somewhat:  It is possible to not partition a flash drive, (which the Android device is effectively acting as), and you actually do want to mount /dev/sdb.

Mounting should be the same, just leave off the number.

---

### Post by fuchini on 2012-09-02
Thanks for answering. I'll try to mount /dev/sdb without any number.

Besides that, I found that this may also be possible with mtpfs.

---

