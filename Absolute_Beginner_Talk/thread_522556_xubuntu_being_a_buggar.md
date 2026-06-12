---
title: "xubuntu being a buggar"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-08-10
i installed Xubuntu with the alternate CD on my spare laptop.
alls went well, but i didt have the partitions how i wasnted them.

so i reinstalled using the SAME disk.
but when i come to boot, it says invalid boot sector?

wtf?

---

### Post by skymera on 2007-08-10
indeed, i can understand if uyou guys are busy..
but please help us out.

---

### Post by overdrank on 2007-08-10
> **skymera said:**
> indeed, i can understand if uyou guys are busy..
but please help us out.

Please stop bumping threads that is very impolite! What are some spec on the the system and did you change anything in the bios?

---

### Post by splintercellguy on 2007-08-10
Perhaps the installer did not properly apply GRUB. How is your dual-boot setup and have you tried Super GRUB CD? [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by skymera on 2007-08-10
no dual boot.

it has 192mb of RAM
1.6Ghz..

it installs fine, but it says invalid boot sector.

and i only bumped to save myself writing out a whooe new one and spamming up the forum with double threads.

---

### Post by overdrank on 2007-08-10
> **skymera said:**
> no dual boot.

it has 192mb of RAM
1.6Ghz..

it installs fine, but it says invalid boot sector.

and i only bumped to save myself writing out a whooe new one and spamming up the forum with double threads.

Ok you have it installed and now the system will not boot. You want to reinstall because you don't like the partitions you set up and it will not boot to the alternate cd.
I understand you not wanting to start another thread but you can wait longer that 30 mins before bumping!

---

### Post by skymera on 2007-08-10
im an impatient person.
it will boot alternate CD...installs
but dosent boot.

due to invalid boot sectore....or summin

---

### Post by TeaSwigger on 2007-08-10
Let's see your partition setup. Specifics please :)

What filesystem was the boot sector formatted with, etc.

---

### Post by lyceum on 2007-08-10
To answer the question, I need to know, are you installing more than 1 OS? Either way when you install a hard drive you never really get the ALL of the hard drive. Ex: I got an 80 gig hard drive and gave 50 gigs to one OS and 20 to another and 10 for swap. What I got was 45 for the 50, 19 for the 20 and around 8 for the 10. This is normal. If you are just using 1 OS I would re-load Xubuntu and let the installer do the work.

Let me know if you need more help. If I cannot get back to you fast enough, feel free to *bump*

:popcorn:

---

### Post by skymera on 2007-08-10
this laptop is BLANK
50GB of formatted HD space.

it has been formatted quite a lot of times recently, and other distribuiton installed.
i think the HD is dead.

it was..

49GB Root
1GB swap...

now nothing

---

### Post by lyceum on 2007-08-10
If the hard drive is dead, you are done. Can you get it to start with a live CD and see if you can access the hard drive? (I would use Damn Small Linux). IF you can see the hard drive, you might be fine. Also, 1 gig for partition seems small to me. Like I said, I would let the install set that up and remember that you will not get the full 50 gigs. You are likely to get about 45 gigs or so. If you have the time I would try loading it one more time. If your hard drive is shot try Damn Small Linux or NimbleX and run your OS from the CD drive if you cannot find the funds to replace it. A shot hard drive is a shot hard drive.

Good luck!

---

### Post by skymera on 2007-08-10
i got the xubuntu live CD reunning just now and i could see the hard drive, through gparted.

then it went dead >_<

---

### Post by lyceum on 2007-08-10
:( sorry...

At this point I guess it is just time for a new hard drive. Wish there I could do to help...

---

### Post by TeaSwigger on 2007-08-10
> **skymera said:**
> this laptop is BLANK
50GB of formatted HD space.

it has been formatted quite a lot of times recently, and other distribuiton installed.
i think the HD is dead.

it was..

49GB Root
1GB swap...

now nothing

Where's the partition for GRUB? No bootloader = no boot, y'know. Should be a tiny ~35mb partition.

---

### Post by skymera on 2007-08-10
at the mo its blank.

i going to install again tomoro

100mb /boot
48GB /
1gb swap


anything else?

---

### Post by lyceum on 2007-08-11
The bigger the swap, the faster your machine, to a point. I would go with 2 gigs or so for swap myself. Good luck though.

---

### Post by skymera on 2007-08-11
ok  idownloaded new alternate.
installed perfect!

i left 100mb for /boot.

thanks for hwlp and advise :)

---

### Post by ugm6hr on 2007-08-12
> **TeaSwigger said:**
> Where's the partition for GRUB? No bootloader = no boot, y'know. Should be a tiny ~35mb partition.

A boot partition isn't necessary. 

GRUB goes on the MBR as default, and the setup files are in /boot/grub

> i think the HD is dead.
Why don't you run a diagnostic?  All HD manufacturers will have a CD for download to check this.  Otherwise, this might help: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by TeaSwigger on 2007-08-12
> **ugm6hr said:**
> A boot partition isn't necessary. 

GRUB goes on the MBR as default, and the setup files are in /boot/grub

Was just going on a hunch there that GRUB wasn't installed. Whether it was MBR or boot partition or wherever... thought they'd seem the same to the OP... trying to look at it through their eyes. You're right my post wasn't technically specific enough, to the point of inaccuracy, but hey it worked and now he has his xubuntu up and running :)

---

### Post by skymera on 2007-08-12
dont worry guys.

its all sorted now :)

---

