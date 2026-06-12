---
title: "Can't boot into Ubuntu"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-04-02
I bought an Ubuntu gamers edition DVD, so I popped it in to my cd drive and the ubuntu screen showed up. So I clicked start from cd and the dragon theme showed up, but then it gave me a huge error. Finally it gave me some message about the screen and I turned it off. I have a Dell Inspiron e1505 laptop. What should I do?:guitar:

---

### Post by ArieT on 2007-04-02
> **mikecomua said:**
> What should I do?:guitar:
Write down those error messages and post them.

---

### Post by mikecomua on 2007-04-02
Failed to start the X server (your graphical interface)
It is more likely that it is not set up correctly. Would you like to view the X server to diagnose the problem. [17178756.068000]bcm43xx:Error:microcode
"bcm43xx_microcode5.fw" not available or load failed.
<Yes>   <No>

When I click yes this shows up
Error:Microcode "bcm43xx_microcode5.fw" not 
available or load failed. Version 7.11
Release date: 12 May 2006
Protocol version 11, Revision 0, Release 7.11.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.17-10-generic #2 SMP Fri
Oct 13 18:45:35 UTC 2006 i686
Build date: 07 July 2006
or load failed. reporting problems, check [www.wiki.x.org](www.wiki.x.org) 
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown
(==) Log File:/var/log/Xorg.0.log time: Mon Apr 2 19:24:36 2007
(==) Using config file: "/etc/X11?xorg.conf"
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1)
found
(EE) I810 (0): No video BIOS modes for chosen depth.
(EE) Screen(s) found , but none have a usable configuration.
Fatal server error:
no screens found
This is a blue and white and red screen with lots of weird letters around that.

Then a black screen pops up:
firmware_helper [4970]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw'
for device '/class/firmware/000:0c:00.0' with driver 'bcm43xx'
[17179669.95200]bcm43xx: Error:Microcode "bcm43xx_microcode5.fw" not available
error load failed.
then  I turn my PC off  and boot into Xp:guitar: Thanks!

---

### Post by zvacet on 2007-04-02
```
sudo dpkg-reconfigure xserver-xorg
```

pick **vesa **driver

---

### Post by mikecomua on 2007-04-05
Where should I enter it?

---

### Post by h0ax on 2007-04-05
You're just trying to boot into a Live CD?
You need to specify framebuffer options on boot it seems.
Need some more details about when this is occuring..

---

### Post by mikecomua on 2007-04-05
yes, i' m trying to boot into a Live CD, but what's a framebuffer?

---

### Post by mikeyphi on 2007-04-05
> **mikecomua said:**
> Where should I enter it?

Open a terminal (APPLICATIONS - ACCESSORIES)

---

### Post by mikecomua on 2007-04-05
I CAN'T boot into Ubuntu

---

### Post by mikeyphi on 2007-04-05
> **mikecomua said:**
> I CAN'T boot into Ubuntu

Sorry!!!! I guess you will need to use the Live CD.

---

### Post by mikecomua on 2007-04-05
Wait, I have a Live CD, but I can't boot. Maybe  I should try Ubuntu in safe graphics mode?

---

### Post by Arcanex0r on 2007-04-05
I'm having the same problem.  Here are the details as I can present them:

I'm trying to install Fiesty Fawn from the LiveCD.  I pop in the CD and restart the computer.  I get to the boot menu:

Start or install ubuntu
start in safe graphics mode
etc.


When I try either of those top two, this set of errors occurs:

> Failed to start the X server (your graphical interface)
It is more likely that it is not set up correctly. Would you like to view the X server to diagnose the problem. [17178756.068000]bcm43xx:Error:microcode
"bcm43xx_microcode5.fw" not available or load failed.
<Yes> <No>

When I click yes this shows up
Error:Microcode "bcm43xx_microcode5.fw" not
available or load failed. Version 7.11
Release date: 12 May 2006
Protocol version 11, Revision 0, Release 7.11.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.17-10-generic #2 SMP Fri
Oct 13 18:45:35 UTC 2006 i686
Build date: 07 July 2006
or load failed. reporting problems, check [www.wiki.x.org](www.wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown
(==) Log File:/var/log/Xorg.0.log time: Mon Apr 2 19:24:36 2007
(==) Using config file: "/etc/X11?xorg.conf"
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1)
found
(EE) I810 (0): No video BIOS modes for chosen depth.
(EE) Screen(s) found , but none have a usable configuration.
Fatal server error:
no screens found
This is a blue and white and red screen with lots of weird letters around that.

Then a black screen pops up:
firmware_helper [4970]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw'
for device '/class/firmware/000:0c:00.0' with driver 'bcm43xx'
[17179669.95200]bcm43xx: Error:Microcode "bcm43xx_microcode5.fw" not available
error load failed.

From the research I've done, the bcm43xx is the wireless driver ubuntu is trying to use, but it's not compatible with the wireless on the Inspiron 1505.  Is there a way to disable this check or do anything so I can actually finish the install, and then go back and fix the wireless driver?

---

### Post by mikecomua on 2007-04-06
I have the same problem.  I know that going into BIOS and disabling wi-fi & bluetooth  won't help either. Do you have Edgy?

---

