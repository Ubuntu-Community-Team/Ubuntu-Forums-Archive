---
title: "[SOLVED] problem with swap"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-03-20
I am having a problem with making a swap. I using the LiveCD and I am trying to use fdisk, then make the filesystem. Then use the mkswap command, but I get this error: ```
root@ubuntu:/home/ubuntu# mkswap /dev/sda3
/dev/sda3: Device or resource busy

```. What is causing that? How can I stop it?

---

### Post by sisco311 on 2008-03-20
Try to unmount the partition first:
```
sudo umount /dev/sda3
```

---

### Post by forestpixie on 2008-03-20
believe that the livecd will use swap if it's present - so it's mounted thus you can't work with it, are you sure you haven't got swap already

---

### Post by slughappy1 on 2008-03-20
```
root@ubuntu:/home/ubuntu# umount /dev/sda3
umount: /dev/sda3: not mounted

```

---

