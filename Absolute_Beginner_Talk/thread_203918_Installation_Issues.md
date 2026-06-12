---
title: "Installation Issues"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by vaibhavkapoor on 2006-06-26
Hi,

I am a newbeee on working with linux systems. I downloaded the Drapper version and tried installing it one of my old systems
(P4, 1.7 GHZ, 128 MB RAM, 60 GD HDD, INTEL-MB, SAMSUNG CD-RW)

I boot from the CD-Rom and go to the Ubuntu Menu, 
I select Install or Start Ubuntu
After that I see a progress bar, the system makes difference checks
After the checks are over the screen turns blank, just the cursor blinks
After say about 25 mins, I get a screen which says Windows Manager and it gets stuck
I have to reboot the system

I read alot of posts about different commands to be given while installing if one had problems with the normal installation, I followed this 

Loaded the Ubuntu Menu
Pressed F6
Typed: debian_installer/framebuffer=false
System starts making checks
and halts giving the error mentioned below

VFS: cannot open root device "NULL" or unknown-block (8,1)
Please append a correct "root=" boot option
Kernel panic - not syncing : VFS : unable to mount root fs on unknown block (8,1)

I really don't know what I am doing wrong here.

The HDD of the machine has been formatted using a Win98 Bootdisk, I also tried using cfdisk and formatted the disk with the formatting option provided in the Slackware v.10 CD which I have. But the problem continues.

I have checked CD for errors, etc everything is fine. The same CD is working perfectly if I try to run the LIVE version of Ubuntu from the CD on my Windows XP PC

I am desperately looking for a solution to this.

Regards,
Vaibhav Kapoor

---

### Post by glotz on 2006-06-26
1. Buy more memory, having 128 megs is madness nowadays. Double that at least or you can forget Gnome.

2. Try using the alternate CD. (you could also try making a server install and adding the desktop later. with that amount of memory, try Xfce or something like that...)

---

### Post by Spleenie on 2006-06-26
Agree with above. The alternate cd install is recommended for systems with less than 192M RAM.

Good luck! Might want to pick up some more old RAM though :)

---

### Post by kons on 2006-08-04
I had exactly the same problem. Had 128M of memory. Doubled it (ironically). Didn't help. Tried to connect two different CD drives. Didn't work. And then. I decided to try the same CD drive as I used to burn Ununtu CD. Solved !!!

---

### Post by renato_rosa on 2006-08-17
I'm trying to install ubuntu for the first time (tho I used to have some linux distributions installed on previous pcs, when i was younger) and I'm getting the same error.

I burned the iso (from the official site) using my apple powerbook's superdrive, cause i don't have a recorder drive in my pc.

What do you suggest me to try? the system is trying to load root in /dev/ram and I have 768mb of RAM.

Any help is welcome.

Tks.

---

### Post by glotz on 2006-08-17
The CD has a self test functionality. Does it produce any errors?

---

### Post by renato_rosa on 2006-08-18
Thanls for the quick answer. Here's my results:

Check CD for defects
"Kernel panic - not syncing: Attempted to kill init!"


memtest
This utility wouldn't run yesterday, but today it ran ok. After some 3h20min, after the 3rd pass, I rebooted, and I didn't notice any errors.

For some wacky reason, after the above test, i tried running the setup again and it started perfectly ok. I did nothing but the test, no utilities no nothing. I guess I just had to not be waiting a solution.

Thanks for all of you, any way.

Renato,
newly come to the ubuntu community.

---

