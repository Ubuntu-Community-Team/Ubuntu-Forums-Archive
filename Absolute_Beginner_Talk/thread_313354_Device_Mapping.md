---
title: "Device Mapping"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-05
My first CD drive is a CD-RW (hdc) mounted on /media/cdrom0, my second is a DVD-RW (hdd) mounted on /media/dvdrecorder.  In my directory /dev I have four link files named cd-rom, cd-rw, dvd and dvd-rw, all targeted at /dev/hdd.  Of course in that same directory I also have hdc and hdd.  This was all set by the system--I haven't altered any of the names.  My question is, what is the purpose of these link files, (in the same directory as the target) and why are there four pointing to hdd and none to hdc?  Also the mount names (if that is the way to put it) cdrom0 and dvdrecorder don't seem consistent with each other--why is there no 0 for the dvdrecorder as in cdrom0?  One more:  why is the file /etc/hdparm.conf all commented out?  Is this file's purpose only for the user to change something?

Thanks in advance,
Buck

---

