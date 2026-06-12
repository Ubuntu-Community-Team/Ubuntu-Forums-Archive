---
title: "DVD Burner does not display"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-07-15
When I put a cd or DVD in my DVDRW it does not display on the desktop,my cdrw does. I did edit my /etc/fstab file as shown here, what is wrong? Thanks !
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /windows2       ntfs    nls=utf8,umask=0222        0       0
/dev/hda6       /windows3       vfat    iocharset=utf8,umask=000   0       0   $/dev/hda7       /windows4       ntfs    nls=utf8,umask=0222        0       0
:(

---

### Post by orb9220 on 2006-07-15
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0

Do you only have one drive? doesn't matter If I am correct remove hdd line.

Note: When I cut out or delete a line I paste it in at top behind the # comment symbol that way I can copy paste it back in if I need too.

Hope this helps.

mine is:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Drakkor on 2006-07-15
Thanks for the reply, orb9220  but as you can see from the attached screen shot, I have 2 optical drives ! Click on screenshot to magnify :(
Huh don't know why commenting that hdd worked ! but now both drives are recognised !  Thanks :p

---

### Post by orb9220 on 2006-07-15
Yeah I don't why either it just one entry.

When I installed I had two burners but only one fstab entry.

Anybody knows why this is?

---

