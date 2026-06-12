---
title: "PowerMac G4 Installation Problems with 9.04"
date: 2009-07-22
forum: Apple Hardware Users
---

### Post by CyclopsCaveman on 2009-07-22
So, I've been trying to install 9.04 on my old PowerMac G4, and I've been having problems with it. Whenever i try to install it, it gives me an input/output error when trying to boot the kernel after install. Am I doing something wrong during install? This problem occurs every time I try to install on the machine.

---

### Post by JOHNNYG713 on 2009-07-22
Hi, I to was having trouble with installing 9.04 on my G3 (same machine different processor)  so my work around was to download and burn 8.04, (as it is the only live cd I found that will load and operate properly),install 8.04,and upgrade from there! you already have the 9.04 cd so it should be easy.If you have an ATI rage 128 card you may have only a 800X600 resolution, for that I wrote this work around: 

[http://ubuntuforums.org/showthread.php?t=854648](http://ubuntuforums.org/showthread.php?t=854648)

and all is well and good in ubuntu ppc land !

Shots of my B&W G3 with an ATI 128 rage

---

### Post by CyclopsCaveman on 2009-07-23
> **JOHNNYG713 said:**
> I to was having trouble with installing 9.04 on my G3 so my work around was to download and burn 8.04, install 8.04,and upgrade from there!

This has been working beautifully so far. Installed without a hitch and is updating right now. Thank you so much. :)

---

### Post by JOHNNYG713 on 2009-07-24
Glad to be of service , I know how frustrating it can be trying to find an install that works! makes! you kinda wounder if they test there stuff! and if they do....what planet!:P as I have about 7 different ppc cds, maybe more and some get so far and die,or just plain don't work and I know its not my burner! but good to hear you got her going:D

---

### Post by CyclopsCaveman on 2009-07-24
So, after Hibernating when I finished the upgrade, after it loads the kernel and video, it gives me a quick Loading, Please wait screen and then turns black and does nothing. I heard I need to disable the splash, but how do I do this from yaboot? Or must I reinstall?

---

### Post by JOHNNYG713 on 2009-07-24
So after you re-boot from being totally shut down this happens? Is there a blinking cursor? or just a black screen ?what video card are you running? If It is a ATI rage 128 fire up the live cd and follow the instruction on the link I provided above in my last post ,I didn't have that happen,but if you have to re-install after you get 8.04 running go into power management and disable hibernation set everything to never shut off also deactivate screensaver or maybe try the rescue mode on the live 8.04 cd,in boot options,I will look around and see If I can find an answer for you ,as I'm sure you are already doing that but I will see what I can come up with! :)

---

### Post by DJKnut on 2009-07-24
I have just gotten Ubuntu 9.04 running on my Mac Mini, and love it!!  I downloaded the Power PC iso from...
[http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)  ... burned it to a cd, and away we went!!!  Dave                                [http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)

---

### Post by CyclopsCaveman on 2009-07-25
If it's any help, my graphics card is nVidia GeForce 2 MX/MX 400. I'll be looking for fixes other than installing the legacy drivers.

---

### Post by B_Free on 2009-07-26
> **JOHNNYG713 said:**
> Hi, I to was having trouble with installing 9.04 on my G3 (same machine different processor)  so my work around was to download and burn 8.04, (as it is the only live cd I found that will load and operate properly),install 8.04,and upgrade from there! you already have the 9.04 cd so it should be easy.If you have an ATI rage 128 card you may have only a 800X600 resolution, for that I wrote this work around: 

[http://ubuntuforums.org/showthread.php?t=854648](http://ubuntuforums.org/showthread.php?t=854648)

and all is well and good in ubuntu ppc land !

Shots of my B&W G3 with an ATI 128 rage

I have 4 Macs (iMac 266 256MB, Blue and White 300 512MB, G4 450 512MB, and a G4 1.25 MMD 1.5g). The B&W and the 450 share a Starlogic 19" monitor. The MMD has a Acer 22" flat screen. I have tried Xubuntu 8.10, Ubuntu 8.04, Ubuntu 6.10, Ubuntu 9.04 in all of the computers and there are varying results. The iMac loads the software but the screen is dark. The B&W and 450 have a "invalid signal" which I assume is regarding the monitor. The MMD does not load, it is a "invalid device". All the Ubuntu software had image burnt in Disc Utility.

Since I am a "Newbie" I have no clue how to alter a file as a work around. I've owned Macs since 1989 and I'm only familiar with the installer for Mac software. What file do I double click to install any of the OSs?

---

### Post by &lt;crush&gt; on 2009-07-29
Sorry, I'm rather new to using Ubuntu and I got an old PowerMac G4 and I wanted to make it into a home network server to use to develop websites (trying to learn that too).

I got the Mac from my mother-in-law who'd had it just sitting around doing nothing for a while, and my brother-in-law told me it does work, but I can't get it to boot. I just burned the 9.04 i386 server to a CD, stuck it in, rebooted (during the boot up) and held the C key, but it doesn't boot from the CD. Can someone tell me what I'm doing wrong?

---

### Post by B_Free on 2009-07-29
I do know something about Macs not about Ubuntu. But you need the PPC version of 9.04 not the 386.

---

### Post by JOHNNYG713 on 2009-07-30
> **<crush> said:**
> Sorry, I'm rather new to using Ubuntu and I got an old PowerMac G4 and I wanted to make it into a home network server to use to develop websites (trying to learn that too).

I got the Mac from my mother-in-law who'd had it just sitting around doing nothing for a while, and my brother-in-law told me it does work, but I can't get it to boot. I just burned the 9.04 i386 server to a CD, stuck it in, rebooted (during the boot up) and held the C key, but it doesn't boot from the CD. Can someone tell me what I'm doing wrong?

Hi you have the wrong install i386 is 32bit pc you need to download and burn PPC version, and you will probably have install issues with 9.04 I start at 8.04 and up grade from there!

---

