---
title: "I tried just running ubuntu off the CD"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Xplunger on 2008-03-09
But it was really slow, which I attribute to the fact that it was running off the cd, which makes booting up slow, but when it booted up it had to use low graphics because it couldn't register my card, righter now I'm using a Nvidia Geforce 6200, do I have to install Ubuntu and then download some funky drivers or something?

---

### Post by halitech on 2008-03-09
you could try opening a terminal and doing

```
sudo dpkg-reconfigure xserver-xorg
```

but it may not work and even if it does, if you reboot you would have to do it again as the live cd can't save things to the cdrom

---

### Post by criskat777 on 2008-03-09
just install it and once it's all done and u boot in to Ubuntu at the top right of the screen u will see an image that looks like a video card those are the restricted nvidia drivers just activate them and you'll be set.:)  if u have any ? just come bake here and post them

---

### Post by The Titan on 2008-03-09
yes, i have the same card, i also could not run it off of the cd normally but after i installed everything worked fine and worked great after i installed the restricted drivers.

---

### Post by Xplunger on 2008-03-09
Ok, then I'm going to defragment and give it a shot, but first, if I decide to get rid of it, how do I get rid of  grub, last time, since I don't have a windows live CD, when I wanted to get rid of opensuse, when I deleted it... I couldn't get back into windows... due to grub error 22,  how would I get rid of that?

---

### Post by The Titan on 2008-03-09
> **Xplunger said:**
> Ok, then I'm going to defragment and give it a shot, but first, if I decide to get rid of it, how do I get rid of  grub, last time, since I don't have a windows live CD, when I wanted to get rid of opensuse, when I deleted it... I couldn't get back into windows... due to grub error 22,  how would I get rid of that?
is it all on 1 hdd?

---

### Post by halitech on 2008-03-09
before you get rid of the partition, you could always edit grub to make windows the default OS, set the delay to 1 or 0 (but test to make sure it works first in case you need to make changes) and then grub will still load but very quickly put you into windows.

you say you don't have a windows live cd, do you have the install cd?

---

### Post by Xplunger on 2008-03-09
> **halitech said:**
> before you get rid of the partition, you could always edit grub to make windows the default OS, set the delay to 1 or 0 (but test to make sure it works first in case you need to make changes) and then grub will still load but very quickly put you into windows.

you say you don't have a windows live cd, do you have the install cd?

I have the install cd, but I don't have my driver cds, which means I'd have to go to my friends house and download all my drivers and install them... like last time.

> 
is it all on 1 hdd?


Yeah it's all on one hdd.

---

### Post by halitech on 2008-03-09
if you have the install cd, you can boot from it and at one point it will ask if you want to install or rescue (can't remember the exact screens, been awhile since I installed XP). If you go to rescue, it will allow you to drop to a command prompt and run fixmbr to restore the mbr and remove grub. You will not need to reinstall windows at all.

---

### Post by Xplunger on 2008-03-09
K thanks for the help, but could that also be done through regular command prompt. If I just set up grub to use windows as default, after I removed Ubuntu(if I do), would I be able to just load windows and delete from the cmd there?

---

### Post by halitech on 2008-03-09
I would think you should be able to do it that way as well but I can't say for certain. If it works that way, great. If not, at least you have the install cd and we know we can do it that way.

better safe then sorry and with MS, rule 1 is be prepared :D

---

### Post by azimuth on 2008-03-09
> **Xplunger said:**
> I have the install cd, but I don't have my driver cds, which means I'd have to go to my friends house and download all my drivers and install them... like last time.



The obvious solution is download all the drivers you would need now while you have a working system. Burn them to a cd and then you will have them, when and if you need them. I always found with Windows, I eventually needed them.

---

### Post by steveneddy on 2008-03-09
The command to repair Windows is

```
fixmbr
```

do this from the Command Screen in Windows.

After installing Ubuntu, make sure that Windows boots first.

Give Ubuntu @ 20 Gig if possible. More if you have it.

Don't worry. Dual boot for a while. This is how most of us started with Ubuntu.

When we discovered that when we were booting into Windows only to update that it was time to go full time.

---

### Post by Xplunger on 2008-03-09
> **steveneddy said:**
> The command to repair Windows is

```
fixmbr
```

do this from the Command Screen in Windows.

After installing Ubuntu, make sure that Windows boots first.

Give Ubuntu @ 20 Gig if possible. More if you have it.

Don't worry. Dual boot for a while. This is how most of us started with Ubuntu.

When we discovered that when we were booting into Windows only to update that it was time to go full time.

After a while I eventually just got to a black screen with four lines... the last said [ok] and something about running local but script... from there nothing really happened. Right before that I had seen a thing about running in low graphics. From what I read on ubuntu, normally when you do that option, you have a choice to mess around on a live cd and then install, but that doesn't seem to be working, is their an option to just go strait to install?

---

### Post by halitech on 2008-03-09
what are our system specs? You may need the alt install cd instead of running the live cd if you want to install.

---

### Post by Xplunger on 2008-03-09
It's a Dell Dimension e310

  Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_qfe.070227-2300)
           Language: English (Regional Setting: English)
System Manufacturer: Dell Inc.                
       System Model: Dell DV051                   
               BIOS: Phoenix ROM BIOS PLUS Version 1.10 A04
          Processor: Intel(R) Pentium(R) 4 CPU 2.80GHz
             Memory: 1526MB RAM
          Page File: 331MB used, 3090MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.2180 32bit Unicode

---

### Post by halitech on 2008-03-09
should have plenty of power to run the live cd so not sure why it isn't loading other then maybe it doesn't like your video card.

---

### Post by Xplunger on 2008-03-09
That could be why, I get a pop up about low graphics, and I get three options, configur, shutdown or continue.

---

### Post by halitech on 2008-03-09
if you go into configure, does it give you the options on setting up your video card properly?

---

### Post by Xplunger on 2008-03-09
Not sure, I'm going to reboot and fool around with it, I'll post again after.

---

### Post by Xplunger on 2008-03-09
It gave me some options I didn't really understand, but I got the same screen with four lines in the end, which makes me think it loaded in a command line interface, so I'm not really sure what to do from there.

---

### Post by halitech on 2008-03-09
what is the last line saying?

---

### Post by RequinB4 on 2008-03-09
Before you try messing around with the CLI, when you boot and get the low gfx message, go to configure and choose the VESA drivers.  Then you should get a GUI and be able to install restricted drivers for your card.

---

