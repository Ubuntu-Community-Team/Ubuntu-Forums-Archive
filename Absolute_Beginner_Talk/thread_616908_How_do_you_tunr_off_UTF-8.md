---
title: "How do you tunr off UTF-8?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Dipper on 2007-11-18
I have searched everywhere and cannot find out how to turn off UTF-8.  VDR will not run otherwise.  Does anyone know how to do this?  Is there a tutorial somewhere that explains it in plain English (not German or Spanish or Dutch)?

---

### Post by gsiliceo on 2007-11-18
post the contents of the
/etc/fstab
 file here please

---

### Post by Dipper on 2007-11-19
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=fe7d75ef-bf19-4e66-8bba-b165811c8641 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=7A7B-EE73  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=22024d15-99b7-4b18-bc22-637a3c94f71c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by gsiliceo on 2007-11-19
Now open the file with
> sudo gedit /etc/fstab
Look at this line

> UUID=7A7B-EE73 /windows vfat defaults,utf8,umask=007,gid=46 0 1

Just delete utf8 so it changes to this

> UUID=7A7B-EE73 /windows vfat defaults,umask=007,gid=46 0 1

Save the file
Reboot

---

### Post by jaybombalous on 2007-11-19
whats VDR? ^^^ sounds like this is the solution.

---

### Post by Dipper on 2007-11-19
Thanks for the advice.  But that didn't do the trick.  I still get the message saying to turn off UTF-8 to run VDR. :(

---

### Post by gsiliceo on 2007-11-19
Yeah what is VDR? maybe you can search in the VDR project forums or something like that

---

### Post by Dipper on 2007-11-20
I always use search before posting questions.  A search in Google revealed a site in German.

---

### Post by whazooo on 2007-11-20
> **Dipper said:**
> I always use search before posting questions.  A search in Google revealed a site in German.


[http://devel.reinikainen.net/content/view/40/40/](http://devel.reinikainen.net/content/view/40/40/)
check the bottom of the page

---

