---
title: "CD-ROM won't read install disk?"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by jarviscares on 2006-03-07
So here is my problem: 

I've made 2 separate install disks (one with ISORecorder, one with NERO, just to make sure it wasn't the burning software), and they were made on an XP machine. Neither, however, will even be recognized by an older computer I have that I am trying to install ubuntu onto (full install, wipe drive first). 

Specs of computer in question:
intel celeron 633mhz
112 mb pc133 ram 
6.48 gb Fugitsu HDD
Hitachi CDR-7930 CD-ROM
Windows 98, 2nd edition 

This computer refuses to boot to, or even recognize (trying to open the cd to explore in "my computer" gives me an error message: "D:\ is not accessible. The device is not ready", and an option to retry or cancel), while my xp computer (the one that burned the cd) boots off of it and explores it with no problems. 

Now my CDROM on the win98 computer DOES work fine with other program/music cds. I've tried booting the cd with a win98 startup disk (floppy), but after the driver for my cd rom is installed (Drive E: = Driver MSCD001 unit 0), it gives me the error message "CDR101: Not ready reading drive E... Abort, Retry, Fail?" anytime I try to type something in to the A:\> prompt. (granted, I have no idea what to type in the prompt to run the install cd for linux...) 

Any ideas would be GREATLY appreciated... I've googled everything I can think of for a fix, but so far have come up with nothing... 
Thanks!

---

### Post by Sutekh on 2006-03-07
When you burnt the disc did you burn it as an *image*?  This is very important, burning the iso as a data disc or bootable disc won't work.

In Nero close the wizard at start-up and choose 'Recorder' and then 'Burn Image', then select the ISO you downloaded.

---

### Post by jarviscares on 2006-03-07
Yeah, I did that... And I even tried burning a CD with ISO Recorder (as the wiki suggests) and that didn't work either... Both boot completely fine on my XP computer... it's just my win98 computer isn't recognizing it... 
Thanks for the quick reply!

---

### Post by jarviscares on 2006-03-07
Anyone have any ideas?

If you need more info, let me know and I'll do my best... I really wanna give ubuntu a shot on this computer... it's not used for anything else right now, perfect for playing around and learning on!

Thanks!

---

### Post by racecat on 2006-03-07
Maybe pull the cd burner out of the XP box and put it in the other for the install.

Bill

---

### Post by jarviscares on 2006-03-07
... good plan... I kinda feel dumb for not thinking of that myself :oops:!

I'll do it tomorrow (too late tonite) and let you know how it works out!

thanks for the idea

---

### Post by racecat on 2006-03-07
Your welcome and good luck with it. Keep us posted.

Bill

---

### Post by Scunizi on 2006-03-11
I had close to a similar issue with machines not being able to read the CD after burning.  I had to slow the burn process down to under 10X to make it work.

---

