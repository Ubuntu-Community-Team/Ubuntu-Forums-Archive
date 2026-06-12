---
title: "How do I install Java for Firefox and get automount to work for NTFS?"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by blitz666 on 2005-11-27
My friend pestered me for a while to try Linux, I finally broke down and did so.  He installed Ubuntu 5.10, then left me on my own.  So far, I got some things to work... but having problems with many others.

1) I got flashplayer to work, but despite my best efforts, Java will not.  I got the software straight from Sun, and no matter what faq/walkthru I've seen (all from april) it never works.  How do I get J2re to work in my FF?

2) I mounted my NTFS drive to a folder (/mnt/ntfs) via the /etc/fstab... but every few boots it forgets it is there, and I need to unmount (umount /mnt/ntfs) and then remount (mount -a).  Any way to prevent this?

3) I had something else... but I forgot now... I'll try to remember it.

Please try to talk slow and avoid complicated things... I've only used Ubuntu for about 5 hours now, and have used WinXP since it came out.  (and winme before that, win95 before that, and DOS/Win3.1 before that, so I am very windows minded)

---

### Post by aysiu on 2005-11-27
[QUOTE=blitz666]My friend pestered me for a while to try Linux, I finally broke down and did so.  He installed Ubuntu 5.10, then left me on my own.  So far, I got some things to work... but having problems with many others.[/quote] Some friend! No offense, but that's cruel.

> 
1) I got flashplayer to work, but despite my best efforts, Java will not.  I got the software straight from Sun, and no matter what faq/walkthru I've seen (all from april) it never works.  How do I get J2re to work in my FF? This may help:
[https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249)

> 
2) I mounted my NTFS drive to a folder (/mnt/ntfs) via the /etc/fstab... but every few boots it forgets it is there, and I need to unmount (umount /mnt/ntfs) and then remount (mount -a).  Any way to prevent this? Yes, but keep min mind NTFS is strictly read-only (whereas FAT32 is read/write) in Linux: [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by blitz666 on 2005-11-27
Thanks for checkin on me... unforutuneately, this is all what I've done already.

The first link (JAVA) I tried following the first thing there... tells me it is likely out of date, and thus, will not D/L.  So I followed the rest of the complicated instructions to install Java... it says it is, and yet, I cant use any website that needs the J2re.

As for the second link, that is how I auto-mounted in the first place... I am still curious why occasionally, it forgets it is there.

---

### Post by aysiu on 2005-11-27
[QUOTE=blitz666]Thanks for checkin on me... unforutuneately, this is all what I've done already.

The first link (JAVA) I tried following the first thing there... tells me it is likely out of date, and thus, will not D/L.  So I followed the rest of the complicated instructions to install Java... it says it is, and yet, I cant use any website that needs the J2re.[/quote] I don't really know that much about Java, as I don't use it. Maybe you'd be interested in [Automatix](http://www.ubuntuforums.org/showthread.php?t=80295)?

> 
As for the second link, that is how I auto-mounted in the first place... I am still curious why occasionally, it forgets it is there. Well, there are two links. 

One is entitled "How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only?" The other is entitled "How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?" 

If you're absolutely certain you followed the second set of instructions, let's see what we can do. Can you reboot your computer, open up a terminal (Applications > Accessories > Terminal) and then post the output of these three commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by blitz666 on 2005-11-27
The first:```
Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14215   114181956   83  Linux
/dev/hdb2           14216       14593     3036285    5  Extended
/dev/hdb5           14216       14593     3036253+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS
```

The second:```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1             108G  2.3G  100G   3% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-10-386/volatile
/dev/sda1              75G   34G   41G  46% /mnt/ntfs
```

The third:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /mnt/ntfs       ntfs    nls=utf8,umask=000      0       0
```


I dont mind using someone other than java, as long as it works... I'll look into it now.

EDIT: After looking into it... I'd rather not have anything doing PC stuff for me, its better if I learn.

---

### Post by aysiu on 2005-11-27
It looks good to me.
A few things I noticed, though: ```
/dev/sda1       /mnt/ntfs       ntfs    nls=utf8,umask=000      0       0
``` This line should be umask=0222, not umask=000. That has nothing to do with it automounting or not automounting, but you definitely want NTFS to be read-only in Linux; otherwise, it will become unstable.

/dev/sda1 seems like an external hard drive. A second internal one would probably be /dev/hdb1. Maybe it being an external hard drive has something to do with the automounting problem?

/mnt is a preexisting folder for mounted volumes. Since you're specifying it to mount every time, you may want to try mounting it to a different new folder. For example, I mounted my Windows XP partition to a folder called /xp that I created (not /mnt/xp, just plain old /xp). I don't know for sure if that would make a difference, but it's worth a try.

---

### Post by blitz666 on 2005-11-27
This restart it was fine... as to where it was mounted... blame my friend.  He manually mounted first time, and thus, I made that the auto-mount point... not a bad idea to change it to /XP.

Oh, I remembered the third thing... could someone explain to me clearly how to set up my MX550 Logitech mouse? I read the HowTo on imwheel... got me horribly lost.

---

### Post by aysiu on 2005-11-27
[QUOTE=blitz666]This restart it was fine... as to where it was mounted... blame my friend.  He manually mounted first time, and thus, I made that the auto-mount point... not a bad idea to change it to /XP.[/quote] I'm not 100% sure on this one. I'm just letting you know what works for me.

> 
Oh, I remembered the third thing... could someone explain to me clearly how to set up my MX550 Logitech mouse? I read the HowTo on imwheel... got me horribly lost. No idea on this one.

---

