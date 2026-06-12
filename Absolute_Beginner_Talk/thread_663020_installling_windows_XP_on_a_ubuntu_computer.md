---
title: "installling windows XP on a ubuntu computer"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by purplearcanist on 2008-01-09
Hi.

I have a computer that only has Ubuntu Gusty Gibbon on it, and I wanted to install windows XP.  But I want to keep my Ubuntu files.  Is there a way to do this, and make a partition for windows?

---

### Post by OffAxis on 2008-01-09
backup your important files and then...

fire up a livecd and use gparted to resize your linux partition
then install xp
then re-install grub.

when xp is installed it will overwrite the master boot record; that's why you need to re-install grub.

```
sudo grub
```

(and from the grub prompt)
```
root (hd0,1)
setup (hd0)
quit

```

where (hd0,1) is the location and partition of your ubuntu install.
Here's a helpful link:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by purplearcanist on 2008-01-15
Did I hear you correctly that I can install XP without needing to format Ubuntu?  Because that would be great.:KS  I've heard that XP requires the first partition

---

### Post by dstew on 2008-01-15
XP does not absolutely require the first partition. If you put it on another partition, you can use map statements in /boot/grub/menu.lst to fool it into thinking it is on the first partition, and it will boot OK. Windows _does_ need to be on a *primary* partition, however. That is, you cannot put it on a logical partition inside an extended partition.

---

