---
title: "cant mount usb flash drive"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-03-16
I can't use my USB flash drive for some reason it cannot read it when I stick it in. However it works fine in Windows XP. I even reformatted it to be FAT32. Help please!

---

### Post by Najand on 2007-03-16
Use the terminal to mount it manually:

```

sudo mkdir /media/FLASH
sudo mount -t vfat /dev/sda1 /media/FLASH

```
and see if it works or not.

---

### Post by syalam on 2007-03-16
mount: wrong fs type, bad option, bad superblock on /dev/sda1,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so

---

### Post by Najand on 2007-03-16
Are you sure it is FAT32?

---

### Post by syalam on 2007-03-16
im positive, when i check it in windows it says its FAT32, i reformatted it as FAT32 in windows as well.

---

### Post by Najand on 2007-03-16
Change "vfat" to "ntfs" in the command above and see it works or not?
Try to run
```

dmesg | tail

```
after plugging you stick memory to the usb plug. and copy/paste it here.

---

### Post by Pixie25 on 2007-11-01
This problem exits in three out  of three  computers I've upgraded from feisty to gutsy. Update breaks USB auto mount...

UBUNTU masters please find solution to this it's really annoying to re-install, just because this upgrade breaks something so important. I've tried following the solution from [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139070](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139070)
but it doesn't work...
:confused:

---

### Post by Inxsible on 2007-11-01
try using pmount. Look at my signature

---

### Post by Pixie25 on 2007-11-02
Well, I tried with pmount. It works really nice. 
However it's not automatic, and not integrated with Thunar, which still give error.
So now I can mount wia cli, which is fine, and I'm half happy.

Any Idea how to fix mounting wia thunar ?

One more little thing, how do I unmount with pmount ? Couldn't find it in the man page...

---

