---
title: "Mplayer can't play DVD's after Feisty upgrade"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-05-14
I was able to play DVD's using Dapper but after I upgraded to Feisty, I can't play DVD's using any of my movie players.  I have been trying to get Mplayer to work with no luck.  I have all of the codecs installed.  When I try to mount the DVD-ROM drive it says "unable to mount" probably no media present.  I can play movies using firefox OK.  Is there some bug with Feisty and DVD playback??

---

### Post by rggavubt on 2007-05-14
After doing a lot of reading I think my problem is in the /etc/fstab file.  I ran the following command in the terminal "cat /etc/fstab" and got the following readout :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=4efc62d4-8b02-424e-8391-37f8685eb5f7 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=b43127b5-d1be-462c-86eb-ec86e24c381a none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

My first drive is a DVD-ROM drive(master) and is called /dev/hdc....
My second drive is a CD-RW drive and is called /dev/hdd.....
I am thinking I should edit the above file and change /dev/cdrom to /dev/hdc and change the second /dev/cdrom to /dev/hdd.  What should I change /media/cdrom0 and /cdrom1 to??
Should I change them to dvd0 and cdrom1?????

ANY HELP WOULD BE APPRECIATED!!!:confused:

---

