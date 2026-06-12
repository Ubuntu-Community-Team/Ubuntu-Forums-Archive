---
title: "fstab mounting"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by ben.christey on 2007-04-26
Ok i've added samba mount data into my fstab for my mount. When i type "sudo mount -a" it mounts fine. How do i make this happen automatically when i boot up?

---

### Post by Cypher on 2007-04-26
If the "mount -a" is mounting it properly, then it should do that on each boot without any extra work..

---

### Post by ben.christey on 2007-04-26
i just tried rebooting. I type:

"ls mountdrive"

and it shows no files. I then type

"sudo mount -a"
"ls mountdrive"

and it shows all the files.

---

### Post by kelbizzle on 2007-04-26
Heres my fstab with a samba mount. I use samba fs so I'm still able to play music and movies across the network, without copying them first.


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=98d78a79-57d4-4ff4-8e0f-9e2df09d2d0e /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda5
UUID=5a4abecd-7019-4075-80ff-dab95f67b154 none            swap    sw            
  0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
//skooters-room/c /media/skooter smbfs username=guest,password=,uid=1000,isocharset=utf8,codepage=unicode  0  0
(END) 

```

what does yours look like. It should mount automatically after rebooting.

---

### Post by ben.christey on 2007-04-26
Mine looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e105870d-c0e5-43e4-8657-f972d86d26ef /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=40ab8319-a131-42f2-98f4-97f7e3782af1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
//ben_desktop/bigshare /home/ben/bigshare smbfs defaults 0 0


i will try adding all the extra bits like yours

---

### Post by ben.christey on 2007-04-26
EXCELLENT that worked thanks!

---

### Post by kelbizzle on 2007-04-26
your welcome. `

---

