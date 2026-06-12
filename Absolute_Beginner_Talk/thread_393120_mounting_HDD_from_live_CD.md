---
title: "mounting HDD from live CD"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by hoosemon61 on 2007-03-25
Can someone tell me how to mount my hard drive when I'm running the live cd? I'd like to be able to sometimes access files without installing Linux.

I have versions of Ubuntu going back to 5.04 I believe, but none can see the HDD.

---

### Post by taurus on 2007-03-25
Is it ntfs, vfat, ext2/ext3, etc.?

---

### Post by hoosemon61 on 2007-03-25
Ntfs

---

### Post by taurus on 2007-03-25
Assuming it's /dev/hda1, do

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
ls -la /media/windows
```

---

### Post by hoosemon61 on 2007-03-25
I believe Hda1 is correct.  Thanks, I'll try it.

---

### Post by hoosemon61 on 2007-03-25
It worked great, thanks for the help!

Hoosemon     :p

---

