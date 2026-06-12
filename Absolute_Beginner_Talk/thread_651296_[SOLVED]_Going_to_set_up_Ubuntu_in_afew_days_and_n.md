---
title: "[SOLVED] Going to set up Ubuntu in afew days and need some advice"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by travismoore on 2007-12-27
Ok I've decided to switch to Ubuntu for a a few reasons but I still need windows for some apps and an MMO or 2.

I've looked into this a a bit and it seems that my options are Daul-boot or a Vitural Machine.

I would prefer to steer clear of dual-boot as its just pretty time consuming but will do it if I absolutely have to.

So I suppose my main question is about how applicable Virtual Box (or other virtual machine software is for me).

I have an 80GB hard drive at the moment and my 500GB is arriving in a few days. So what I need to know is with virtual box will I be able to run 3D Max (although im willing to try Blender), Photoshop and an MMO (lineage atm). 

Also if what version of Ubuntu to run as 7.10 sounds some what unreliable from what I've read.

Edit: Also with virtual machine is there a need for a partition? And how is linux for game development i.e programming and 3D graphics?


Cheers,
Travis =D

---

### Post by LowSky on 2007-12-27
I dont know where you got your information from but Dual boot is very simple in Ubuntu, and everytime I've done it VM setp is a pain, plus VM has no native USB support.

If windows is already installed then adding ubuntu is as easy as pie with the LiveCD, just choose guided or manual set up  (stay clear of use entire disc).

As for which version its up to you, if you need all the new technology then use 7.10, if you want superb stability use 6.06

---

### Post by jken146 on 2007-12-27
If you're getting a new hard drive, it might be easier to do a dual boot.  Some things don't work in a virtual machine, for example compiz-fusion (not exactly mission-critical lol).

---

### Post by travismoore on 2007-12-27
My main bug bare with dual-boot is speed. I need something nice and quick to switch between both. Also I'm not really going to use compiz fusion as my graphics card is OLLLDDD.

---

### Post by LowSky on 2007-12-27
how is dual booting slow?

it takes me just as long to reboot to another OS than to start up a VMed OS

---

### Post by jken146 on 2007-12-27
> **LowSky said:**
> how is dual booting slow?

it takes me just as long to reboot to another OS than to start up a VMed OS

The problem is rebooting into windows.  That takes forever and a day compared to booting up a linux distro.

---

### Post by travismoore on 2007-12-27
Yea also its nice to have linux open underneath in case I need to do something quickly.

---

### Post by jryprt on 2007-12-27
Take a look a [Wubi](http://wubi-installer.org/)  Its a good way to try ubuntu.

---

### Post by asmiller-ke6seh on 2007-12-27
> **jken146 said:**
> If you're getting a new hard drive, it might be easier to do a dual boot.  Some things don't work in a virtual machine, for example compiz-fusion (not exactly mission-critical lol).

I think he meant virtualizing Windows.

Dual boot has the advantage that you know what worked in Windows will work in Windows under a dual boot situation - the disadvantage is that you have to completely leave Linux/Ubuntu to work with Windows.

Virtualization has the advantage that you don't have to leave Linux to use Windows apps, but until you try it (and maybe work out some bugs or setup) there is no way to know for sure if what worked in Windows will work in the virtualization. Same goes with using WINE/Cedega, etc...

Best thing is to see if what you want to do in Windows can be done in Linux/Ubuntu  - for example, try GIMP instead of Photoshop - Blender is a very mature and very capable application. For either there is a learning curve, but once you master the apps, you won't need to work through a dual boot or virtualization - and the applications will be fully integrated to everything else in your Linux/Ubuntu environment -- and that can be advantageous, too.

I use Gutsy and I find it quite stable. Most of my problems are of my own creation, but as I learn to solve my own problems, I gain in knowledge and independence from Micro$oft.

[COLOR="Blue"]**In a world without Walls and Doors, who needs Windows and Gates?**[/COLOR]

---

### Post by travismoore on 2007-12-27
there still are a few things I want to use (although i will try linux alternatives) but for the moment I will need windows in one form or another.

> **jryprt said:**
> Take a look a [Wubi](http://wubi-installer.org/)  Its a good way to try ubuntu.
I will have a little play around on that in a minute as I do just want to see what its like as well.

---

### Post by p_quarles on 2007-12-27
So, just to clarify, you're talking about running Ubuntu as the host OS, and Windows as the guest . . .  correct?

Photoshop will work, but anything relying on 3D rendering could give you problems. Many graphics heavy games will work better in Wine than in a VM, but there's no guarantee that the one you want will work at all with either. As for 3D Max, I would suggest giving Blender a try before making a decision. It's very powerful, but that doesn't mean that it will suit you. 

Anyway, you didn't mention anything about system memory -- this kind of setup is going to need at least 1 gig. More is better always.

I have a similar setup (Ubuntu 7.10 as the sole host OS, and Win XP running in VirtualBox). It's very nice, and I love the fact that XP takes about 15 seconds to boot up. :)

---

### Post by laidback on 2007-12-27
I use hdd caddys. I can swap out an hdd in seconds and install another which will have a different version of Linux on it, or an earlier version of the same OS, e.g., 7.04 & 7.10. With several hdds I can play to my hearts content without ever worrying about messing up any other OS. For Windoz I do have another PC which shares devices via a KVM switch. My hdds were not expensive, in fact most were free as it appears that a number of people simply throw away old systems in their constant desire to keep up to date. 10-20Gb is fine for my Linux systems. I also have a 250Gb USB hdd which gets called into action should I need large amount of storage, or storage that works with all systems.

---

### Post by travismoore on 2007-12-27
> **p_quarles said:**
> So, just to clarify, you're talking about running Ubuntu as the host OS, and Windows as the guest . . .  correct?

Yep


As for my system:
[LIST]
[*]80GB hd
[*]500GB hd soon
[*]geforce 2 mx/mx400
[*]764MB ram (hopefully 2GB soon)
[*]1.4 AMD Athlon processor
[/LIST]

---

### Post by travismoore on 2007-12-28
Ok looks like I will probably have to go with dual-boot although its not my ideal option. 

Can I partition my 80GB for windows and linux and then use my 500GB for data storage purely?

Oh yea and can you run skype under linux?


> **jryprt said:**
> Take a look a [Wubi](http://wubi-installer.org/)  Its a good way to try ubuntu.
Can't get it to work and I'm not getting much help in the wubi forum.

---

