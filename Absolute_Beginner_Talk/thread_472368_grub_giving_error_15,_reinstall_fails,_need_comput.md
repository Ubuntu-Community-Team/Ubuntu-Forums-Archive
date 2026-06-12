---
title: "grub giving error 15, reinstall fails, need computer to work soon!!!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by salalejo on 2007-06-13
So I forgot both my username and password and the root's password, so thinking I could solve everything, I deleted the ubuntu partition and reinstalled everything.  However, the reinstall sort of went ok except after I came back, the computer was off, I hadn't remembered if Ubuntu had shut it off previously.  So I turn the computer on, and grub gives me a error 15.  So I decide to reinstall again, except this time I actually sit to watch the install and find that after about  60ish percent of the installation of files after I choose partitions and etc., the screen goes black and shows nothing.  What should I do?  This was supposed to be a dual-boot between Ubuntu and XP.  I need to have this computer usable by tomorrow!!!

---

### Post by salalejo on 2007-06-13
help pretty please?

---

### Post by dogatemycomputer on 2007-06-13
> **salalejo said:**
> So I forgot both my username and password and the root's password, so thinking I could solve everything, I deleted the ubuntu partition and reinstalled everything.  However, the reinstall sort of went ok except after I came back, the computer was off, I hadn't remembered if Ubuntu had shut it off previously.  So I turn the computer on, and grub gives me a error 15.  So I decide to reinstall again, except this time I actually sit to watch the install and find that after about  60ish percent of the installation of files after I choose partitions and etc., the screen goes black and shows nothing.  What should I do?  This was supposed to be a dual-boot between Ubuntu and XP.  I need to have this computer usable by tomorrow!!!

Basically error 15 means grub is missing a file somewhere.  If you want help fast then you're better off plugging "grub error 15" into Google and start reading.  There is plenty of help documentation on the net on how to recover from this error.   You should be able to boot the ubuntu/kubuntu liveCD and use Firefox to achieve this goal. 

[http://forums.gentoo.org/viewtopic.php?t=122656](http://forums.gentoo.org/viewtopic.php?t=122656)

```
Grub error 15
After hitting return in the grub prompt you get something similar to this one?
Code:
Booting 'gentoo Linux'

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel (hd0,0)/boot/kernel-2.4.20 root=/dev/hda3 vga=792

Error 15: File not found
Press any key to continue...
info grub wrote:
15 : File not found
This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

If it's the kernel that it's missing (bzImage, kernel...):make sure that the file it is referring to exists on your boot partition.

To find out what the exact name of your kernel is, first boot from the live-cd or into your existing linux installation. Then mount /boot if you've got a seperate partition, or mount / if you don't. Then do the following:
Code:
cd /boot
ls
This will list all the kernels that you've got on your boot partition.

If your kernel is missing make sure that you compiled a kernel either with genkernel or make menuconfig
Code:
 cd /usr/src/linux/
make menuconfig
and you copied it to your boot partition.
Code:
cp /usr/src/linux/arch/[your architecture, e.g. i386]/boot/bzImage /boot/


However if this error is caused while trying to install grub. And is similar to this one:
Code:
grub> root (hd0,0)
 Filesystem type is xfs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
First of all make sure that you changed root(hd0,0) and setup (hd0) according to your systems specifications.

It may also be possible that grub uses other numbers for your drives than your kernel. So although it may be hda it could be that it is not hd0. However usually this is not the case.

Or else give this line a try provided by dirtboy
Code:
grub-install /dev/bootdevice


If all else fails make sure that your partition is not somehow corrupt. Be sure that you are able to great symbolic links.
```

---

### Post by antoz on 2007-06-13
If you desparately need to boot into Windows you will have to restore your MBR. It will get rid of grub of course but if you are going to reinstall anyway it does not matter.
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)  this link tells you how to restore your mbr if this is what you want to do

---

