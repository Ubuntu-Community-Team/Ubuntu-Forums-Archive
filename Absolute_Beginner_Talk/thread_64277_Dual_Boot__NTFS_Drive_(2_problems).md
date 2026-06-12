---
title: "Dual Boot / NTFS Drive (2 problems)"
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by Oni-Dracula on 2005-09-10
First of all, let me state that while I have not been using ubuntu for very long, I have fallen in love with it.  It would seem that I will be going farther away from windows as time passes.  However, my windows hard drive has some information, music, pictures, etc that I wish to retrieve - not to mention the games that I would like to play. 

So let me start by explaining my dual booting problems.  I power up my computer, GRUB loads asking me which OS I wish to boot.  Selecting "Windows XP Professional" brings me to a mostly black screen with text which I assume are the "boot commands" for the operating system.  I sit...I wait...nothing happens.  Windows will not boot.  I am almost certain that it still exists on the hard drive.  I do know that I did overwrite the original Windows bootloader with GRUB during the Ubuntu installation, but that shouldn't prevent GRUB from booting windows alltogether.  Any suggestions on this peticular problem?

Second issue:  I wish to mount my two NTFS partitons on my secondary (slave) hard drive that has windows on it.  Problem is, there is no /mnt/hdb1/ or other directory that I know how to mount.  Mister Terminal tells me this when I type "mount":

```
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

```

I don't know if the drive is listed here and I don't know it or I need to do something else to have it mounted. By the way, I am running the Hoary Hedgehog version.

- Thanks in advance for any help you may be able to provide.

---

### Post by cwaldbieser on 2005-09-10
[QUOTE=Oni-Dracula]First of all, let me state that while I have not been using ubuntu for very long, I have fallen in love with it.  It would seem that I will be going farther away from windows as time passes.  However, my windows hard drive has some information, music, pictures, etc that I wish to retrieve - not to mention the games that I would like to play. 

So let me start by explaining my dual booting problems.  I power up my computer, GRUB loads asking me which OS I wish to boot.  Selecting "Windows XP Professional" brings me to a mostly black screen with text which I assume are the "boot commands" for the operating system.  I sit...I wait...nothing happens.  Windows will not boot.  I am almost certain that it still exists on the hard drive.  I do know that I did overwrite the original Windows bootloader with GRUB during the Ubuntu installation, but that shouldn't prevent GRUB from booting windows alltogether.  Any suggestions on this peticular problem?

Second issue:  I wish to mount my two NTFS partitons on my secondary (slave) hard drive that has windows on it.  Problem is, there is no /mnt/hdb1/ or other directory that I know how to mount.  Mister Terminal tells me this when I type "mount":

```
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

```

I don't know if the drive is listed here and I don't know it or I need to do something else to have it mounted. By the way, I am running the Hoary Hedgehog version.

- Thanks in advance for any help you may be able to provide.[/QUOTE]

The "mount" command will only show you filesystems that are already mounted.  Try:
```
$ sudo fdisk -l
``` 
That should give you a list of all the partitions (mounted or not) that the system detects as well as the logical device name and the type of filesystem.

---

### Post by Oni-Dracula on 2005-09-10
okdokie, the drive and partitions are showing up as such:
```

Disk /dev/hdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hdd2            1913       14945   104687572+   f  W95 Ext'd (LBA)
/dev/hdd5            1913       14945   104687541    7  HPFS/NTFS

```

what might I do to get these drives mounted?

---

### Post by aysiu on 2005-09-10
This might help you out:

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

And, just so you know, my XP entry in the /boot/grub/menu.lst file looks like this:

title Microsoft Windows XP Home Edition
	rootnoverify (hd0,0)
	makeactive
	chainloader +1

What does yours look like?

---

### Post by mlomker on 2005-09-10
[QUOTE=Oni-Dracula]Any suggestions on this peticular problem?[/quote]

You'll want to take a look at the /boot/grub/menu.lst file.  Perhaps you could post the portion relating to your XP install?

For the second part, open a terminal prompt:

[b]
su
mkdir /mnt/hdd2
mkdir /mnt/hdd5
echo "/dev/hdd2 /mnt/hdd2 auto defaults 0 0" >> /etc/fstab    
echo "/dev/hdd5 /mnt/hdd5 auto defaults 0 0" >> /etc/fstab   
mount -a
[/b]

That should do it...and they should be there when you reboot.

---

