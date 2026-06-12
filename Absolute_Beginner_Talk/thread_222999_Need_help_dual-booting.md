---
title: "Need help dual-booting"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by jpe2000 on 2006-07-25
Okay, I have installed PC-BSD on my computer first. I didn't install the boot loader. I figured that Ubuntu would use Grub so I could dual-boot. That didn't happen. How can I get it so I can dual-boot PC-BSD and Ubuntu. Thanks.

---

### Post by jpe2000 on 2006-07-25
Com'on, anyone?

---

### Post by ndyguy on 2006-07-25
> **jpe2000 said:**
> Okay, I have installed PC-BSD on my computer first. I didn't install the boot loader. I figured that Ubuntu would use Grub so I could dual-boot. That didn't happen. How can I get it so I can dual-boot PC-BSD and Ubuntu. Thanks.

You'll need to provide more info.  Are you trying to boot two seperate computers, two hard drives on the same computer, or two partitions on the same hard drive?  What versions of what software are you using?  Did you get any errors?  These _might_ help:

[http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by jpe2000 on 2006-07-25
I'm using the same computer. PC-BSD is on the master hard-drive. Ubuntu is on the slave hard-drive. Ubuntu is using Grub but I cannot figure out how to edit Grub within Ubuntu itself. I would like to know how to do this so I can get PC-BSD working again.

---

### Post by confused57 on 2006-07-25
I'm not familiar with the grub entry for PC-BSD, but here is an excellent grub tutorial:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by catlett on 2006-07-25
You have to know the partition that pc-bsd is on. So enter 
```
sudo fdisk -l
``` To list your partitions. Once you know your partition, edit the grub menu
```
sudo gedit /boot/grub/menu.lst
```
For an example I'll assume pc-bsd is on hd0,0 (grub places a value on 0. So /devhda1 in grub is hd0,0)
once the file opens, scroll to the bottom. Hie enter a couple of times to get some space between the last entry and this one 
```

title        PC-BSD
rootnoverify (hd0,0)
chainloader  +1
boot

```Make sure to save the file by hitting save at the top of gedit.
Reboot and choose the entry. It should boot no problem but if it does, post. There is another way to boot to pc bsd

---

### Post by jpe2000 on 2006-07-25
I got it working. Thanks guys!

---

