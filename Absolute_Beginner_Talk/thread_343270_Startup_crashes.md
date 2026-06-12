---
title: "Startup crashes"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by SDL on 2007-01-21
Hi,

I'm completely new to linux. I've been trying to install ubuntu on my pc but within 5 seconds of getting to the login screen the computer becomes completely unresponsive. If I'm really quick I can sometimes type the username in that time.

I've tried a number of different versions of ubuntu all of which have the same problem:
- for ubuntu 6.10, I downloaded both the desktop and alternate 64-bit CD's
- for ubuntu 6.06, I downloaded both the PC and 64-bit PC versions of the desktop CD

I'm writing this from the university library as my PC is currently non-functional! Therefore I cannot remember the exact specifications but from memory my setup is:
AMD64 processor
1 Gb RAM
120 Gb Western Digital HDD
Nvidia GeForce FX5700 graphics card.

I managed to get into some sort of text based prompt at one of my more successful attempts after installing the alternate 64-bit version of 6.10, this appeared to work but I can't be sure as I don't know how to use command prompts anyway.

Sorry if my problem has already come up elsewhere. I've tried searching the forum with minimal success.

Thanks very much for any help.

Stephen.

---

### Post by wpshooter on 2007-01-21
Stephen:

My GUESS is that this is a problem relating to your graphics card.

First, are you checking the integrity of your Ubuntu CDs by running the verfication function that is found on the initial Ubuntu boot screen menu ?

Second, have your run the memtest found on that same menu ?

Third, have you tried to boot from the CD using the safe video mode parameter & then doing the installation from there ?

---

### Post by CroEragon on 2007-01-21
I am by no means able to help you, i will just give you few pointers. Have you booted into live cd? Did you check your md5 sum? Did you burn disk too fast (i think 4x should be used when you have problems)? Did you use build in system that checks disk for errors? Did you try using 32bit version? Have you ever used any other Linux distro and did it work?

---

### Post by lamego on 2007-01-21
If you are new to linux you should keep with the 32 bits version.

---

### Post by Malta paul on 2007-01-21
Hi Stephen, Don't give up, Can you boot from the live disk? There are lots of good folk in this community with  knowhow, who will help you, good luck :)

---

### Post by SDL on 2007-01-22
Firstly, thank you all for your responses. Sorry that I haven't been able to reply as quickly as you guys, my internet access is limited to about once a day.

This is the first time I've tried to run any distribution of Linux on my PC. The old HDD failed last week and I had thought it would be good to give Linux a go on the new one.

I've run the CheckCD thingy on all of the disks that I have and they all came back OK.

The live disk had exactly the same results as the OEM version and more than one of the disks I have used have been 32-bits and they've all had the same problem.

I don't believe there is a problem with the installation per se. If I press 'escape' as Ubuntu loads and go into the safe mode I can successfully login using the command prompts but if I let the system boot properly the problem occurs when the desktop appears.

I'd really like to get this working as I think it's a really good concept. Might have to fork out on the £100 for XP though :(. I'm going to persevere but if it's so difficult to get running I can't see that it's going to be practical to use as a sole operating system for me.

So as suggested by *wpshooter* I'm going to look around and see if I can get any information on whether my graphics card is at fault.

Thank you all for your help. I'll let you know how I get on and if anyone has any further ideas I'd really appreciate them.

---

### Post by SDL on 2007-01-22
Well I've tried manually installing the drivers using the commands:

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

A message saying that it was successful appeared. However, it has made no difference in the crash problem.

Can I now assume that the problem lies away from my graphics card? Is my system altogether incompatible with Ubuntu?

Just to clarify as my previous post was unclear, the version of Ubuntu I am know using is the 32-bit 6.10 OEM.

If anybody could suggest anything that I could do to resolve the problem I'd be very greatful.

Thanks,

Stephen.

P.S. I couldn't automatically configure my wireless network either (stupid noob!) so please could any solutions you guys may have avoid the need to use internet.

---

