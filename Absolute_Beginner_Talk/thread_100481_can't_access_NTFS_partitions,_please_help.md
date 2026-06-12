---
title: "can't access NTFS partitions, please help"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by RaiSuli on 2005-12-07
Hi,

just installed Ubuntu on my pc. It's a dual boot system and according to the tutorials I've correctly mounted my 3 NTFS WinXP partitions. I can see them, but can't access them. The error message displayed says that I can't get permission to view the files because I'm not the owner. What do I do now?

Hope that someone can help and sorry, if this is a silly question.

---

### Post by linbetwin on 2005-12-07
Can you post the contents of the file **/etc/fstab** ?

---

### Post by RaiSuli on 2005-12-07
[QUOTE=linbetwin]Can you post the contents of the file **/etc/fstab** ?[/QUOTE]

This should be it:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda9       /home           ext3    defaults        0       2
/dev/hda1       /windows        ntfs    defaults        0       0
/dev/hda10      /windows1       vfat    defaults        0       0
/dev/hda5       /windows2       ntfs    defaults        0       0
/dev/hda6       /windows3       ntfs    defaults        0       0
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by aysiu on 2005-12-07
[QUOTE=RaiSuli]This should be it:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda9       /home           ext3    defaults        0       2
**/dev/hda1       /windows        ntfs    defaults        0       0**
/dev/hda10      /windows1       vfat    defaults        0       0
/dev/hda5       /windows2       ntfs    defaults        0       0
/dev/hda6       /windows3       ntfs    defaults        0       0
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/QUOTE] You don't want you NTFS mounting options to be *default*. Use this line instead ```
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
``` First, though, unmount the appropriate partitions: ```
sudo umount /windows
sudo umount /windows2
sudo umount /windows3
``` Then make a backup copy of your fstab ```
sudo cp /etc/fstab /etc/fstab_backup
``` Then edit fstab with root privileges ```
sudo nano /etc/fstab
``` Replace the appropriate lines and save. Then, ```
sudo mount -a
``` For more info, see [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by RaiSuli on 2005-12-07
That did it! Thanks for your help!:KS

---

