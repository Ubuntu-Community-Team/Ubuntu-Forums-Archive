---
title: "PC not booting after install"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by RavUn on 2007-08-13
I began installing the server edition and everything was FINALLY going smoothly.  I could not install before because I did not have enough RAM.  I added 64 megs to the 48 I already had and it was going fine.  However, the 64 was PC100 and the 48 was PC66.  I had read that if you combine then it will run as the slowest, so I figured I'd combine the two just to get past installation then leave it with only the 64.

The installation was taking a while so I was flipping back and forth between my two PCs and the last I saw it was almost done setting up the base system.  When I flipped back it was just a blank screen but the PC was still on.  I tried restarting and it would not boot up, but the PC turns on.  I tried with and without the CD... I tried with the 48 MB PC66 and I tried with the 64 MB PC100 and it still does not boot.

Is it possible I screwed up my PC or maybe I only screwed up BOTH of the memory cards?  I just want to get some opinions to see if there's anything I could do to salvage this.  I do not want to buy another memory card only to find out the PC is garbage.

Thanks.

---

### Post by jw5801 on 2007-08-13
What happens when you try to boot? Do you get to the bios? Does it try to load Ubuntu and fail? Or does nothing happen at all?

---

### Post by RavUn on 2007-08-13
It does not do anything at all... usually it goes to the blue HP screen during startup and then it will boot.  Now it turns on and the CD-Rom light blinks some but then the monitor says no input and nothing comes up.  It does it with or without anything in the CD-ROM.  I'm pretty sure it's something with the memory, because when I was changing out the memory I did not have it in all the way the first try and it did something similar.  Now I know they're in all the way but it's doing it.

---

### Post by tgalati4 on 2007-08-13
Did you create a /swap partition?  112 MB is not really enough to run Ubuntu.  128 MB is really the minimum and you can run it with 64 MB with a decent swap file, but it will be slow.

Those older PC100 sticks seem to work better when they are matched, but it depends on the motherboard.  Only testing will tell what works.  It's hard to imagine any damage, except static electricity to the RAM sticks.  Hold some metal when installing RAM sticks.

---

### Post by RavUn on 2007-08-14
would anyone know how to diagnose the problem?  It still does not boot at all.

I put in a 128 MB stick and it still does not boot, and this is memory from my other PC that I know works fine.  It's the server edition so it should run on 64 MB and should be perfect on 128 I'd imagine.

It did not happen until installing the base system.  Now, I turn on the PC and it powers up and checks the CD-ROM and floppy but then just sits there and does not boot up anything.  I cannot even get it to boot from the installation CD either.

If anyone knows of things to check please let me know.  I don't want this PC to be trashed now.

Thanks.

---

### Post by RavUn on 2007-08-15
Is there a way to test if the motherboard and/or video card are dead without booting or getting to bios?

Also, is there a way to manually reset the BIOS settings?  I heard someone mention this in a chat but when searching google I only found a couple search results and they said to do a manual reset of BIOS but did not say how to.  It involved the jumper somehow.

---

### Post by Hobo Joe on 2007-08-15
I'd recommend trying Xubuntu, it's tailored for running on older machines, especially ones that have a low supply of RAM.

In answer to your problem, I'd say it was the RAM or your video card. I'd install Xubuntu, and then run Envy to deal with your graphics drivers. It's a simple but highly effective program that installs your drivers and configs your xserver. See my sig for a link.

---

