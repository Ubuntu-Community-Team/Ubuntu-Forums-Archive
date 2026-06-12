---
title: "Bad format in /etc/fstab"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by DOD1951 on 2006-10-15
I have obviously done something wrong with my fstab. When I boot up I get a msg bad format on line 12 of /etc/fstab.
This is the content of fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/mapper/pdc_hefieaib1 /mnt/raid ext3 defaults,errors=remount-ro 0 1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,fmask=0333,dmask=0222   0       0

I don't understand what is meant by line 12 as there is only 9 lines of text in the fstab. Anyone know what is wrong with above please?

---

### Post by taurus on 2006-10-15
> **DOD1951 said:**
> I have obviously done something wrong with my fstab. When I boot up I get a msg bad format on line 12 of /etc/fstab.
This is the content of fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/mapper/pdc_hefieaib1 /mnt/raid ext3 defaults,errors=remount-ro 0 1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,fmask=0333,dmask=0222   0       0

I don't understand what is meant by line 12 as there is only 9 lines of text in the fstab. Anyone know what is wrong with above please?


Try to remove the fmask=0333 and change the dmask=0222 to umask=0222 from the last line!!!

---

### Post by DOD1951 on 2006-10-15
Changed fstab as suggested. Had no effect still get same message. Good thing is it didn't make it any worse :)

---

### Post by taurus on 2006-10-15
Can you post your new /etc/fstab here again?  Just want to make sure it's good!

---

### Post by DOD1951 on 2006-10-15
New fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/mapper/pdc_hefieaib1 /mnt/raid ext3 defaults,errors=remount-ro 0 1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222   0       0

---

### Post by taurus on 2006-10-15
I suppose there are no empty lines after the last line in /etc/fstab, /dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0!!!

---

### Post by DOD1951 on 2006-10-15
Many thanks for your help Taurus. There was a blank line at end which I would not have even considered until you asked. All is working as it should. Now I just need to understand what the options are in fstab that you suggested I change.

---

### Post by taurus on 2006-10-15
Some scripts don't like to have a blank line at the end of the file but some don't care.  /etc/fstab is the one that is not too happy if you have a blank line at the end...

Glad to hear everything is working for you now.

---

