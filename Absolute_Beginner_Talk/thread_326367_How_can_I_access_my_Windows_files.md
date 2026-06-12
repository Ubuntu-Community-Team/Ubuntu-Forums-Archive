---
title: "How can I access my Windows files?"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by mejerry on 2006-12-27
I am totally new to Ubuntu.  I have been using a live CD on my XP laptop and have decided I'd like to change over to Ubuntu.  However, I don't want to lose my Windows (FAT32) files.  Is there any way that I can access or see those files while running on the live CD?

Thanks in advance.

---

### Post by lucky_chouhan on 2006-12-27
if you download ubuntu 6.10 then you automatically access your ntfs partition. if don't access just download ntfs-3g.

---

### Post by herrma29 on 2006-12-27
have a look at this: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html)

---

### Post by taurus on 2006-12-27
Yes, you can access your fat32/vfat partition from the LiveCD.  You just have to mount it.  What partition is it anyway?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by rajeev1204 on 2006-12-27
hi

dont know how from livecd .
but if ready to install
there is an excellent howto here [www.psychocats.net](www.psychocats.net) where u will get full instructions on how to go about it


also remember it is not safe to share ntfs partition with ubuntu as that is xperimental .
NTFS sharing NOT RECOMMENDED !!

FAT32 is completely safe for that and ubuntu can read and write to it.

so best of luck


regards

rajeev

---

### Post by mejerry on 2006-12-28
Thanks for the quick reply.

I am a complete novice.  I don't know how to mount my partitions.  I'm afraid of screwing up my windows files if I do any resizing, mounting or whatever.  My Windows is XP but all FAT32.

---

### Post by taurus on 2006-12-28
Are you still wanting to know how to mount your Windows?  If yes, then I need to see that output again?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by mejerry on 2006-12-28
> **taurus said:**
> Are you still wanting to know how to mount your Windows?  If yes, then I need to see that output again?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

Yes, thank you, I still want to mount my Windows.  What output are you refering to?

---

### Post by taurus on 2006-12-28
Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by mejerry on 2006-12-28
> **taurus said:**
> Are you still wanting to know how to mount your Windows?  If yes, then I need to see that output again?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

Is this the info you mean?

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30005821440 bytes
240 heads, 63 sectors/track, 3876 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3124    23617408+   c  W95 FAT32 (LBA)
/dev/hda2            3125        3876     5685120    f  W95 Ext'd (LBA)
/dev/hda5            3125        3876     5685088+   b  W95 FAT32

---

### Post by taurus on 2006-12-28
From a terminal, Applications -> Accessories -> Terminal, do

```
sudo mkdir /media/hda1 /media/hda5
sudo mount -t vfat /dev/hda1 /media/hda1 -o iocharset=utf8,umask=000
sudo mount -t vfat /dev/hda5 /media/hda5 -o iocharset=utf8,umask=000
df -h
```

---

### Post by mejerry on 2007-01-27
:D Thank you for answering my questions.  It worked and I neglected to thank you.:( 

In the meantime, I have installed Ubuntu and except for crashing the whole thing (my own fault) and having to reinstall, I am much happier than I was with MS.

---

