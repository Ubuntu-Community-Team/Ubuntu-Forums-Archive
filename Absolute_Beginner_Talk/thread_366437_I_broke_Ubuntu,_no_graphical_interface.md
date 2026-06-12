---
title: "I broke Ubuntu, no graphical interface"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by jonsayer on 2007-02-20
Ok, so I was trying to install a driver for my Ati graphics card acording to the info here:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I did these commands:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

I followed it until it told me to restart, which i did. when ubuntu restarted, it gave me this error message:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

<yes> <no>

Of course i hit yes. After that, I get some information. I don't want to copy all of it, but this is what seems relevant:

Module Loader Present.
Markers:(--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) Warning, (EE) error, (NI)not implemented, (??) unknown.
(==) Log File: "/var/log/Xorg.0.log", Time: (approximately the time i added in the changes)
(==) Using Config file: "/etc/X11/xorg.conf

So yeah. apparently, I don't have any graphical interface right now. what do i do?

---

### Post by ComplexNumber on 2007-02-20
does typing the following on the commandline help:
**sudo dpkg-reconfigure xserver-xorg**

---

### Post by jonsayer on 2007-02-20
it went through and reconfigured the file. a can't guarantee it worked. i will get back to you in a sec... i am going to restart it

---

### Post by jonsayer on 2007-02-20
nope. I think i might have messed something up, tho, so i am gunna go back in and do something differently

---

### Post by Maestro23 on 2007-02-20
> **jonsayer said:**
> nope. I think i might have messed something up, tho, so i am gunna go back in and do something differently

If you can't get it to work following the guide, you can always try the Envy script.

[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

---

### Post by jonsayer on 2007-02-20
i am at an option that has several [ ] things, some with * in them.  how do I check something?

---

### Post by jonsayer on 2007-02-20
I have an ATI, not nVidia card. that tutorial wouldn't do anything I think

---

### Post by Maestro23 on 2007-02-20
> **jonsayer said:**
> I have an ATI, not nVidia card. that tutorial wouldn't do anything I think

Works for both. Read his first paragraph.

---

### Post by jonsayer on 2007-02-20
you know, two second before you posted that, I realized that

He should put ATI into the headline.

Thanks anyway, i will post again after i try that one

---

### Post by jonsayer on 2007-02-20
YES YES! it works! eureka!

---

### Post by Maestro23 on 2007-02-20
> **jonsayer said:**
> YES YES! it works! eureka!

Congrats man.:guitar:

---

