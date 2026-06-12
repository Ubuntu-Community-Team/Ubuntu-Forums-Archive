---
title: "Special device dev/pktcdvd/0 does not exist"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-11-02
For packet writing I installed 'udftools' on a Edgy system to read/write CD-R/Ws (the way I can do with floppies). 
It works well, except one flaw I didn't have in Dapper. 
I can't mount the selected volume "cdwriter" shown at "Computer Places" permanently. 
The Error message is: > Unable to mount the selected volume.
mount: special device dev/pktcdvd/0 does not existBefore each session I always have to type the mount command ```
sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/cdwriter
```first in the terminal.
[COLOR="Blue"]Who knows what the problem could be? Where could I get some help?[/COLOR]

PS.:
1) In [COLOR="Magenta"]/etc/fstab[/COLOR] I added line:
[COLOR="Magenta"]dev/pktcdvd/0 /media/cdwriter   udf user,noauto,noatime,utf8  0  0[/COLOR]

2) Content of [COLOR="Magenta"]/media[/COLOR]: 
lrwxrwxrwx 1 root root    6 2006-10-31 00:06 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-10-31 00:06 cdrom0
drwxr-xr-x 2 root root 4096 2006-10-31 00:06 cdrom1
[COLOR="Magenta"]drwxr-xr-x 2 root root 4096 2006-11-01 14:15 cdwriter[/COLOR]
lrwxrwxrwx 1 root root    7 2006-10-31 00:06 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2006-10-31 00:06 floppy0
karibu@BitByter:/media$
 
3) Content of [COLOR="Magenta"]/dev/pkcdvd[/COLOR]:
[COLOR="Magenta"]brw-r----- 1 root root  254,  0 2006-11-02 01:33 0[/COLOR]
brw-r----- 1 root root  254,  1 2006-11-02 01:33 1
crw-r--r-- 1 root root   10, 62 2006-11-02 01:33 control
brw-rw---- 1 root cdrom 254,  0 2006-11-02 01:33 pktcdvd0
brw-rw---- 1 root cdrom 254,  1 2006-11-02 01:33 pktcdvd1
karibu@BitByter:/dev/pktcdvd$

4) Content of [COLOR="Magenta"]/etc/modules[/COLOR]
# /etc/modules: kernel modules to load at boot time.
# This file contains the names of kernel modules that should be loaded
lp
rtc
sbp2
fuse
[COLOR="Magenta"]pktcdvd[/COLOR]

---

### Post by Cariboo1938 on 2007-03-10
See my comments [HERE!]("http://http://www.ubuntuforums.org/showthread.php?t=293255"):confused:

---

