---
title: "Video Resolution"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by simple1 on 2005-10-09
Went to the Wiki at "https://wiki.ubuntu.com/FixVideoResolutionHowto" and followed the first work around "Run the Autodetect Script Again".  Told me /var/lib/xfree86... was a file and worked fine.  I was able to set the correct resolution etc... Restarted X and blank screen with blinking curse...r.  sudo shutdown now and it restarted with

pci dev 0000:00:0a.0 (id 10ec:8139 rev 10) is not a 8139C+ compatible chip
Try the "8139too" driver instead

That part is normal

Then 8 insmod errors inserting '/lib/modules/2.6.12-8-386/kernel/drivers/video/...

That part isn't

And at the bottem is the logon and curser - But not responding.

During shutdown I am warned that the cpu (AMD K6 475) is known not to support apm?

New install yesterday.

Can't turn it off and can't turn it on.

HELP

---

### Post by simple1 on 2005-10-09
Well since no one else is responding; I figure this is as good a place as any to talk to yourself.  After running "sudo dpkg-reconfigure -plow xserver-xorg" five er ten times, I found that my monitor (philips 107s H-30-66Khz, V50-130Hz; up to 1280x1024, 60 hz) runs at 1280x1024 only when I reduce the colors to 16 bit.  And then The last 2 er so inches of my screen is black with occasional minor fireworks.
maybe I'm not alone here

---

### Post by Kyral on 2005-10-09
Well a desktop CPU not supporting Advanced Power Management (APM) is nothing new (My Athlon XP 2700+ doesn't either)

Also the Insmod errors aren't either (my complains about it already being there, go figure)

But I have no clue why your screen isn't going full power

---

