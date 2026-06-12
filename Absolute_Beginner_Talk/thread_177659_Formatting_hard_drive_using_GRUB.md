---
title: "Formatting hard drive using GRUB?"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by CanadaGradeEh on 2006-05-16
Ok, so I have Ubuntu installed on my hard drive. Unfortunately, my computer I'm using it on right now is really old, and this particular OS demands a lot of resources. I wanted to install Damn Small Linux on it instead for faster and smoother using, but the DSL CD won't boot in properly. I got into DSL once the LiveCD way, but it won't boot anymore. I think it has something to do with my hard drive being corrupt. Not sure.

Anyway, I want to completely format my hard drive, THEN try an installation of DSL.

Help?

---

### Post by skinnygmg on 2006-05-16
you could try xubuntu to free up some resources...

i think you can d/l a 30 free trial of partition magic from thier website.  it should let you boot from the disk and format your hdd no matter what's on it.

---

### Post by aysiu on 2006-05-16
[QUOTE=skinnygmg]you could try xubuntu to free up some resources...

i think you can d/l a 30 free trial of partition magic from thier website.  it should let you boot from the disk and format your hdd no matter what's on it.[/QUOTE] I don't see anything about a free trial on the Partition Magic website:
[http://www.powerquest.com/home_homeoffice/products/system_performance/pm80/index.html](http://www.powerquest.com/home_homeoffice/products/system_performance/pm80/index.html)

When they did have a free trial, I don't think it allowed you to actually resize partitions or anything--you could futz around but not commit any changes.

Why use Partition Magic when you could use DiskDrake on PCLinuxOS or QTParted on Knoppix?

---

### Post by skinnygmg on 2006-05-16
good call aysiu

---

### Post by catlett on 2006-05-16
You should be able to boot to your cd regardless of your hard drive state. It is a motherboard , bios issue. Your copy of DSL might be corrupted.
The easiest way to format without buying a program is to use a linux distro's live cd. Just about all of them have a version of gparted or qtparted on them. If you can still run your system download a copy of a live cd, the one that always works for me is knoppix [http://www.linuxiso.org/distro.php?distro=44](http://www.linuxiso.org/distro.php?distro=44)  If you can boot to it run qtparted and reformat your entire drive to ext3. Then try and install DSL. 
You might want to re-download DSL as well [http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)

---

### Post by CanadaGradeEh on 2006-05-17
Ok, so I am pretty sure it's a motherboard and/or BIOS/CMOS error, considering my motherboard rarely, if at all, reads my floppy or CD drive. It almost always goes to boot from my hard drive, and I haven't YET been able to boot to my Partition Magic boot floppy. Sometimes it would look for it, but mostly I get an A:\ error at startup, then it'll attempt the CD, then hard drive if that doesn't work. This is all regardless of my boot sequence, and I have everything plugged in correctly. I've been able to get to my Windows 98 disc ONCE and my DSL disc a few times, but I've only ever gotten into the DSL Live GUI once, but it froze up because that was before I had a cooling solution (my heatsink was messed up).

Any ideas on what I might be able to do to attempt to fix or reset my CMOS/BIOS or something? Or just format my hard drive using GRUB command line? I haven't really done any of this before, obviously.

**EDIT**

Little update: I tried formatting using fdisk the one time Windows 98 worked, and it ended up filling the rest of the free hard drive space with a new, blank partition I think. Now I can't load up Ubuntu either. the GDM crashes it says on a funky-lookin' blue and yellow screen with odd ASCII as a border, and prompts me to restart. This is one of the main reasons I want to format now as well.

---

