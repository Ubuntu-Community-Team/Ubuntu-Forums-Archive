---
title: "CD-RW will read but not write"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Daz1969 on 2008-02-06
Hi,

I had a problem recently (after plugging in a new MP3 player) where no external drives could be mounted & CD-RW & DVD_ROM weren't recognised.
 
I re-wrote my fstab file:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       		<dump>  <pass>
proc            /proc           proc    defaults        		0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 	0       1
/dev/hda5       none            swap    sw              		0       0

#Original CD ROM line...
#
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     		0       0
#
# New Lines to try and get CD working 05/02/2008 ...
#
/dev/hdc		/media/dvd	auto	noauto,user,exec,ro	0	0
/dev/hdd		/media/cdrw	auto	noauto,user,exec,rw	0	0
#
# New lines DW 07/01/2008 (to get USB working.....)
#
/dev/sda1       /media/usb0     auto	noauto,user,exec,rw,sync	0	0
/dev/sdb1       /media/usb1     auto	noauto,user,exec,rw,sync	0	0



This solved most of my problems.
I can now access all USB devices and have read access on CD & DVD.  I just can't write to CD-RW.

Any ideas?

Thanks
Daz

---

### Post by pmshirey on 2008-02-06
There are a few things to do. I need your specs. Also, make sure you have basic writing drivers installed. What software did you try to write with? Last but not least, try lowering the burn speed.

When you have replied:

Send me a private message with the title, "I replied", and with the message being the link to the thread(so i can get back to you.)

---

### Post by Daz1969 on 2008-02-07
Thanks for the reply.
Not sure exactly which specs you're after, but here goes:

I'm running Dapper on a low end PC (Celeron D 331 2.66GHz).
The CD-RW is an old Freecom internal drive.
Software was the basic Nautilus CD/DVD Creator.

All of this worked and wrote to the CD-RW previously.
Oh and I tried lowering the burn speed to x1 .....

The software seems to create the image file OK, but then falls over just as it starts trying to write to the blank disc.

---

### Post by skymera on 2008-02-07
Try K3B

sudo apt-get install k3b

---

### Post by Daz1969 on 2008-02-07
> **skymera said:**
> Try K3B

sudo apt-get install k3b

Does that need KDE?

---

### Post by Tatty on 2008-02-07
> **Daz1969 said:**
> Does that need KDE?


No.

It does need to install some KDE packages to get it working under gnome, but the package manager should take care of that for you when you install KDE.

---

### Post by pmshirey on 2008-02-07
All of your configurations seems to be correct, there is something here I just can't figure out!

---

### Post by forrestcupp on 2008-02-07
I know it sounds like a stupid question, but have you tried more than one blank CD?  It's possible it's a bad CD.  I've had that happen before.

---

### Post by Daz1969 on 2008-02-08
Quick update, I tried K3B.
Initially it couldn't see either of my optical drives and I couldn't add them under settings... some permissions problem was flagged, but didn't mean much to me.

But, if I ran K3B as SU ("gksudo k3b" from the terminal), the drives magically appeared and I can now burn CD's!

So thanks for your help with this guys.

I still don't quite understand what's going on here, but I have a work around.

I'm wondering if my user permissions have got corrupted somehow.....
I had to re-write my fstab file, so it would be no surprise if something else got messed up at the same time.

Thanks again.

Daz

---

