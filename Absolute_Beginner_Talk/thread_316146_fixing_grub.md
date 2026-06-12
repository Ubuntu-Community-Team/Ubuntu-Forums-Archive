---
title: "fixing grub"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by SVWander on 2006-12-10
Somehow when resurrecting XP which is on the master 40 gig hard drive I messed up the MBR or something because I can know longer boot to my 10 gig drive that has Ubuntu on it. Because it was a clean drive I thought I could just reinstall the Ubuntu but it still booted into XP. So disconnected the primary hard drive and connected the slave as the master but still it wouldn't boot . . . hmm, is that part of the problem? Is the record on the 40 gig drive?

Anyway, I used Ubuntu live to get into the files and typed gksudo gedit /boot/grub/menu.lst The file that comes up in empty of course because grub has a subdirectory grub/i386-pc/ but even there there isn't menu.lst. 

How do I fix this problem? Should I reconnect the primary hard drive before trying to fix the boot record . . . 

Thank you, Tim

---

### Post by mr_samsonov on 2006-12-10
Does your computer boot directly into Win XP? If you change your bios to boot into the Ubuntu drive, what if anything happens? 

I had troubles with my grub the other day and I think I was told that the same information should be on both disks with regards to the MBR and grub.

---

### Post by mr_samsonov on 2006-12-10
If its any help here is a copy of my menu.lst file

```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by smoker on 2006-12-10
when you reinstalled windows looks like you wiped the grub portion from the mbr. try reinstalling grub on the link below:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

i think you need your two drives connected to set this up, and you repair grub from the live-cd

good luck

---

### Post by bulldog on 2006-12-10
Connect the slave drive with ubuntu as your master boot device and make the windows drive the slave.
Install GRUB on your ubuntu drive (hd0) and make a little change to the windows entry [mapping the drives]

Now you can start ubuntu and windows as well from your GRUB,and in case of trouble you can start windows by changing the boot order in the BIOS.

Let me know what you think about it.

---

### Post by SVWander on 2006-12-10
> **smoker said:**
> when you reinstalled windows looks like you wiped the grub portion from the mbr. try reinstalling grub on the link below:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

i think you need your two drives connected to set this up, and you repair grub from the live-cd

good luck

I read many of the six pages of comments of the thread above but I got more and more confused. I was able to get into grub however it is only "looking" at the CD live and not at either of my hard drives. I went through various methods listed to mount the other drives but now I am totally confused. Getting this to work might be beyond my skills. Maybe it would be best to delete the grub and start over. Is there away of doing that so I can reinstall Ubuntu to my secondary drive?

Tim

---

### Post by bulldog on 2006-12-10
GRUB is probably on the other drive.
But read what I wrote to you.
If you want it that way,let me know,otherwise set the 40GB as boot device and reinstall GRUB with the live cd.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

