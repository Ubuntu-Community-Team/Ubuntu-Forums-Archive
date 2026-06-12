---
title: "Two entries of Ubuntu in GRUB and other questions"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Charco on 2006-07-24
On the menu it something like this: 

Ubuntu
Ubuntu (safe mode)
Ubuntu
Ubuntu (safe mode)
Other operating systems:
Windows NT/XP
Windows XP Home edition

How do i get rid of the extra ones?

I also get this error when i start up Ubuntu:

LVM Volume groups
Buffer I/O error on device hdd, logical block 1
Buffer I/O error on device hdd, logical block 2
Buffer I/O error on device hdd, logical block 3
Buffer I/O error on device hdd, logical block 4
Buffer I/O error on device hdd, logical block 5
Buffer I/O error on device hdd, logical block 6
Buffer I/O error on device hdd, logical block 7
Buffer I/O error on device hdd, logical block 0

Which really slows up the startup...

I just installed Ubuntu today and there seems to be too many problems. :(
If there's no answer I've pretty much given up on linux and will try to go back to my XP, but I'm having trouble figuring out how to do that either.

If anyone knows how to cleanly uninstall it, please share. I installed Ubuntu into my secondary hard drive which is 80 gigs originally, but i partitioned it 40/40 and installed linux on one of them. Is there a way to get the fully function 80 gigs with my old OS. My comp did not come with a boot disk by the way...

Please help and post anything you know
Thanks in advance for your help.

---

### Post by Third Thoughts on 2006-07-24
> **Charco said:**
> On the menu it something like this: 

Ubuntu
Ubuntu (safe mode)
Ubuntu
Ubuntu (safe mode)
Other operating systems:
Windows NT/XP
Windows XP Home edition

How do i get rid of the extra ones?


```

sudo gedit /boot/grub/menu.lst

``` 
Will open up the grub menu config file in gedit. From there you can edit it to remove one of the entries. Each entry will look something like this.
```

title           Ubuntu, kernel Default
root            (hd0,2)
kernel          /vmlinuz root=/dev/hda5 ro quiet splash
savedefault
boot

```

They'll each be seperated by a single blank line. Just delete all the lines associated with an entry and you won't see it next time at boot.

> 
I also get this error when i start up Ubuntu:

LVM Volume groups
Buffer I/O error on device hdd, logical block 1
Buffer I/O error on device hdd, logical block 2
Buffer I/O error on device hdd, logical block 3
Buffer I/O error on device hdd, logical block 4
Buffer I/O error on device hdd, logical block 5
Buffer I/O error on device hdd, logical block 6
Buffer I/O error on device hdd, logical block 7
Buffer I/O error on device hdd, logical block 0

Which really slows up the startup...


Do you get that with both of the Ubuntu entries? Or just one of them. Also the error message seems to suggest there's something wrong with your hard drive(device hdd, is a hard drive, probably your secondary one since the primary one is usually called hda) Have you run a disk check on it?

> 
I just installed Ubuntu today and there seems to be too many problems. :(

Compared to dealing with viruses, spyware, pop ups, Sony rootkits, and paying for software? :rolleyes: 

> 
If anyone knows how to cleanly uninstall it, please share. I installed Ubuntu into my secondary hard drive which is 80 gigs originally, but i partitioned it 40/40 and installed linux on one of them. Is there a way to get the fully function 80 gigs with my old OS. My comp did not come with a boot disk by the way...


You can format the partition to ntfs. You could use the liveCD and gparted, or you could find another boot CD with partitioning tools on it. I personally use System Rescue CD, but I've heard things about PCLinuxOS cause it has Disk Drake on it. Reformatting the partition will wipe Ubuntu pretty cleanly.

~Andrew S.

---

### Post by Merlintrix on 2006-07-24
do u have 2 different kernels installed on ur system? that could be why u r seeing 2 entries(they should differ in their numbers). if so go to system->administration->synaptic package manager and remove linux-image-'kernel version'.

---

### Post by confused57 on 2006-07-24
If you installed grub to your Windows mbr, deleting the Ubuntu partition will render your system unbootable, unless you reinstall Ubuntu.
You can download the Windows 98SE boot floppy and enter* fdisk /mbr* at the A: prompt, which should restore the Windows mbr.
You can get it here:

[http://www.bootdisk.com/](http://www.bootdisk.com/)

I've never done it myself, but please consider this before you delete the Ubuntu partition.
Here's an excellent link:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Uncle Spellbinder on 2006-07-24
I thought I had the same issue, but as can be seen below, I can apparently boot two different kernels: 2.6.15-26-386  or  2.6.15-23-386. Is this the result of an update? Is it necessary to delete the older kernel. If so, how? 

```
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by az on 2006-07-24
> **Third Thoughts said:**
> Will open up the grub menu config file in gedit. From there you can edit it to remove one of the entries. 

Do not edit your grub.

Remove the linux-image packages you don't need using synaptic or any other package manager.  You only need one.  Keep the most recent one.

---

### Post by Uncle Spellbinder on 2006-07-24
> **azz said:**
> Do not edit your grub.

Remove the linux-image packages you don't need using synaptic or any other package manager.  You only need one.  Keep the most recent one.


Thanks. That did the trick. :-D

```
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Charco on 2006-07-26
Thanks everyone, I fixed the GRUB problem! You saved me from turning back to windows, and I will give linux a chance. Well, the other problem still shows up sometimes though, although less frequently. And my XP seems to start up noticibly slower and i think it might be connected to the LVM problem. :( I alsoam having problems with my DVD and CD-RW drives in both opperating systems. Could this all be connected? Thanks again for the help, its really appreciated.

(p.s. Does anyone know how to install Extended Prefrences for GAIM? It doesn't seem to work for me...)

---

