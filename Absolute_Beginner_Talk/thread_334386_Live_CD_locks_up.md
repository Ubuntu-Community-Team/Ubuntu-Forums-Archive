---
title: "Live CD locks up"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Borzen on 2007-01-08
Hay I need help
My computer will lockup during the Ubuntu loading screen during the live CD. How can i fix this. 

My specks are
AMD 64 X2
Nvidia 7600GT, it is manufactured OCed.
1.5 GB of ram, don't ask.

---

### Post by glabouni on 2007-01-08
you'll have to give us more info about your case if you want to get help.

---

### Post by Borzen on 2007-01-09
Ok Lets see the kernel loads fine, except on the 38 ed it mentions an error for something like nopic, and I have tried 6.06 and 6.10. Is that it?

---

### Post by rscheckler on 2007-01-09
Are you using a disc supplied from Ubuntu or did you download the iso image?

---

### Post by viper on 2007-01-09
Possible that its a bad burn, you should burn iso`s at the lowest possible speed.

---

### Post by Modernity on 2007-01-09
> **viper said:**
> Possible that its a bad burn, you should burn iso`s at the lowest possible speed.

16x and 8x should be safe enough. If those don't work, then there is something else that is calling the problem. 

> you'll have to give us more info about your case if you want to get help.

If you can watch the load screen and try to see what runs and what fails, it would help us better find out what is going on.

---

### Post by %hMa@?b&lt;C on 2007-01-09
it may be due to hard disks, try unplugging all of your hard drives, you may have them set up improperly (ie both as master/no master only slave)

---

### Post by marktechey on 2007-01-09
I had the same probably, here are three solutions I found:[LIST=1]
[*]You can try using the alternative install Cd
[*]You can use instlux
[*]What I did, you can install an early version of Ubuntu, then update it
[/LIST]
The alternative CD didn't automatically configure my wireless card, and neither did instlux. So I installed Ubuntu 6.06, (Drapper) then upgraded to Edgy. There are tons of ways to at [the installation guide]("https://help.ubuntu.com/community/Installation")for other ways to install Drapper Drake, which you can easily update to Edgy. I suggest you check it out.
8)

---

### Post by jws957 on 2007-08-29
I just downloaded the iso for ubuntu-7.04-desktop-amd64 and have the same problem.  I have the AMD Athlon 64-bit dual core processor, 2G of RAM, and a Gigabyte GV-NX66256DP2 graphics card.  I did an Md5Sum on the iso and it checked ok and the CD verified after burning.  I get the initial boot options screen and then no matter what boot option I select, it locks.  For the basic option, I get displays that say, "loading Casper ..."  "Kernel alive" "Kernel direct mapping tables..." then - nothing.  The display goes blank and everything stops.  Tried every option on the boot options and nothing seems to work.  Would like to get this going to see whether I like Ubuntu and not have to install... Help!?

---

### Post by zeehat on 2007-08-29
You downloaded the 64 bit version.  The 32 bit is more stable with less bugs.  When burning, supposedly the lowest speed possible is good. [I burnt mine at 18x].  Also make sure you burn the iso as an image.  Does it freeze when you select the safe graphics mode option?  If so, I think there is a problem with you Live CD.

---

### Post by jws957 on 2007-08-31
The CD was fine, I downloaded the 32-bit version and the computer locked but gave me a message that there was a problem with the IO-APIC.  Booted with noapic nolapic options and SUCCESS!  Will see if this works on the 64-bit version!

---

### Post by FSHero on 2007-10-07
> **jws957 said:**
> I just downloaded the iso for ubuntu-7.04-desktop-amd64 and have the same problem.  I have the AMD Athlon 64-bit dual core processor, 2G of RAM, and a Gigabyte GV-NX66256DP2 graphics card.  I did an Md5Sum on the iso and it checked ok and the CD verified after burning.  I get the initial boot options screen and then no matter what boot option I select, it locks.  For the basic option, I get displays that say, "loading Casper ..."  "Kernel alive" "Kernel direct mapping tables..." then - nothing.  The display goes blank and everything stops.  Tried every option on the boot options and nothing seems to work.  Would like to get this going to see whether I like Ubuntu and not have to install... Help!?

I am having the exact same problem on my new computer. I burned a Kubuntu 7.04 AMD64 iso image and ran it on my new computer. After I see "Kernel alive", I see a blank screen, and the monitor's OSD says "no signal". If I leave my comp for a couple of minutes, the cd-rom drive starts accessing the CD again. Also, my speakers "pop", as if the driver for the soundcard were just loaded. But of course, I cannot see anything.

The computer's specs are:
Processor: Core 2 Quad Q6600
Graphics card: NVIDIA GeForce 8600 GT
RAM: 4GB
Motherboard: ASUS P5N32-E SLI nForce 680i

I also tried safe graphics mode, but that doesn't work either.

Instead, I tried using the 32-bit version of Kubuntu. That works perfectly. However, I would eventually like to use 64-bit Kubuntu.

Any help is greatly appreciated!

EDIT: I cannot remember the cd writing speed, but before I burned both CDs, I performed a MD5 checksum, which was correct. Both were burned from the same computer, in the same drive.

---

### Post by overdrank on 2007-10-07
> **FSHero said:**
> I am having the exact same problem on my new computer. I burned a Kubuntu 7.04 AMD64 iso image and ran it on my new computer. After I see "Kernel alive", I see a blank screen, and the monitor's OSD says "no signal". If I leave my comp for a couple of minutes, the cd-rom drive starts accessing the CD again. Also, my speakers "pop", as if the driver for the soundcard were just loaded. But of course, I cannot see anything.

The computer's specs are:
Processor: Core 2 Quad Q6600
Graphics card: NVIDIA GeForce 8600 GT
RAM: 4GB
Motherboard: ASUS P5N32-E SLI nForce 680i

I also tried safe graphics mode, but that doesn't work either.

Instead, I tried using the 32-bit version of Kubuntu. That works perfectly. However, I would eventually like to use 64-bit Kubuntu.

Any help is greatly appreciated!

EDIT: I cannot remember the cd writing speed, but before I burned both CDs, I performed a MD5 checksum, which was correct. Both were burned from the same computer, in the same drive.

HI and this thread maybe of some help. 
[http://ubuntuforums.org/showthread.php?t=559891&page=4](http://ubuntuforums.org/showthread.php?t=559891&page=4)
Good luck!

---

