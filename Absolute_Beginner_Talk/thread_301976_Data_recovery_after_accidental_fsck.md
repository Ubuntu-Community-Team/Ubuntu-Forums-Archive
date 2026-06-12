---
title: "Data recovery after accidental fsck"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by greenonion on 2006-11-17
Accidentally ran fsck in rw mode, I thought I had remounted in ro mode, but must have done something wrong. Can anyone tell me if I can recover my data?

---

### Post by eighthate on 2006-11-18
you can with an external HD and a live cd then
assuming your linux partition is hda1,


```
mkdir /media/linuxpart sudo mount /dev/hda1 /media/linuxpart/ -t ext3 -o iocharset=utf8,umask=000
```

Then your files will be visible in /media/linuxpart and you can copy them from there.

If it's not hda1, and you don't knwo what partion it's on, sudo fdisk -l will list them all, and you'll hopefully be able to figure it out from that.

---

### Post by greenonion on 2006-11-18
Thank you thank you thank you

---

