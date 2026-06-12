---
title: "boot"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by pbman on 2007-05-24
i have win xp installd on a hd
then i installed ubuntu on another seperate hard disk

however wen i turn the comp on there is no option to chose whether i want to boot to xp or ubuntu

how can i get this to work?

thx

---

### Post by digitalbenji on 2007-05-24
what does it boot into first when you turn on your computer?  Does it say hit escape for a boot menu?

Thanks

---

### Post by pbman on 2007-05-24
it boots straight into windows

no message about alternate boots

---

### Post by Seisen on 2007-05-24
What happened is grub was installed on the second hard drive therefore it won't show up. Here is a link to install Windows and Ubuntu on seperate hard drives.

[http://ubuntuforums.org/showthread.php?t=179902]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by pbman on 2007-05-24
i run with 2 satas 
the guide is for a sata and an ide

---

### Post by dstew on 2007-05-24
Probably you did not install grub on the boot drive. You will need to re-install grub. Boot an Ubuntu Live CD, open a terminal window, and type grub. This will get you the grub prompt, **grub>**. Now you can enter commands for grub. For a list of available commands, enter```
grub> help
```What you need to do first is find the partition that contains the grub configuration files.```
grub> find /boot/grub/menu.lst
```It will answer with either "file not found", or with something like (hd0,1). If it says "file not found" we have BIOS issues. If it says (hd0,1) (or something like it) this will become grub's root.```
grub> root (hd0,1)
```The last step puts the grub boot loader into the Master Boot Record of your boot drive, which I assume is (hd0)```
grub> setup (hd0)
```Next, quit grub (type **quit**), take out the CD, and reboot. You should get the grub menu that lets you pick your O.S.

---

### Post by pbman on 2007-05-24
thx will try that

allso for automatix do i need the version for amd64
i run an amd athlon dual core 3800+

---

### Post by pbman on 2007-05-24
im running that scan
it says it may take a while but its been an hour already and still done nothing

any ideas?

---

### Post by phoenix23 on 2007-05-24
> It will answer with either "file not found", or with something like (hd0,1). If it says "file not found" we have BIOS issues.
This seems to be the problem I am having. I get the "file not found" error.

How do I resolve these BIOS problems? BIOS sees my 500 GB, and it is set on auto. What am I missing?

---

### Post by psusi on 2007-05-24
What does sudo fdisk -l say?

---

### Post by phoenix23 on 2007-05-24
I'm not entirely sure what it means, but...

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60424   485355748+  83  Linux
/dev/sda2           60425       60801     3028252+   5  Extended
/dev/sda5           60425       60801     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


---

### Post by psusi on 2007-05-24
Ok, you have a standard ubuntu only single disk configuration.  See if your bios has an option for LBA disk access.

---

