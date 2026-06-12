---
title: "Installing Beryl fglrx issue"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-08
When using this guide

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

to install beryl on my Inspiron E1505 with an ATI X1400 video card (it did not sane that is unsupported) I got the response:

FATAL: Module fglrx is in use.

to this command:

sudo modprobe -r fglrx


What should I do? Just continue on? Ive read that Beryl can really mess things up but I havent found anything dealing with this. 

Thanks in advance for any help.

---

### Post by Yasumoto on 2007-07-08
I've been trying to get Beryl to work with my E1505 and ATI X1400 card for a while without sucess. If you get it working let me know ... :X

(and if I somehow figure it out I'll let you know)

I'm just waiting in hopes that the compatibility issues will be resolved eventually.

---

### Post by swisscow on 2007-07-09
Reboot after the sudo mdprobe-r (whatever) command and try it again. Make sure you have edited your xorg though to pick up the ati/radeon driver instead (if this is in the instructions you are using of course!)

---

### Post by Nem1976 on 2007-07-11
I have Beryl running on my system with an Ati X1300 using the closed source ATI Drivers.   You will need to most likely used the Alternate method install which is what I did to get it working.

The only issue I have run across is I'm using XGL to get beryl working and games won't run under XGL I need to log out and log into the gnome session with out XGL.  No biggy since it's  work computer anyways but atleast I can still play games by just logging off and back in .

Here is the setups I used to install beryl.  I had it working in about 15-30 min's.  

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

I hope this helps you.

Nem

---

