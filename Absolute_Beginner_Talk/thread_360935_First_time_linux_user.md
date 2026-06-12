---
title: "First time linux user"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by idledanger on 2007-02-13
Okay, so here's the deal.  My system specs are as follows:

AMD Athlon64 3700+
DFI Ultra-D motherboard
OCZ Gold EL PC4000 memory
ATI X1900 XT video card
WD 150 GB Raptor HDD
Creative X-Fi sound card
LG L1970HR connected via DVI-D

Currently I am using the i386 LiveCD to try and install Ubuntu.  Here's the problem.  I can get to the screen where I choose my installation type and specify the other boot options and things.  When I choose the installation, it loads for a while, then I get a flashing cursor up in the top left.  Directly after this, my monitor goes into power save mode.  

Now, after scouring these boards, I have found that I can get into the terminal by hitting CTRL + ALT + F1.  I run the command "sudo dpkg-reconfigure xserver-xorg" to run through automatically detecting the video card, keyboard, monitor and mouse.  This succeeds.  However, being the complete noob that I am, I don't know how to get back out of terminal to get to the live desktop...

I also read that installing the i386 version onto an AMD64 setup has problems.  So, as per another thread, I hit F6 at the installation select and entered in the command "irqpoll pci=noacpi noacpi nolapic acpi=off".  I also tried hitting F4 and selecting a resolution that I know the vid card and the monitor support (1280 x 1024 native, but I used 1024 x 768). 

If I use the "irqpoll pci=noacpi noacpi nolapic acpi=off" command I get random lockups in terminal as well, which requires a reset of the system.

I am currently going to try the alternate AMD64 installation and see if that's better.  But, I would definitely appreciate any help and or suggestions that people are willing to throw out there.

Thanks, 
idle.

---

### Post by tronica on 2007-02-13
> I also read that installing the i386 version onto an AMD64 setup has problems.

thats completely false, you will have zero problem, i've been running a 32-bit OS on a 64-bit chip forever.  As far as booting the live CD, when you get the first menu, select "install in safe graphics mode" thats obviously not the right wording, but you get the drift, try that,

---

### Post by idledanger on 2007-02-13
I have tried in Safe Graphics mode, but this also just shuts the monitor off.  I think I may have a solution for getting out of terminal though.

sudo startx

Does that sound correct?

I will try leaving the extra boot options out, since it seems adding them causes terminal to lock up.  Are there any other suggestions?

---

### Post by tronica on 2007-02-13
thats correct.

---

### Post by Motoxrdude on 2007-02-13
Yes, to start the xserver just run
```
startx
```
Then install and see if it works after you configure your xorg.

---

