---
title: "Fresh install problem from boot"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by zorr0 on 2007-10-24
Hi, downloaded i386 and amd64 versions of 7.10 and with both on both of my computers the same problem happens:

I load it from the cd, and click on install or install in text mode and it loads the kernel and says:


kernel alive
kernel direct mapping tables up to 10000000 @ 8000 - d000




and stays there.

please help.

---

### Post by Pumalite on 2007-10-24
Some info would help. Your specs to start.

---

### Post by shad0w_walker on 2007-10-24
Try booting with these options

```
noapic
noapci

```

I had that issue with a system, turned out the BIOS had a bug, might want to update it to the latest available one.

---

### Post by zorr0 on 2007-10-24
My Rig:

AMD Athlon 64 X2 4200+
8800GTS 640mb
Gigabyte nForce 590 SLI 
2GB Kingston DDR2 800
500GB@7200RPM + 74GB Raptor @15,000RPM

---

### Post by Pumalite on 2007-10-24
Use the Alternate CD to install. You'll end up with a blank screen. Come back and I'll help you configure your xserver.

---

### Post by zorr0 on 2007-10-24
I did use the alternate CD. I am going to try again right now though. Usually same thing as I described happens. kernel alive etc...

brb.

---

### Post by zorr0 on 2007-10-24
yep, back to the same problem.

---

### Post by Pumalite on 2007-10-24
Better download a new iso. Do md5sum on iso, burn at 4x. Torrents better than HTTP or FTP.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by zorr0 on 2007-10-24
okay downloaded a few new iso's. I am burning at 4x now, and I will tell you how it turns out in about 4 minutes but what I don't understand is the fact that I burn cd's and dvd's all the time. Usually at max speed or close to it with no problems. 

Wish me luck :)

---

### Post by Pumalite on 2007-10-24
Don't forget to burn it as 'Image' and not 'data'.

---

### Post by zorr0 on 2007-10-24
Got it, done.

Still doesn't work on my pc for some reason, I just loaded the i386 version on my mom's laptop worked fine (so far that is, which is further then i am) but I am waiting in this black screen where it says that horrid:

kernel allive
kernel blah blah on the bottom of the screen.

thats all i get. :(

---

### Post by zorr0 on 2007-10-24
:( no luck. same stuff is happening.

---

### Post by zorr0 on 2007-10-24
[fixed for the most part]

I ran the text install with the extra option:  acpi=off

loaded up so far. still installing.

---

### Post by zorr0 on 2007-10-25
Im ready to learn how to set up X Server whenever you get a chance. :)

---

