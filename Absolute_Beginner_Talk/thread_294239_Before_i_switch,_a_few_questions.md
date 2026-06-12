---
title: "Before i switch, a few questions"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by thecynicality on 2006-11-06
Yeah im bored with windows and im trying to get rid of the general dependece on microsoft so i am about to switch to Linux and someone told me ubuntu was a good distrubution to start with.

There are however, a few questions i have before i switch. My first one is installing drivers. None of my drivers are made for Linux and i can't find any that are. How will i install all of those on linux? Also Will i be able to run programs and games that i could on windows? I know i won't be able to run my games (mostly fpss) straight from linux but i hear theres something i can download to run them? And will that work for other programs that i may use that aren't supported by linux?

---

### Post by Bachstelze on 2006-11-06
Hi and welcome to Ubuntu :)

What kind of hardware do you have ? For most of it, you will most likely not have to install anything.

---

### Post by ReaderRat on 2006-11-06
You will find that the "Gaming & Leisure" forum can help you better with gaming questions.

---

### Post by boban on 2006-11-06
> **thecynicality said:**
> Also Will i be able to run programs and games that i could on windows? I know i won't be able to run my games (mostly fpss) straight from linux but i hear theres something i can download to run them? And will that work for other programs that i may use that aren't supported by linux?

Some programs and games can be run in Wine ([http://www.winehq.com/)](http://www.winehq.com/)), there is a list of apps that were tested...

Other programs you can run via virtual machine... But performance isn't best (and direct X is kind of poor, I was only able to run older DX8 games).

But there are some linux games - some of them are listed here: [http://doc.gwos.org/index.php/Native_Games](http://doc.gwos.org/index.php/Native_Games)

As for "other programs" - lot of windows applications has a linux equivalent.

---

### Post by thecynicality on 2006-11-06
Im mostly concerned about my video, audio, and lan drivers, my computer configuration is:

the specifics are:

Intel centrino duo Processor T2500;
2GB (1/1) DDR2 533 SDRAM;
120GB SATA hard drive 5400RPM; 
modular Super-Multi drive (DVD+R, DVD-R, DVD-RAM);
5-in-1 card reader;
ATI® Mobility™ Radeon® X1600 graphics;
802.11a/b/g WLAN;
Acer® OrbiCam camera

---

### Post by Tomosaur on 2006-11-06
Hardware support is generally excellent, but you may notice some weird things going on since the drivers aren't propietary. I haven't had any hiccups with hardware while using Ubuntu.

---

### Post by thecynicality on 2006-11-06
So i just install the normal windows drivers?

---

### Post by bulldog on 2006-11-06
> **thecynicality said:**
> So i just install the normal windows drivers?

That won't go.
You have to install graphics drivers for your hardware,the rest is mostly done by Ubuntu.

If you have a live cd you can check out what works and what not,before you install anything.

---

### Post by boban on 2006-11-06
> **thecynicality said:**
> So i just install the normal windows drivers?

No... Generally you don't install any drivers (maybe only closed source gfx card, but as an option, not necessarily).

Look here: [http://ubuntuforums.org/showthread.php?t=183664](http://ubuntuforums.org/showthread.php?t=183664) for Hardware Compatibiliy List

And here: [http://ubuntuforums.org/showthread.php?t=207916](http://ubuntuforums.org/showthread.php?t=207916) for incompatible hardware...

---

### Post by Tomosaur on 2006-11-06
No, you can't run Windows drivers under Linux. You will most likely not need to install as many drivers as you think you do - the linux Kernel supports much more hardware natively than Windows. You will probably need to install graphics drivers, there are HOWTOs lying around on the forum and in the wiki which will tell you how to do this. A good way to check what hardware is supported is to just try the LiveCD. If any of your hardware refuses to work using that, then chances are you'll need to install drivers or change some configurations to get things going. You should be able to surf the web using the liveCD so you can check if your hardware can be run under Linux/Ubuntu.

---

### Post by lyceum on 2006-11-06
> **thecynicality said:**
> So i just install the normal windows drivers?

I would say use the live CD first, see what hardware it can find. The things that do not work should/may have walk throughs on this site as to "how to make this work". 

Windows drives will not work, as Linux is not Windows. I would start small if I were you. Dual boot your PC. If you have to, pick up a second hard drive for Ubuntu to run on until you get the hang of things. 

The most important rule, keep asking questions! It is worth it. I started using Linux for the same reason, and it is a lot of fun.

---

### Post by Kieranties on 2006-11-06
Best thing you can do to see what hardware ubuntu recognises is to get yourself a Dapper Drake disc.  Download the live cd and burn the iso.  Pop it your drive and boot from it.

This will let you see what ubuntu is like (although will be much slower as running from the disc)  If you don't like it then you can always just switch of the computer and take the disc out.  Your back to windows.

The only device that edgy eft did not recognise in my comp was a wifi card which is non-standard.  The miracle that is ndiswrapper allowed me to use my windows drivers from the disk I got with the device.

The benefit with Dapper Drake is its long term support for stability and hardware.  Give it a go and let us know how you get on :D

---

### Post by devilsadvocate1987 on 2006-11-06
Except the WLAN drivers, which is chipset dependant and we'll have to know more about what kind of hardware you have to confirm if it is supported, everything else should work more or less directly. There are loads of How-Tos for installing ATI drivers and you'll be able to get that going without much trouble. Even if you dont do it, the generic drivers will get you through quite nicely, although eye-candy wont be nearly as responsive.

As for software, most common programs have a linux alternative. If you use something exotic, though, you should make sure that there is, in fact, an open source inux alternative. As for games, assume that none of the good ones will work. Wine can run games built on OpenGL quite nicely but DirectX is windows proprietary code, and, well, if you can get some games running you can take it as a bonus.

VoIP is also a buggy thing so far, but with Tapioca and Psi-Jingle in development that situation should change soon. I have not been able to compile Landell/Tapioca in edgy yet, though.

---

