---
title: "GRUB did not load..."
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by JustDon on 2007-10-15
Wow,  I lost my dual boot when Windows crashed several weeks ago. I finally got around to reloading Ubuntu 6.06 today. When I installed Ubuntu to hda2 (hda1 is Windows, hda3 is swap), GRUB never installed. I did not even get the option. Now all of my documents and stuff that I need for work is stuck on my inaccessible Windows partition.

How can I force GRUB to install and give me the OS option screen at startup?

Oh - I did look over the other GRUB problem threads but none of them seemed the same as mine.

Thanks for the help.

Here is my /boot/grub/menu.lst:

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
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
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Duck2006 on 2007-10-15
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by JustDon on 2007-10-16
Actually - I suppose GRUB does load. I get the screen where I can pick the OS that I want - I just can NOT boot into Windows XP. I can scroll down to XP but when I hit enter it boots right into Ubuntu. I have tried the solution in the above link (copy/paste the XP entry above the automagic entries but this does not work either. It does make XP my top option but I still can't boot into it.

---

### Post by Duck2006 on 2007-10-16
In the terminal run

sudo fdisk -l

and post the output

---

### Post by JustDon on 2007-10-16
> **Duck2006 said:**
> In the terminal run

sudo fdisk -l

and post the output

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3209    25776261    7  HPFS/NTFS
/dev/hda2            3210        9586    51223252+  83  Linux
/dev/hda3            9587        9726     1124550    5  Extended
/dev/hda5            9587        9726     1124518+  82  Linux swap / Solaris

---

### Post by Dr Small on 2007-10-16
It looks like you need to edit /boot/grub/menu.list and edit the entry for Windows XP Home Edition and change:
```
root (hd0,0)
```
to this:
```
root (hd1,0)
```

But I could be wrong, since I have never fooled with grub.
But that shouldn't hurt to try.

Dr Small

---

### Post by Duck2006 on 2007-10-16
Change this

title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

to this


title Microsoft Windows XP Home Edition
root (hd0,0)
makeactive
chainloader +1

---

### Post by JustDon on 2007-10-16
> **Duck2006 said:**
> Change this

title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

to this


title Microsoft Windows XP Home Edition
root (hd0,0)
makeactive
chainloader +1

This did not work either - I changed it exactly as directed.

---

### Post by Duck2006 on 2007-10-16
Have you got the windoze entry befor or after the ubuntu. It sould be at the bottom of the menu.lst

When you boot your system and hilight the xp you can edit it there to see if it is set for (hd0,0)

---

### Post by rsambuca on 2007-10-16
Try changing the Windows entry to this:

title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
makeactive
chainloader +1

---

### Post by JustDon on 2007-10-16
> **rsambuca said:**
> Try changing the Windows entry to this:

title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
makeactive
chainloader +1

Still can't boot into XP... :(

---

### Post by JustDon on 2007-10-16
> **Duck2006 said:**
> Have you got the windoze entry befor or after the ubuntu. It sould be at the bottom of the menu.lst

When you boot your system and hilight the xp you can edit it there to see if it is set for (hd0,0)

Yes - I have XP at the bottom, below the Ubuntu options. When I reboot, highlight Windows XP, and press "E" to edit it IS in fact set to root (hd0,0). Actually under the "E" option I can highlight root (hd0,0), makeactive, OR chainloader+1. I am not sure all of that should be there but it is. I can scroll down and select Win XP but the highlight then just bounces right up to Ubuntu and refused to boot into Windows.

---

### Post by rsambuca on 2007-10-16
This is strange behaviour indeed.  When you are in Ubuntu, can you access your XP partition?  If not, post the output of 

cat /etc/fstab

---

### Post by JustDon on 2007-10-16
> **rsambuca said:**
> This is strange behaviour indeed.  When you are in Ubuntu, can you access your XP partition?  If not, post the output of 

cat /etc/fstab

No, I can not access hda1, here is the output of cat /etc/fstab:

dhatcher2@dhatcher2-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I don't even SEE hda1 in that mix....

---

### Post by Duck2006 on 2007-10-16
Can you mount your hd0 drive?
This sould help

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by rsambuca on 2007-10-16
OK, let's first make sure your XP partition is intact.  First, make a new directory to mount the drive to:
```
sudo mkdir /media/Windows
```Then mount the XP partition to the folder you just created:```
sudo mount /dev/hda1 /media/Windows
```

---

### Post by JustDon on 2007-10-16
> **rsambuca said:**
> OK, let's first make sure your XP partition is intact.  First, make a new directory to mount the drive to:
```
sudo mkdir /media/Windows
```Then mount the XP partition to the folder you just created:```
sudo mount /dev/hda1 /media/Windows
```

dhatcher2@dhatcher2-desktop:~$ sudo mkdir /media/Windows
dhatcher2@dhatcher2-desktop:~$ sudo mount /dev/hda1 /media/Windows
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by rsambuca on 2007-10-16
I think you might consider an fsck on the partition.

---

### Post by JustDon on 2007-10-16
> **rsambuca said:**
> I think you might consider an fsck on the partition.

Errr, stupid question I know but what is an fsck?

---

### Post by rsambuca on 2007-10-16
Not a stupid question.  It checks your drives/partitions for errors.  The 'bad superblock' comment in your previous post has me a little worried.

Open a terminal and enter```
sudo fsck -f /dev/hda1
```It will then check the inodes (whatever they are), blocks, and sizes.

---

### Post by JustDon on 2007-10-16
Thanks for all the help but I am going to have to reformat my hard drive to get back into Windows. I hate it but my job depends on Windows because the software that I use only works on Windows. I have been out of business since yesterday and have to be able to work tomorrow. I will perhaps try again at a later date. Sorry to waste everyone's time trying to help me but I can't mess with it any longer. 

Kids have gotta eat ya know...

---

