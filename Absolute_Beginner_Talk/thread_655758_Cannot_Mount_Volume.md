---
title: "Cannot Mount Volume"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by kokora on 2008-01-01
Before I switched to Ubuntu,  I used xp pro, sp2, on my Dell Inspiron 6000 laptop. Also, before I completely switched from Windows to Ubuntu, I backed up documents and music files onto dvds. When I tried to mount the disks I used to back up my files to transfer to my home folder, I received this error message:

Cannot mount volume.

Invalid mount option when attempting to mount the volume.

I have tried searching for the solution to my particular problem by googling and searching the message board, but it seemed like they were geared toward issues with NTFS hard drive partitions and dual booting. Can anyone assist me?

---

### Post by blueridgedog on 2008-01-01
Are you trying to mount hard disks or DVD-ROM disks?

What command/action are you using?

Can you post the output of:

sudo fdisk -lu

---

### Post by kokora on 2008-01-01
I am trying to mount DVD-ROM disks.

I am not using command or action. My DVD-drive automatically attempts to mount ny disk inserted.

This is the output of fdisk -lu:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   114190019    57094978+  83  Linux
/dev/sda2       114190020   117210239     1510110    5  Extended
/dev/sda5       114190083   117210239     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   622117124   311058531   83  Linux
/dev/sdb2       622117125   625137344     1510110    5  Extended
/dev/sdb5       622117188   625137344     1510078+  82  Linux swap / Solaris

The first device that shows as Disk /dev/sda is my internal hard disk that I do not use. The second device shown that is indicated as /dev/sdb is my external hard drivethat has 7.10 installed.

---

### Post by blueridgedog on 2008-01-02
OK, thanks.  When you say you backed up your data do you mean you copied data to DVD's or do you mean that you used the backup program in windows to write DVD backups?  If the later, I suspect the format may be different.

I assume other DVDs mount and run normally?

---

### Post by kokora on 2008-01-02
i used the Sonic/Roxio prgram to copy my files to DVDs.  I checked to see of other DVDs and CDs moutn correctly and they do not. When I try to play an audio cd, my laptop freezes. When I try to play other DVDs, they do not mount, but my laptop does not freeze.

---

### Post by thelatinist on 2008-01-02
Please post the results of:

```
sudo cat /etc/fstab
```

---

### Post by zipperback on 2008-01-02
Can your system read other dvd's or does it have a problem with all data disks at the moment?

- zipperback
:popcorn:

---

### Post by kokora on 2008-01-02
My system cannot read any data disks at the moment.

Here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=209a873f-26ad-4d3b-bf2e-07b54177fc50 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=e8bcf974-09e0-439a-ba21-e552a7af009e none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0error-023@

---

