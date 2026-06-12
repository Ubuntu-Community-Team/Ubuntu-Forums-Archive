---
title: "I get blank screen when I start Ubuntu 7.04"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by wasim2050 on 2007-07-16
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=304018](http://ubuntuforums.org/showthread.php?t=304018) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I find some similar threads related to my problem but I find nothing in them that can help me.

Its been 4 days since I have installed first ever linux system on my PC and it is Ubuntu 7.04 Fiesty Fawn. And it was working fine after installing all the codecs and updates and necessary softwares but since yesterday whenever I try to start the system I get a blank screen and I cannot login to my system as I cannot see the login screen nor do I hear any sound. I try pressing Ctrl-Alt-F1 and Ctrl-Alt-Backspace but nothing happens so I have to do the hard reset and after reseting I can see my login screen and everything works fine. And this happens everytime I try to start my system after shuting it down.:(

So does anybody knows whats wrong.

What I am doing currently is I am booting from recovery mode as this seems to solve my problem but I would like to boot from the first option.

---

### Post by scrooge_74 on 2007-07-16
Does your system has any ATI or Nvidia card?

from recovery mode at least try sudo dpkg-reconfigure xserver-xorg, when asked for video driver go with either VESA driver (for the time been) or if you have an Nvidia card use "nv", if you have an ATI use "ati"

If the problem is your video drivers that should get you back to your desktop for the time beeing

---

### Post by wasim2050 on 2007-07-16
Let me tell u in more detail

On the first day when I installed the system everything was working fine but whenever I try to logout the screen use to go blank so I ask an Internet friend of mine who has been using Ubuntu for few years and he help me to change my display driver from vesa to i810 since I am using Intel display card and the problem was solved for 4 days and now this new problem has arised.

---

### Post by scrooge_74 on 2007-07-16
definetly is a video driver issue 

I just read a thread some [here]("http://www.linuxquestions.org/questions/showthread.php?t=69720")  which says the problem lies with the drivers (is an old thread anyway), but check on your bios how much ram is available for your video card

Also check this [thread]("http://ubuntuforums.org/showthread.php?t=494409&highlight=i810") in the forums, it seems there is a driver in the repositories

---

### Post by wasim2050 on 2007-07-17
Ok I just checked my Asus Motherboard CD and I find out that I have been supplied with the linux driver for my display card.

There are three files in it

20030425-i386.tar.gz
dripkg-1.0-4.i386.rpm
readme.txt

I am also writing the contents of the readme.txt file
======================================================
1. We only provide Graphic driver for Linux in current POR.

We have no plans to offer other drivers like USB, SMBus or AC97.



2. We are use Open Source (not binary code like MS Windows OS driver) to release Linux 845 Graphic driver.

Customer need to get it from XFREE86 website: [http://www.xfree86.org](http://www.xfree86.org)



3. Information link:

[http://www.xfree86.org/cvs/changes.html](http://www.xfree86.org/cvs/changes.html)

129. Add Intel i845G 2D support to the i8x0 driver, DRI is disabled. (#A.1062, Graeme Fisher, 2D3D).



4. Download link:

[http://www.xfree86.org/cvs/index.html](http://www.xfree86.org/cvs/index.html)

All instructions (download, build and install) are on the Xfree86 website.



5. Intel will submit new version of Graphic driver for 845G XVIDEO support in the next few weeks.

Schedule: Late September.
======================================================

So what should I do now.

---

### Post by scrooge_74 on 2007-07-17
Read the instructions carefully, check all the websites (there may be more up to date drivers), see if you can find more info on the subject and then take the plunge and install

Also did you check that in synaptics you have the xserver-xorg-video-i810 and the xserver-xorg-video-intel packages?

---

### Post by moire76 on 2007-07-31
I had the same problem yesterday on my inspiron 1100 (with i810 driver).
Don't know the reason, but I found a way it works.
If your video driver/xorg.conf set correctly, (you can check if you boot recovery mode and after the bootup type startx at the console and your x is starting without problems) but you still see the blank screen, you can try my way I describe it here: [http://ubuntuforums.org/showthread.php?t=428200&highlight=i810+blank]("http://ubuntuforums.org/showthread.php?t=428200&highlight=i810+blank")

Cheers,
Moire

---

