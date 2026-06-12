---
title: "Help with playing DVDs (Solved)"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by Sonic5688 on 2005-12-01
I followed the instructions on getting DVDs to play on this one website which I lost the link to, but now that the DVD plays, it skips and jumps too bad to watch. Can someone help me? Thanks!

---

### Post by aysiu on 2005-12-01
Have you tried this?
[http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom)

---

### Post by Sutekh on 2005-12-01
You should try enabling DMA (if you already haven't).  

[Ubuntu Guide - Speed up CD-ROM/DVD]("http://ubuntuguide.org/#speedupcddvdrom") has steps to enable DMA, which hopefully will stop the skipping and chunking.

Ed: seconds, aysiu, seconds ;)

---

### Post by aysiu on 2005-12-01
[QUOTE=Sutekh]
Ed: seconds, aysiu, seconds ;)[/QUOTE] It happens all the time...

---

### Post by Sonic5688 on 2005-12-01
this is the site that i followed last time. it still skips around though. is there something else that could be wrong? is it totem thats doing it? also, where would my dvd drive be located? im used to windows where its just F: . Thanks!

P.S.
I have 2 media drives. a CD burner in my primary and my DVD burner in my seconday. just thought i should note this.

---

### Post by Sonic5688 on 2005-12-01
I think I've fixed the problem. I don't seem to have any trouble with VLC Media Player. I'll return to this thread if my problems continue. Thanks for your help guys!:D

---

### Post by akiro.yamamoto on 2005-12-01
Question?
Did you use hdparm on the CORRECT Drive....???
If you only copied and pasted the info from the listed site and your drive is not located at /dev/cdrom (which I didn't use) .... ah that ain't gonna work :smile:
Check your fstab.....
Take a look at mine....
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2    /               reiserfs notail          0       1
/dev/hdb5       /home           ext3    defaults        0       2
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hdb1       /media/slack    reiserfs defaults        0       2
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


The important part is 
/dev/hdc     /media/cdrom0

So I used hdparm -d1 /dev/hdc to check for DMA status on my drive.

And also used /dev/hdc in the hdparm.conf file to make the change
permanent. Try that first... post any errors if any.
Also please post the result of the check for DMA on your dvd drive....
Regards....
:smile:

---

### Post by Sonic5688 on 2005-12-01
Thats what I was doing wrong. Thanks! You've saved my tail yet again.

---

