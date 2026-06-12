---
title: "drive mounting"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by kirbydrumm on 2007-10-04
After installing, I realized I didn't mount my "shared" partition as /osshare, or something of the like.  Can I remedy this?  I know it's /dev/hda6.  I image there is some sort of "mount as" facility to fix this?

---

### Post by JustAboutRealJAR on 2007-10-04
what are you sharing it with? a network? another operating system?

if it's a network, you want to use samba

if it's another operating system, it shouldn't be a problem, since they won't be accessing it simultaneously. As long as it's formatted in such as way that both linux and the other OS can read

---

### Post by kirbydrumm on 2007-10-04
It's a FAT32 partition on a Windows XP / Ubuntu dual boot machine.  It's basically there for sharing files between the two OS's.  You're right, no simutaneous access.

I guess I'm a little confused as to the whole mounting thing.  (I'm a windows guy).  I'm guessing that, since it found it, and there was nothing in the partition file to tell it to mount it as /osshare, it just mounted it as /dev/hda6?

It also mounted my windows partition, /dev/hda2.  I would really not even like to know about this from Ubuntu.  I guess another question might be...can I permanently "unmount" this partition so Ubuntu just disregards it on startup?

Thanks for your help.

---

### Post by JustAboutRealJAR on 2007-10-06
sure... to keep ubuntu from mounting a drive on boot-up... just remove it from your fstab file (/etc/fstab)

```
sudo gedit /etc/fstab
```

you don't need mount it as a shared drive, the sharing is kind of an unspoken agreement

---

### Post by bsharp on 2007-10-06
to mount the shared drive to /osshare, type this in a terminal:
```
sudo mount /dev/hda6 /osshare
```

To mount it on startup, just add it to your /etc/fstab as the post above states.

---

