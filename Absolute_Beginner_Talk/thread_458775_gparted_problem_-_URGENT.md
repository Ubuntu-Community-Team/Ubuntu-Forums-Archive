---
title: "gparted problem - URGENT"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by jackmc on 2007-05-30
Hey everyone,

I am trying to make my windows partition smaller, and the progress bar in gparted (livecd version) has stoped moving, and something (hardware, CD drive I think) is clicking pretty loud and often. I dont want to cancel due to the warning - severe filesystem damage - what to do!

Help!

---

### Post by sankarv on 2007-05-30
there are still  problems in gparted in resizing partitions. always its better to backup before any resizing of partitions since its not reliable. if u havent saved your settings (Apply)  better restart the system. atleast your data is saved.

---

### Post by rsambuca on 2007-05-30
Problems with gparted are very rare.  How long has it been going?

---

### Post by jackmc on 2007-05-30
I dont think I have much choice. It got a fair way through the process, now it is buggered. I am worried, off to turn it off.

---

### Post by jackmc on 2007-05-30
> **rsambuca said:**
> Problems with gparted are very rare.  How long has it been going?

Its been clicking for about 10 minutes now, the progress bar hasn't moved in that time

---

### Post by rsambuca on 2007-05-30
"Clicking" definitely is a troubling sound.  How big is your drive, and how much free space do you have, and what are you trying to shrink it down to?  Also, did you defragment the drive first?

---

### Post by jackmc on 2007-05-30
Yep, followed all the instructions. I was worried about hardware damage, so I've cancelled it. Pretty sure it is time for a fresh install - i have a "Primary Master Hard Disk Error" at boot.

It is a 40gb laptop drive.

I was resizing XP partition from 15gb to 10, expanding linux to take the rest.

Any chance of recovery?

---

### Post by jackmc on 2007-05-30
The clicking is now present for a few seconds at boot. I am thinking it is the harddrive.

I will wait a while if there is a chance of recovering data (a few things weren't backed up). If I have no hope, I'll start reinstalling...

---

### Post by rsambuca on 2007-05-30
Ouch!  Sorry, but I have no experience with that type of error.

---

### Post by jackmc on 2007-05-30
Reinstall, here I come. At least it gives me a reason to get rid of windows.

I am an angry man :(

---

### Post by sankarv on 2007-05-30
just a risky suggestion that you can reboot **if theres no other option** and check it once. it may be ok. 

it is possible to recover data as well as partitions to a great extent using tool like **testdisk**.


possibly u can run testdisk using a live cd linux and recover data to a new media.


see the  help in testdisk.


i faced a similar situation thrice and i have recovered my partitions twice and data upto 80 % the other time since i installed another os to the formatted partition in the last case. 


dont install anything at this point so that u can do effective recovery.


anyway its ur wish to recover /re install

---

### Post by ugm6hr on 2007-05-30
> **jackmc said:**
> Reinstall, here I come. At least it gives me a reason to get rid of windows.

I am an angry man :(

I had a similar problem with my previous laptop HD.  It was clicking at every boot, and intermittently was throwing up errors, or not being recognised by BIOS.  I ended up reinstalling a couple of times (and it actually led me to try Linux because of the LiveCD options).  Eventually I ran a Hitachi Diagnostic CD which confirmed it was a *fatal HD error*.  Now I'm hooked on linux, with a new HD.

I'd recommend you try your HD manufacturers website, or [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) has various diagnostic tools included.  The LiveCD will still allow you to backup your data before it's too late.

PS: I suspect this has nothing to do with GParted - coincidence.

---

### Post by kvonb on 2007-05-30
Yup, dodgy hard disk!

You might be lucky and get it replaced under warranty.

It has nothing to do with Gparted, it's just bad luck that it happened while you were doing the resize.  It would have happened anyway at some point.

If you have been having intermittent problems under Windows, then that is likely the cause.

---

### Post by jackmc on 2007-05-30
Nothing, including testdisk, is finding my drive. Time to get a newie I reckon. It'll be nice to have more than 40gb I guess..

Great time for it to happen, exams in a few weeks :(

---

### Post by hellmet on 2007-05-30
Sorry for that bombed hdd.. but.. great that you're taking a new one..
While you're at it, why don't you opt for a bigger HD? 60GB is kinda standard now on many laptops. I suggest you take 120GB and have much more fun with your Ubuntu installation !! :D

---

### Post by jackmc on 2007-05-30
> **hellmet said:**
> Sorry for that bombed hdd.. but.. great that you're taking a new one..
While you're at it, why don't you opt for a bigger HD? 60GB is kinda standard now on many laptops. I suggest you take 120GB and have much more fun with your Ubuntu installation !! :D

Yup, I have already bought it, it should be here in a few days :)

120gb will be a nice step up from 40!

Until it arrives, I'm running Ubuntu from LiveCD, saving everything to USB. Hopefully won't need to turn on/off too much!

While I am severely pissed at myself for not backing up better, I'm excited to be rid of XP, and to have a nice new bit for the computer on the way :D

---

### Post by hellmet on 2007-06-01
Thats great :D.. 120GB !!  All the best in gettin rid of XP.

---

