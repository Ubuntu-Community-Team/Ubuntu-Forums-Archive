---
title: "Cannot eject USB drive"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-04-22
Hi,

I've a little problem: I'm using Feisty Fawn (fresh install) and cannot eject a USB external drive from the desktop. Normally I can right click one of the partition on the USB drive (the are automatically mounted and dsplayed on the desktop when hot plugged) and select "eject" and it would unmount/eject the volumes. Now if I do that I get an error message: "Cannot eject volume".

However the weird thing is that I can eject the USB drive (sdb) from the terminal with **eject /dev/sdb**. I can also unmount individual partitions on it by typing **sudo umount /dev/sdb2** for example

Does anyone know why I can't eject the volume from the desktop but can do it from the terminal?? Is there anyway to correct this?

Thanks




Here is my fstab (sda is my internal drive, not the USB drive. The USB drive doesn't appear in fstab)
:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=87a903b2-6723-4a14-b16b-c99356e4928c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=8222f627-cfb9-4d63-a965-134afda520da /home           ext3    defaults        0       2
# /dev/sda2
UUID=A0DC7EB4DC7E8476 /media/winxp    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=f3eed72f-39e2-4d0a-8330-f3531672314e none            swap    sw              0       0

Here is my mtab (in red: partitions on my USB disk. 2 partitions are FAT32, one is FAT16 and one is EXT3.....but this doesn't seem to be the cause of the problem since I can unmount/eject correctly from terminal):

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
/dev/sda6 /home ext3 rw 0 0
/dev/sda2 /media/winxp ntfs rw,nls=utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=kilou 0 0
[COLOR="Red"]/dev/sdb3 /media/disk ext3 rw,noexec,nosuid,nodev 0 0
/dev/sdb2 /media/LIVEUSB vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
/dev/sdb6 /media/USB2 vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
/dev/sdb5 /media/USB1 vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0[/COLOR]
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by kilou on 2007-04-22
I thought the problem came from permissions because I didn't have rights on the ext3 partition (mounted as /media/disk) on the USB disk. However after doing sudo chmod 777 -R /media/disk I got rights on that partition as well but I still cannot eject the volume from Desktop :(


EDIT: sounds like it's a common problem [https://bugs.launchpad.net/ubuntu/+bug/99538](https://bugs.launchpad.net/ubuntu/+bug/99538)

---

### Post by Xamindar on 2007-04-22
Yeah I have this problem too but sadly they ignored it when I posted about it in the beta thread.  I don't think they read that thread because none of the problems I have with feisty were fixed.

---

### Post by kilou on 2007-04-22
Yes it's a weird problem since it works perfectly from the terminal. Someone showed that it's the status of the USB disk that causes problem because it's set as "non removable". I hope someone can get a fix soon.

I think it will be fixed soon because virtually everyone with USB disks or flash drives is experiencing the problem.

---

### Post by Xarok on 2007-04-22
Yeah I get the same problem. 
I'm using Fiesty on an iBookG4.
  
I can NOT eject: 
- digital cameras
- the Mac OS X partition
- usb flash drives 
- usb external drives
- firewire external drives

basically everything so far...

haven't tried the terminal yet

---

### Post by arron on 2007-04-22
Yes, I have the same problem with a USB ide drive, 2 USB camera's (usb wire) and a USB stick.  Is this being looked at, it is very annoying.

---

### Post by kilou on 2007-04-24
Yes it's being looked at since there is a bug file issued and apparently there is another thread in the general section on this forum. I think it happen only in Gnome, I tried Kubuntu and could correctly remove my USB disk :confused: I hope there is a fix soon.

---

### Post by ramjet_1953 on 2007-04-24
If you follow this link:

[http://ubuntuforums.org/showthread.php?t=418688&highlight=USB+HDD](http://ubuntuforums.org/showthread.php?t=418688&highlight=USB+HDD)

evilc seems to have it sussed-out. It worked for me.

Just cut and paste the command into a terminal and the problem goes away.

Regards,
Roger 8)

---

### Post by Xamindar on 2007-04-25
> **ramjet_1953 said:**
>  sussed-out.

Sussed-out?  Sorry, you lost me there.  What country are you from?:) 

Thanks for the info!

---

### Post by matthew on 2007-04-25
> **Xamindar said:**
> Sussed-out?  Sorry, you lost me there.  What country are you from?:) 
It means "[analyzed]("http://www.wordwebonline.com/en/SUSSOUT")." It's British slang, but I've heard Americans use it.

---

### Post by Amenemhet on 2007-04-25
Beg to differ lad, 'sussed, I first heard while living in NZ and the Britsdo use it as well, where it started who knows, probably british. But, it means 'figured out' or 'fixed' etc, not analysed. To use it as analysed, you would say, ' I was/tried to suss it out' hehe  class of slang 101 dismissed for the day ;)

---

### Post by lepz on 2007-04-25
> **ramjet_1953 said:**
> If you follow this link:

[http://ubuntuforums.org/showthread.php?t=418688&highlight=USB+HDD](http://ubuntuforums.org/showthread.php?t=418688&highlight=USB+HDD)

evilc seems to have it sussed-out. It worked for me.

Just cut and paste the command into a terminal and the problem goes away.

Regards,
Roger 8)

Thanks ramjet and evilc for that, I was having the same problem.

---

### Post by gh0st on 2007-04-27
I was just about to post a new thread about this problem but luckily I searched first and found this thread. I'm gonna try that fix now. Thanks guys, once again the Ubuntu Forums prove to be the best tech support I've ever had :)

P.S - I am British and can confirm that the term "sussed" or "sussed out" means fixed, sorted or solved and not analysed. I dunno where it comes from but it's been around as long as I can remember. Hope that solves the International slang barrier ;)

---

