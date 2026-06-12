---
title: "Noob trying to get ati graphics installed"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by fisting_mayfield on 2006-11-05
Hi,
I realise that there must be thousands of posts on how to get ati graphics installed on ubuntu, but i have gone through alot of those posts to no avail.

I'm running dual monitor, 2Gig Athlon X2 64Bit system with Radeon X1600pro PCIE graphics, and i'm having a hell of a time getting the graphics to install ](*,)  

Now from what i have read, there is some issues with running X1600 cards and higher, but i'm sure that there is someone out there who has got one to work and is willing to help someone trying to migrate from windows out!!!

Any help would be appreciated!!!!


-Laurence

---

### Post by ReaderRat on 2006-11-05
I found a little info @  **[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#ATI_Cards](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#ATI_Cards)**
It said this:
>     *  Radeon X1600 PCIe 256M
          o Chipset: MOBILITY RADEON X1600 (M56 71C5)
          o Driver: ati-drivers-8.24.8
          o Notes: tested on Asus A6ja-q039h, gentoo 2006.0 with unstable ati-drivers ebuild. 

Hope this helps...

---

### Post by fisting_mayfield on 2006-11-06
Hi,

I have had a look at the link that you provided, but apart from the driver number (ati-drivers-8.24.8) which i do not know how to install, and the following quote: "unstable ati-drivers ebuild" which puts me in doubt whether i am able to setup my x1600 pcie vga card.

I would like to note that i am a total noob with ubuntu. I have dabbled with linux over the past 5 years, and have not attempted to do any command line programming in at least a year, however, i would desperately like to migrate from winBLOWS to a user friendly distro such as ubuntu

HELP ME PLEASE!!!!!

---

### Post by caravel on 2006-11-06
This is the best guide I've come across.  You'll need to read it properly.  Simply skimming through it won't help you at all.

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by Knowles on 2006-11-06
> **caravel said:**
> This is the best guide I've come across.  You'll need to read it properly.  Simply skimming through it won't help you at all.

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

aye, that is the BEST guide.

IT worth all newbies looking at 

[http://ubuntuguide.org/](http://ubuntuguide.org/)

its the official wiki of pure sex.

its ace.

---

### Post by fisting_mayfield on 2006-11-06
Cheers, will look at it later today when I get a chance!

-Laurence:-D

---

### Post by jsandys on 2006-11-06
If you are trying to use a TV as one of the two monitors, forget about it.  If both screens are regular monitors read on.

First get easyubuntu and use it to install the ATI drivers.  This doesn't use the very latest proprietary drivers but they are very good, compatible and easy to use.

Next run aticonfig --initial (or is it still fglrxconfig --initial).  This will create the initial xorg.conf file.  Run aticonfig --help and print out the listing.  This will give you some clues of the options to use to get the two monitors working.

If this doesn't get both monitors running ask for help again, or try converting your computer back to windows or get an nvidia card <wink>.  I gave up trying to configure my ATI card with a monitor and TV.

If you can get both monitors working, you can then make a backup of your xorg.conf and try tweaking it to get the exact results you desire.  Search about the forum for ATI, fglrx, and MergedFB, starting with the stickys in the Multimedia & Video forum.

---

### Post by fisting_mayfield on 2007-09-17
got it working!!

its a little late, but its a reply none the less

one word

ENVY!!!

---

