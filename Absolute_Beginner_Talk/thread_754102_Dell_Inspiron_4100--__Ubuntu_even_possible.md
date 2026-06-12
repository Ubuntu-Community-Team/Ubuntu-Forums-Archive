---
title: "Dell Inspiron 4100--  Ubuntu even possible?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by adk46er on 2008-04-13
I have a Dell Inspiron 4100 running Win XP and want to switch completely to Ubuntu-- get rid of windows forever. My specs are: Pentium 3, 866 Mhz, 512 MB RAM, 40 GB HD. My video adapter is ATI Mobility Radeon AGP, 128 bit accelerated.  I downloaded and burned the Ubuntu 7.1 live CD (desktop), and want to run the live CD successfully BEFORE i wipe out windows. However, even if i run Ubuntu in safe mode, it hangs at the orange bar and then (if i wait it out) the screen goes black and it freezes.  I downloaded the alternate CD but I don't want to get into partitioning and all that if it won't work in the end. I also tried burning and running OpenSuse 10.3  as a live CD; that went further and I actually thought it would load and then the screen displayed random lines and garbage and the system froze. I would prefer to install Ubuntu, but will use what ever distro I need in my quest to rid myself of windows.  I know from my research that it's the ATI Mobility that is the problem. Any suggestions are greatly appreciated; most info that I can find for my system/specs is either A) too old, or B) they have a different graphics adapter.

---

### Post by j.bunce on 2008-04-13
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)

Might be able to help, looks like you will be supported.

---

### Post by adk46er on 2008-04-13
I've read all those posts, but they are no help to absolute beginners! Bottom line... I can't run the live CD, can I? I have no choice but to go forth with an install from the alternate CD and attempt to tweak things from there???

---

### Post by rdsherwood on 2008-04-13
When the live CD brings up the booth menu, try pressing F6, then in the options line, try adding "acpi=off", "noapic" and or "nolapic", and see if any of those help. (Also delete "quiet", and change "Splash" to "nosplash". That might give you details on where in the proces it is hanging up.) 

You might also try going into the VGA settings with F4, and trying some of the resolution settings (i.e. set it to 640 x 480 16 bit) to see if you can get past the funky screen. Once you come up with a setting or combination that works using the Live CD, then you can feel fairly comfortable that you can get it to work when you install it on the hard drive.

---

### Post by starcannon on 2008-04-13
There is an excellent alternative, try doing a Wubi install, I recommend these anytime someone is not 100% comfortable, it lets you install Ubuntu like a windows application, if you decide your not ready then you can simply uninstall it like any other windows application.

You can get it here [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

Be sure to read the FAQ there is some information in there that can save you a lot of time since you already have the Ubuntu LiveCD.

---

### Post by adk46er on 2008-04-13
> **rdsherwood said:**
> When the live CD brings up the booth menu, try pressing F6, then in the options line, try adding "acpi=off", "noapic" and or "nolapic", and see if any of those help. (Also delete "quiet", and change "Splash" to "nosplash". That might give you details on where in the proces it is hanging up.) 

You might also try going into the VGA settings with F4, and trying some of the resolution settings (i.e. set it to 640 x 480 16 bit) to see if you can get past the funky screen. Once you come up with a setting or combination that works using the Live CD, then you can feel fairly comfortable that you can get it to work when you install it on the hard drive.

so when i hit F6, i get the command line and the last things are "quiet splash--"  i successfully deleted the "quiet" and changed the VGA settings as you suggest, but i am unclear where to add the "acpi=off" and the like.... is it before or after the "splash--" i have tried both. by the way, if i leave the splash but omit the quiet, i can see that it hangs after "running/scripts/casper-premount   ok"

to the responder below, i have the wubi installing on the live disc-- it was included-- is that what you speak of? i tried going that route and it didn't work either

i am almost positive it's the ATI Radeon Mobility that's the issue

---

### Post by adk46er on 2008-04-13
also, if i change to nosplash i get nothing-- just a blank screen and the cd stops

---

### Post by rdsherwood on 2008-04-13
> **adk46er said:**
> so when i hit F6, i get the command line and the last things are "quiet splash--"  i successfully deleted the "quiet" and changed the VGA settings as you suggest, but i am unclear where to add the "acpi=off" and the like.... is it before or after the "splash--" i have tried both. by the way, if i leave the splash but omit the quiet, i can see that it hangs after "running/scripts/casper-premount   ok"


The other commands (acpi=off, noapic, etc.) can be entered on the line anywhere - I don't think the position is important. I entered them after splash but before the -- .

(I'm also a newbie - maybe some of the more experienced users have more valuable input).

---

### Post by adk46er on 2008-04-13
SOLVED by trying Hardy Heron current beta release. Live DVD works fine-- internet and all! Waiting patiently for final release. thanks to those who tried to help.

---

### Post by rdsherwood on 2008-04-13
> **adk46er said:**
> SOLVED by trying Hardy Heron current beta release. Live DVD works fine-- internet and all! Waiting patiently for final release. thanks to those who tried to help.
Glad you found a fix!

---

