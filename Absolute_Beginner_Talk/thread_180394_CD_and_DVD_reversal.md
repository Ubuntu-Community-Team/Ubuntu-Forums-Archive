---
title: "CD and DVD reversal"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Cud on 2006-05-22
Hello I have a really bizzare problem. Ubuntu (hoary) has somehow reversed the recognition of my dvd player and cd player. What I mean is that when I type eject hdd ina command line, the cd ejects instead of the dvd. Of course nerolinux isnt functioning either it also ejects the wrong drive, and asks for a cd or dvd for a drive theat already has one inside. both drives functioned perfectly about a week ago. Then I got locked out of windows XP (no activation) (dual boot) and since then ???. Here is FSTAB  

/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home/jesse/Mount_hdb3 ext3    defaults        0       2
/dev/hdb4       /home/jesse/Mount_hdb4 ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/dvd      udf,iso9660 rw,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda1       /media/windows3  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb5       /media/windows2  vfat    iocharset=utf8,umask=000   0       0




ANY IDEAS???

---

### Post by Sef on 2006-05-22
Update to Dapper.  There are a lot of fixes for various bugs.

Was it working ok before and then started to reverse the DVD and CD players?  If so, have you installed anything?  I suspect there is some corruption somewhere.

---

