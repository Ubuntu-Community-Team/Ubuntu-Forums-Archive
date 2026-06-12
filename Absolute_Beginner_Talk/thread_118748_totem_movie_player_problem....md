---
title: "totem movie player problem..."
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-01-17
i cant get my dvd movies to play on the totem movie player. it will play cd's but not the dvd's. when i put in a dvd i get this error message.

Failed to find mountpoint for device /dev/hdc in /etc/fstab

im new to linux does anyone know what this means. thanks to anyone that can help me out.

---

### Post by christhemonkey on 2006-01-17
can you tell us the output of your /etc/fstab file?
cd /etc
sudo vi fstab
Press ZZ to quit.

---

### Post by grim918 on 2006-01-17
here is the output of the fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
~
~
~
~
~
~
~
~
~
~
~
~
~
~
"fstab" 9L, 534C                                              1,1           All

---

### Post by grim918 on 2006-01-19
my totem movie player wont play any movies. it only plays cd's. does anyone know how to fix this problem.

---

### Post by hen3rz on 2006-01-19
I know this sorta doesnt solve your problem but i would recommend using Mplayer to play dvds as its alot more user friendly and have found it easy to find support for it.

There main page can be found here:
[http://www.mplayerhq.hu/homepage/]("http://www.mplayerhq.hu/homepage/")

And you can install it via the Synaptic Package Manager:
**System > Administration > Synaptic Package Manager > Search **

Then type **Mplayer** in the search field.

---

### Post by christhemonkey on 2006-01-20
[QUOTE=grim918]
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/QUOTE]
Looks like its setup correctly?   You have two cd/dvd drives?

---

### Post by grim918 on 2006-01-21
no i only have one cd drive and the other is a dvd drive. and my movies will also not play with mplayer.

---

