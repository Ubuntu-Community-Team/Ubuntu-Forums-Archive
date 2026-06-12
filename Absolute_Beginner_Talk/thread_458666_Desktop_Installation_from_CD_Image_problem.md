---
title: "Desktop Installation from CD Image problem"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by koz-man on 2007-05-29
I am a new Ubuntu user on my laptop and love it.  So I got another pc out to install it.  It has a **40GB Harddrive, Pent4 Processor, 500MB of RAM, it's a Dell ****OptiPlex GX240** **Desktop**, about 4 years old.  I took the desktop and reinstalled windows xp over entire hard disk - 1 partition created.  Then I did a defrag.  Windows works fine.  So then I slap the very same Ubuntu CD I used to successfully install on my laptop (which went without a hitch) into the desktop pc.  problems!!!!!

I did a CD integrity check and it says the disc has no errors.

I have tried installing, no kidding here, everynight for the past 5 days, so that means about 7 times that I can recall.

Still no successful installation - one time it got to 50% installed and then suddenly it rebooted.

Currently it takes about 20 minutes to boot from the CD, i think it's getting slower everytime.   Right now it won't even boot all the way.  Every time I get a Gnome Daemon Settings Error.  After I close that error all i hear is the cd driver running like a workhorse but nothing is happening on the screen or very little.  right now all i can see is the install icon and the ubuntu logo.  when i try to move the mouse it takes about 10 seconds b4 it registers and then it moves for a little.  when this happens i can only do a force shutdown and try again tomorrow.  last night i let it run for few hours and checked back and it still had not progressed beyond the install icon.  

Again I am new but this had got me really confused.  Laptop fine, desktop no worky.

is there a different version i should be using for a pentium desktop vs pentium laptop?

---

### Post by deadgobby on 2007-05-29
Please post your PC specs. That is very very key on given details on your PC. Need CPU type and speed, Ram amount, Vid card if any, and so on. If it is 4 years old you may have to slow of a CPU and little ram. Thus a different version on Ubuntu like Xubuntu, Damn Small Linux, or DeLi Linux. 
GObby

---

### Post by koz-man on 2007-05-29
**40GB Harddrive, Intel Pent4 Processor, _256MB_ of RAM, it's a Dell ****OptiPlex GX240** **Desktop** - 1.70GHz speed

i think it's an ATI Radeon VE - for video.  

is that enough? i don't know much else about what it has.

---

### Post by zvacet on 2007-05-30
Maybe this is not popular but try alternate Cd.

---

### Post by koz-man on 2007-05-30
> **zvacet said:**
> Maybe this is not popular but try alternate Cd.
What is the Alternate CD?  I have only heard a little about that.

---

### Post by deadgobby on 2007-05-31
I think it it your ATI card that may be the cause. YOu may have to edit xorg before install.
GObby

---

### Post by apunc1 on 2007-05-31
> **koz-man said:**
> What is the Alternate CD?  I have only heard a little about that.

with the alternate cd there is no live session, just installation. since you only have 256 mb of ram this might help out a bit. it is an older computer and sometimes they can be ornery with live cds.

[http://us.releases.ubuntu.com/feisty/](http://us.releases.ubuntu.com/feisty/)
scroll down for alternate cd install. you need the first one, i386.iso

---

### Post by koz-man on 2007-05-31
can you explain how to edit xorg?

---

### Post by koz-man on 2007-05-31
thanks -- i will download the alternate cd and try that.

---

### Post by deadgobby on 2007-05-31
I think you may have the same problem with Xububtu with the ATI card. 
You can manually edit your /etc/X11/xorg.conf file and type in the desired resolutions, or boot in to recovery mode and run "sudo dpkg-reconfigure xserver-xorg"
 You could make a new post on your PC system. It should run fine with the amount of ram and CPU speed. It is the ATI card causing your woes. Granted ubie has great vid card detection, but why is it playing hard ball. I do not know vid config all that well. Not my stong points, but working on it.
Gobby

---

