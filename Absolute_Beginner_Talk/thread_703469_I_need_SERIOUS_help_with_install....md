---
title: "I need SERIOUS help with install..."
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Shadonova on 2008-02-21
Ok guys and gals...I hope to hell you can help me out here...first my system

-Amd 64x2 turion
-nvidia 6150 fx card
-2 gig ram
-Hp9000 laptop

Ok Ive been trying to install linux for along the lines of 7 hours now. I started with the 7.10 ubuntu version. Kept freezing at different spots throughout installs...NEVER got passed the boot up. The ONE time it went through boot up and finished with all the oks, my screen went pixelated white, and gradualy got completely white. 

Every time i booted up after that it gave me the option to load Ubuntu up, but the would just go to a command prompt screen that said **INITRAMFS**

>I uninstalled it from my computer afterwards<

Finally i started searching online and people were saying that this laptop has HORRIBLE problems with that version. So I decide to download 7.04 which seems better anyways.

Ok so i Burnt it at 4x btw. When i restart windows, It loads up to the install scrreen right. Well then itll start booting things up...Then when it gets to hardware drivers, it says "**BXM43xx_microcode5fx**" not available or load fail like 4 times. Sometimes it'll freeze there.

If it gets passed that part, it will load the rest of the things. Then itll go to just a black screen.....ANNND thats it. The cd stops spinning. done. 

This is the 3rd time ive downloaded a version and tried to install..WHAT GIVES!?!

PLLLEEEASE help me as Linux looks amazing, and im frankly fed up with vista..

---

### Post by Yuki_Nagato on 2008-02-21
Check what distribution you have downloaded again.  Your problem may lie in the fact that you are using an AMD processor.  I believe certain flavors of Linux hand out separate versions of their distribution for AMD and Intel processors.

---

### Post by Shadonova on 2008-02-21
Yea I know what you are talking about. I have the 64 bit AMD desktop version right now. I had it for the 7.10 release as well.

---

### Post by Shadonova on 2008-02-21
Anyone please?

---

### Post by wolfen69 on 2008-02-21
> **Yuki_Nagato said:**
> Check what distribution you have downloaded again.  Your problem may lie in the fact that you are using an AMD processor.  I believe certain flavors of Linux hand out separate versions of their distribution for AMD and Intel processors.

no they dont. there are seperate 64bit distros, but any 32bit distro will run fine on amd or intel.

you have a *very* linux unfriendly laptop my friend. this thread [http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220) will shed some light on your problems. good luck.

---

### Post by Shadonova on 2008-02-21
yea, and the thing was, I thought any computer was Linux friendly lol...


I just want to start using it. Ill check the thread right now and let you know.

---

### Post by Shadonova on 2008-02-21
HAHAHA wolfen. So I just checked that link...and that was the one I was quoting when I said that ive been reading it was horrible for my laptop.


I really appreciate it though. But the thing is, I gave up on 7.10 and have been trying to install 7.04....



....I really need ideas guys:-/

---

### Post by Shadonova on 2008-02-21
Ok so I went to the tutorial thing the one guy has, so Im now downloading the alternate version. THIS BETTER WORK >.<



But I think I may be out of blank cd.s.....any other way to boot it?

---

### Post by dstew on 2008-02-21
> But I think I may be out of blank cd.s.....any other way to boot it?You can install Ubuntu over the internet using the [ unetbootin utility]("http://lubi.sourceforge.net/unetbootin.html"), which boots off a floppy or USB stick. If you do a network install, it seems to work best if you install a base server with the generic kernel, then boot to a command line and install the ubuntu desktop as you would any application using apt-get.

---

### Post by Shadonova on 2008-02-21
Hey thanks alot. That should really help me out....as long as this darn thing works...

---

### Post by Shadonova on 2008-02-21
OK so im officially pissed. I downloaded that darn non-cd boot thing. Run it, and it tells me at startup when i boot up ubunta....



Windows could not find an operating system. If you have a system disk please insert it now....WHAT THE EFF!!!!


I downloaded the darn non live version and its doing this...


PLease help me...

---

### Post by Sceiron on 2008-02-21
Hi,
have you tried installing in "Safe Grafics Mode" with the Live CD ?

---

### Post by Shadonova on 2008-02-21
Ive tried absolutely EVERYTHING that I know how to do at this point

---

### Post by Doorslammer on 2008-02-21
I also had trouble installing  with live cd 
I then downloaded alt cd & installed fine the first time .
good luck . alt cd is the way to go

---

### Post by Brendan Hart on 2008-02-21
sorry ment new topic

---

### Post by Shadonova on 2008-02-21
I dont have any burnable cd;s to put the alt cd i installed on iit..

---

### Post by dstew on 2008-02-22
After you did the network installation, I assume you re-booted and got the error message> Windows could not find an operating system.Did you get this error after selecting from the grub boot loader menu, or did it just come up? Is that the exact error?
EDIT: If this happened at the very beginning, before you got a chance to install Ubuntu, you need to fix MBR in order to get back to being able to boot Windows. Use the Windows CD recovery console command **fixmbr** to do this. At least that will get your Windows back.
EDIT again: Once you get Windows back, you can try [Wubi]("http://wubi-installer.org/").

---

