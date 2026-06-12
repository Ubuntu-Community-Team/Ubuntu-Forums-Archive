---
title: "Planning for a new hard drive: Reinstalling Ubuntu"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by arphaus on 2007-04-29
I've had Ubuntu installed for about 1 week and I really enjoy the experience.  Some things are a bit beyond me, but there's enough help here (big thanks! :) )and via the interwebs to allow me to learn and be productive.  I was able to successfully install vmware server (tho I'm not sure if I need workstation instead) as Wine + Photoshop CS 2 = no go.  If Photoshop runs well enough in XP via vmware to be usable, I can look ahead to the day when I get a new hard drive, a new computer or both and make some choices as to what I'll be doing moving forward.

My specific question is this: is it possible to 'export' a complete Ubuntu install to avoid having to reconfigure & reinstall everything when installing to a new hard drive?  It sounds too good to be true, but I figure it's worth asking.

---

### Post by Jeff24K on 2007-04-29
Not sure if this is what you meant, but there's tons of 'howto's' out there on cloning drives. The most common tool to use would be 'dd'... 

[http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html](http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html)

---

### Post by arphaus on 2007-04-29
Thanks - that's one solution that would work if I got a new hard drive for my current pc.  However, my intention is to reorganize my hard drive (ie have a fresh install of XP for just-in-case purposes, devote more space to Ubuntu, etc.) and I'm curious if it would be possible to clone just Ubuntu.

---

### Post by annda on 2007-04-29
it gets problematic when your hardware changes. kernel modules and configuration files created on installation are cut out for your hardware. cloning the entire system may or may not be successful.

unless you are prepared to hunt for errors and inconsistencies, i would suggest doing a fresh install.

however, if you plan on changing only the HDD, cloning may be a good idea. you will only have to check/modify fstab to make sure the partitions are correctly mounted.

---

### Post by arphaus on 2007-04-29
Good point - I hadn't thought about the changes in hardware.  I think rather than get a new hard drive I'd rather wait and get a new pc so as not to do it all twice.  Thanks!

---

### Post by Billy McCann on 2007-04-29
Backup your /home directory to external media (DVD).  That'll keep alot of your settings and email and such.

---

### Post by arphaus on 2007-04-29
Excellent - that will make things much smoother.  Thanks!

---

### Post by ramjet_1953 on 2007-04-30
Another way would be to download Ghost for Linux (G4L). 

Install your new drive into your system, if you have a desktop, or if you have a laptop, put it into one of those USB HDD boxes and plug it into a USB port. 

Run Ghost for Linux from the CD that you burnt from the downloaded iso file and make a clone of your current installation onto the new HDD.

Regards,
Roger :cool:

---

### Post by arphaus on 2007-04-30
I love having all these options!  Not that I don't have them for Windows, but it's a little cooler when it's open-source.

---

