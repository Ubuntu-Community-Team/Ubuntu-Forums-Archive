---
title: "Mount Options"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by greenwom on 2006-07-09
Well I though I'd be able to find the answer to this on my own but... I need help.

I have a second hard drive mounted but I can't write without running as root(sudo).  How can I mount it and allow myself to read & write without being root?  I use the drives for pictures and music and I have to runn all my editing software as root to be able to save anything.

I tried mounting it inside my home folder but that didn't change anything.
Here's my fstab (I've tried a few varations)

```
mike1@ubuntu27:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[COLOR="Red"]/dev/hdb1       /media/mp3      vfat    rw,user         0       0[/COLOR]

```

Thanks in advance

---

### Post by woedend on 2006-07-09
options
gid=1000,umask=002,noexec,nosuid

should do it(assuming you are the only user. I *think* by default your group id is 1000.

so it would read 
/dev/hdb1       /media/mp3      vfat      gid=1000,umask=002,noexec,nosuid       0       0

---

### Post by greenwom on 2006-07-15
Thanks that worked like a champ

---

