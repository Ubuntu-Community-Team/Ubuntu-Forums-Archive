---
title: "anyone know anything about mounting a dvd drive?"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by GonZo1323 on 2006-09-07
just installed a dvd drive and ubuntu wont detect it when i go to burn, does it need to be mounted software updated?

---

### Post by GonZo1323 on 2006-09-07
bump

---

### Post by BLTicklemonster on 2006-09-07
Be patient, someone will come along with an answer soon.

In the meantime, click on Applications, go to Accessories, then click on Terminal.

Type in this: sudo gedit /etc/fstab then press enter (duh) then your password.

copy and paste your info that ought to look like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5 /tmp/disks-conf-hda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdc        /               ext3    defaults,errors=remount-ro 0       1 
/dev/hdb1 /tmp/disks-conf-hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0

here.

See the line:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
?

if yours doesn't have that in there, then try adding it, save, then .. something. Um, look and see if it worked. I don't think you have to reboot for this to work.

(of course, if it worked, then you don't really have to copy and paste anything here at all)

Hope that helps. Post back if you get it working!

---

### Post by GonZo1323 on 2006-09-07
sry i bumped it so soon im at work and time really drags
but once i get home toniight i will try that and post back with results

---

