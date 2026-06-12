---
title: "Can't read audio CDs"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by fluoblack on 2007-03-20
Hi! 
I installed Ubuntu Dapper and upgraded to Edgy recently but it seems that I can't read any AudioCDs (original or ripped), it seems to look for the wrong path:
Every time I put an audio CD in the drive, the icon appears on the desktop but if I click it, I get the following message:

[B]"couldn't display "cdda:///dev/hda".
There was an error launching application"[/B]

The drive is mounted in /media/cdrom0 but I can't see any files in it with Nautilus
I can read it with VLC even from /dev/hda, and I can read any other type of media (data CD or DVD)
The removable drives and media stuff is correctly configured with VLC as defaut player, all codecs required are installed and working, but it just don't work.
I'm sure I forgot a little thing, but I can't see what it is...
Thanks for helping

Here is my fstab list:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1 -- converted during upgrade to edgy
UUID=3f8a754b-e0ab-4a88-8424-11d98793ccfb / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc2 -- converted during upgrade to edgy
UUID=39163662-ec10-4f75-a607-fc531cdd2180 /home ext3 defaults 0 2
# /dev/hdd1 -- converted during upgrade to edgy
UUID=c8dedbd1-1221-406f-b5b7-932f7b0828a8 /media/hdd1 ext3 defaults 0 2
# /dev/hdc5 -- converted during upgrade to edgy
UUID=17355dbd-4d3d-46d2-9f66-629358795f94 none swap sw 0 0
**/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0**

---

### Post by fluoblack on 2007-03-21
Partially resolved when i upgraded to Feisty, but it doesn't open VLC, just Sound Juicer...
I don't get it, VLC is supposed to be my default player...
:confused: ](*,)

---

