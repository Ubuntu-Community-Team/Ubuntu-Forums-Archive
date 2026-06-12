---
title: "Cant start ubuntu (Xserver error)"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by wstrinz on 2007-01-03
Ok, let me preface this by saying I have never used Linux before, and although I am pretty knowledgeable about windows, I know nothing about anything Linux. So please, if I don’t make it apparent that I know what an acronym/procedure is, assume I don’t know what it is, and explain it a little more in depth.

Anyway, I've decided to try ubuntu, have downloaded the disc, and when I choose "Start or install Ubuntu" an underscore blinks on the screen a few times, and I eventually am told that Xserver thinks I have no suitable drivers installed. I have an integrated Intel gfx card, which I’m not using, and a pci fx5200. In the detailed output it says it detects both (I think).

I've looked on the forums for solutions to this problem, and most involve going into the recovery console, typing various sudo or dpkg commands, etc. The problem is, when I type anything into the recovery console, it just says, "'whatever I typed' kernel package does not exist".

I'm guessing this is because a.) I'm doing something incredibly stupid/missing something incredibly obvious or b.) my hardware is broken.

Again, I've looked for people with similar problems, and can't find anyone who cant run commands from the recovery console.

---

### Post by jvc26 on 2007-01-03
I take it you're trying to use the live cd - have you md5 checksummed it when you downloaded it (presuming you did) which is to checksum the cd to make sure the data is all present and correct. The second thing is have you checked the cd for errors (there is an option on the live cd if i remember correctly to check the cd) do that and make sure theres no problem.

If there is a problem with the above two you need to redownload or re-burn the live cd as it could be a bad download or a bad burn.

The next question is what is your pc's specs - processor, ram etc. That will tell us whether you have enough RAM for the live cd to work and your gfx card may point us towards a solution with the gfx. Hope that will help, and hope that a bit more info will bring some others to assist on the problem - hang in there theres one heck of a lot of really helpful and knowledgeable folks here.
:)
Il

---

### Post by wstrinz on 2007-01-03
Thanks for the quick reply.

MD5 checksum is OK, and CD is apparently error free.

Here's my computer specs:
Dell dimension 2400
Intell pentium 4 2.53 Ghz processor
638MB RAM
Nvidia Geforce FX 5200 gfx card, 128mb memory, PCI version
GFX driver version 6.14.0010.8425

Again, thanks for the help.

---

### Post by Sunon on 2007-01-03
wstrinz,
Have you tried disabling the on-board video card in the computer's bios.  I think ubuntu is perhaps confused on which graphics adapter to load drivers for.  Nvidia cards work very well with Linux in general, so you shouldn't have many problems with that one...

---

### Post by wstrinz on 2007-01-03
I've actually tried to disable it in the BIOS, but I don't seem to be able to disable it, only to disable the PCI graphics card. I'll go back and mess with it some more, but if anyone else has the same bios as me (Phoenix ROM 1.10 A05).

---

### Post by wallawalla on 2007-01-03
what's your xserver error message?

---

### Post by wstrinz on 2007-01-03
Ok, I've disabled my pci video card, and forced it to use the onboard video card. It worked, so I think xserver is getting confused about which card to use. Does anyone know a way i can disable the onboard video card in my bios or force it to use the pci card?

---

### Post by r4ik on 2007-01-03
Enable the pci card again reboot and see what happens.
If onboard cant be disabled it will choose pci now.
Worth a try happened to me.

---

### Post by wstrinz on 2007-01-05
Ok, I've finally gotten it working. I think all I had to do was change the driver to VESA in xorg, and change the color depth to 16 instead of 24. Thanks to everyone for their help on this.

---

