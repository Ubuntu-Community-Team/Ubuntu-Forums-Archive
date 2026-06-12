---
title: "Grub error 17; not been able to resolve"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by apathos on 2007-08-25
It all started by trying to redo my partitions so I could have a separate /home partition.  I guess that's pointless now.

I removed all of my ubuntu partitions, not fully intentionally.

I have a 200+ GB HDD, with Windows XP Media Center 2005 on the front, and had ubuntu on the back, in 3 partitions.

Anyway, now ubuntu is gone, I think.  Windows is there, and runs fine, but I have to access it through the recovery disk, since GRUB is dead.

When I run the live ubuntu CD, and run gparted, it does not recognize any partitions, and sees the whole ~240GB disk as unallocated.  But like I said, my full Windows install is still there, and is actually covering about 120 GB.

Questions: Is it possible that ubuntu is actually still there, too, and I can't find it?

How do I fix this GRUB error (error 17 and hang)?  I have read many ideas from fdisk to fixmbr, but I have not been successful in getting them to operate, let alone see if they fix the problem.

When it's all said and done, I'd be happy to just have Windows boot right with grub operating fine, and then I can reinstall ubuntu if I need to.  In fact, if I just had Windows boot right and do a clean start over, that'd be great too.  

Thanks for the help!

---

### Post by pizzutz on 2007-08-25
Well, Let's see if we can help you.  Are you able to boot up with the ubuntu live cd?  if so could you post the output of the following 2 commands, so I can start to figure out where you stuff may be?

```

sudo fdisk -l
sudo mount

```


Strange that gparted is showing the whole thing as unallocated, since there seems to be some data there somewhere.  I will do what I can to help you save what you can.

---

### Post by apathos on 2007-08-25
Well, here it is.  Hope it helps.

**ubuntu@ubuntu:~$ sudo fdisk -l**
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         701       15290   117194175    7  HPFS/NTFS
/dev/sda2               1         700     5622718+   b  W95 FAT32
/dev/sda3           15291       30401   121379107+   5  Extended

Partition table entries are not in disk order


**ubuntu@ubuntu:~$ sudo mount**
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdf1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077)

---

### Post by capt scroggins on 2007-08-26
Can't help you with finding your data/partitions but check this link to try and get rid of the GRUB Error 17.
[http://ubuntuforums.org/showthread.php?t=517844](http://ubuntuforums.org/showthread.php?t=517844)

---

### Post by TonyPursell on 2007-08-26
It look like your Linux partitions are gone.

Grub boots from the MBR in the first partition and tries to hand control over to Stage 2 in  '/boot/grub' on the now non-existent root partition.  This give the message 'error 17'.  If it can load stage 2 the message  would be 'Error 17 : Cannot mount selected partition' in full.

You can read about GRUB at [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html).

As Grub took over the MBR for its own use, you will need to restore the MBR as described here [http://answers.google.com/answers/threadview?id=215902](http://answers.google.com/answers/threadview?id=215902)

Good luck

Tony

---

### Post by apathos on 2007-08-27
Well, the problem with trying to restore the MBR is I don't have an original Windows CD, just the restore disk from Gateway.  When I try to put that in, it wants to repair my install automatically.  At least, I can't find any way to get it to restore the MBR.

Is there an alternative way to restore GRUB or the MBR?

---

### Post by apathos on 2007-08-28
UPDATE: I was able to restore the Windows MBR by using Super GRUB Disk.  Now that that is fixed, I thought I'd try to re-install Ubuntu.  But both the default partitioner and GParted both say that my entire disk is 'unallocated'.  What course of action do I take now?

---

### Post by hvollebregt on 2008-03-06
I was able to resolve grub stage1.5 error 17 by using the Ubuntu live CD. Boot from the CD, then enter the rescue process. When you quit the re-installation process, you will enter a menu. Select 'Re-install Grub' (or something like that, I don't exactly remember) and re-install it to (hd0). This worked for me.

Good luck, Hans

---

### Post by Dithers on 2008-03-11
To fix the grub 17 error "caused by media direct" and put everything back exactly how it was without reinstalling anything

[COLOR="Red"]boot your computer with a Knoppix live CD[/COLOR] "does not work with ubuntu live cd"

in terminal run

[COLOR="Blue"]sudo fdisk -lu[/COLOR]

[COLOR="Red"]check the name of the partition that was changed to fat32[/COLOR] "may be different in knoppix"

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/hda1   *          63   153693854    76846896   c  W95 FAT32 (LBA)[/COLOR]
/dev/hda2       153693855   156296384     1301265    5  Extended
/dev/hda5       153693918   156296384     1301233+  82  Linux swap / 

[COLOR="Blue"]sudo fdisk /dev/hda[/COLOR] "or HD name"

[COLOR="Red"]Command (m for help): m[/COLOR] "Type m for menu or just type t"

[COLOR="Red"]Partition number (1-5): 1[/COLOR] "type partition number"

[COLOR="Red"]Hex code (type L to list codes):[/COLOR] "83 for linux or l for list to choose"

[COLOR="Red"]Command (m for help): m[/COLOR] "type w to write to partition or type m for list"

changes will not take effect in knoppix, restart and your ubuntu will start as normal with no grub 17 error

---

