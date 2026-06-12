---
title: "Problems running or installing Natty on Macs with 8G RAM"
date: 2011-04-27
forum: Apple Hardware Users
---

### Post by Rayven on 2011-04-27
My Mac: MacBook Pro version MacBookPro1,4 2.4 Ghz Core 2 DUO, 250G Sata, Nvidia GeForce 8600M GT

I started out with 4 Gig of RAM and after running 10.10 for months and loving it. I decided to install from scratch Natty 11.04 Beta. The install was perfect everything was fine until I decide to upgrade to 8 G of RAM.

After doing thorough research on my Mac I found that it would support 8G and after getting the memory in place I booted up in OSX and checked system profile which showed the 8 G working as expected. The system was working great.

However, once I attempted to boot back to Natty things we pair shape in a hurry. The system was slower then an 8086 processor. During the process I realized I wasn't going to be able to troubleshoot the system like this so I tried to boot off a DVD into recovery mode. Incredible I could not even get to the grub boot menu.

Thinking this had to be a mistake I tried to boot off the old 10.10 DVD I had and got the same result. During all of this trouble I kept seeing Core temperature threshold messages for CPU0 and CPU1 to throttle back pop up every now and again even though the fans were running. Doing some investigation I ran into older issues that might explain it like no lm_sensor configured, ACPI or lm_sensor problems and even a older kernel problems. I did try noacpi and acpi=no but these did nothing for me.

It's at this point that I decided to dropped one of the 4G DDRs and put a 2G back in for 6G total. Natty booted up just fine after that and seems to be running very fast and smooth. I'm afraid I'm not quiet sure what is causing the problem but, I'd be glad to gather information to help out the needed?

Hopefully this exercise will be helpful to someone. I really would like to have the extra 2 Gig back though....

---

### Post by Perfect Storm on 2011-04-27
Moved to Apple Users forum.

---

### Post by clar2391 on 2011-04-28
I'm having a similar problem on my Mac Mini 4,1.  When I try to install Ubuntu 10.10 (32 or 64 bit) or 11.04 (32 or 64 bit) from the live or alternate CD, I get a blinking cursor, no further.  OSX runs fine, but I can't get any version of Ubuntu to install.

I have 8 GB RAm, but I also tried removing one to the RAM sticks and the same thing happens with 4 GB.

---

### Post by joost1123 on 2011-04-28
I might have a similar issue on Macbook Pro 8,1 (2011, 13 inch) with 8 GB of memory

cannot boot from Natty live cd, I get the ubuntu logo and the dots and after a while the screen goes blank

on the other hand, I can boot Fedora 15 just fine..

---

### Post by chad.davis on 2011-04-28
Natty on 8,1 may have other issues, however. At least one person found that booting was only possible when both an install CD and an install USB stick (both with the same installation image) where present at boot. This was based on:
[http://ubuntuforums.org/showthread.php?t=1458341](http://ubuntuforums.org/showthread.php?t=1458341)
I don't know if that was related to memory limits.

---

