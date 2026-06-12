---
title: "Should I install on a partition or use virtual pc?"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by fghouse on 2005-09-20
Hello,

I am planning on purchasing a new laptop to take with me to graduate school.
I would very much like to install Ubuntu on this machine. My issue is I would also like to keep windows up and running so that I can live peacefully with the rest of the world. I have little or no experience with Linux and just like many others, I use widows for all my work. Linux and its capabilities might be more useful for the program I going to school for.

Would you suggest I invest in Microsoft's virtual PC to install Linux (easier to remove) or should I partition the new drive and have Linux exist in a separate partition.

What I like about the virtual pc install is I will have the ability to switch to windows at anytime without having to reboot. Despite critisisms, this does have some value to me. 

TIA

Feroz

---

### Post by joshmachine on 2005-09-20
Not sure about your budget, but I would go the other route.  
Install Ubuntu as your primary operating system and install Windows on VMWare Workstation
[http://www.vmware.com]("http://www.vmware.com") 
if you need full windows functionality, or codeweavers Crossover Office
[http://www.codeweavers.com]("http://www.codeweavers.com")
if you just need some office apps and the like for compatibility.  

As someone new to linux, this may be to big a step, but what the hell, stick it to the man! 

Cheers

---

### Post by KingBahamut on 2005-09-20
Partition the drive. 

Ive not run successfully anything In Virtual PC , and VMware can get a little touchy. 

Dual Booting is easier in my opinion, and creates a situation making you learn the OS a little more.

---

### Post by az on 2005-09-20
[QUOTE=fghouse]Hello,

I am planning on purchasing a new laptop to take with me to graduate school.
I would very much like to install Ubuntu on this machine. My issue is I would also like to keep windows up and running so that I can live peacefully with the rest of the world. [/QUOTE]


Unless you are doing something super-specialized that requires proprietary software (actually, the further "out-there" you go in the sciences, the more prevalent open-source software becomes...) Ubuntu should be able to keep you properly in touch with the rest of the world.

---

### Post by mlomker on 2005-09-20
[QUOTE=joshmachine]Not sure about your budget, but I would go the other route.  
Install Ubuntu as your primary operating system and install Windows on VMWare Workstation
[/QUOTE]

I agree with this.  If your new laptop has 1 Gig of RAM then Windows XP will run great in a window on Ubuntu.

Here's the consideration:  video is slower inside VMWare, sound usually works but can be a little choppy, some unusual devices (USB, etc) may not work from with the VM session.

Which one you pick as your primary operating system will depend upon those factors.

I actually run 32-bit Ubuntu in a window on my amd64 Ubuntu...allows me to troubleshoot things for people from time to time.  VMWare is awesome because you can install a beta operating system in a window to try it out without installing it.  It also has 'snapshot' features that allow you roll back your changes to the last snapshot if something blows up...and that feature works for *any* operating system installed within a VM.  It rocks, really.

---

