---
title: "Dual Boot, Hard Drive Question"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by P0werSquid on 2005-12-01
I put Ubuntu on my hard drive with windows, and partitioned the Ubuntu in the free space and my windows would not work. So, because my friend gave me a hard drive, I installed windows on one hard drive, and ubuntu on another because I can't partition things correctly.

Is there a way for me to dual boot, because it does not give me that option when my computer loads.

(Btw, Ubuntu hard drive is configured to be the master.)

If anyone could help me, or if anyone needs some more information before they could help me that'd be awesome because I really would like a dual boot environment.

---

### Post by aysiu on 2005-12-01
Are you saying your only boot option right now is Ubuntu?
If so, can you post the output of the following commands? ```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by nevelis on 2005-12-01
By default the bootloader is installed, you might want to check /boot/grub/menu.lst for the line:
```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```
The menu might be disappearing before your screen changes resolution, or else change the timeout specified in the *timeout* bit.  Otherwise, there might not be an entry in there for Windows, so try putting in something that looks like this (at the end of the file):

```

title           Microsoft Windows XP Professional (Free Edition)
root            (hd1,0)  # this will do first partition of second drive
savedefault
makeactive
chainloader     +1

```

Grub does not name disks like Linux, so if you had an hda and an hdc for example, they're just numbered as they're found, eg hd0 and hd1 in grub.

Cheers,
Aaron

---

