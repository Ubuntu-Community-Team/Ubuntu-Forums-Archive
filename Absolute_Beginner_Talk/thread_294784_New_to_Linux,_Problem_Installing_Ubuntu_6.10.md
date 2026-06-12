---
title: "New to Linux, Problem Installing Ubuntu 6.10"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Katagai on 2006-11-07
I'm currently trying to install Ubuntu 6.10 (ubuntu-6.10-desktop-i386) on my Dell Inspiron 1100 laptop. So far, whenever I attempt to run the installer in the Live session, my CD-ROM drive eventually stops reading the disc and the entire session freezes up. Any help is appreciated. I've been at this for about 4-6 hours with no luck.

Laptop specs:
Dell Inspiron 1100
256MB ram
27GB HDD
BIOS version A32

Also of note: when I begin the live session, I recieve two driver errors (I believe they were Broadcom drivers) and once the interface begins to load, an error window appears notifying me that GNOME failed to load and some themes or sounds will not work. Is this a problem with the CD?

---

### Post by Bachstelze on 2006-11-07
Hi and welcome to Ubuntu :)

If you want to install, I'd recommend using the Alternate CD instead. The installer is text-based so it's less pretty but also less likely to fail on you.

---

### Post by steve.horsley on 2006-11-07
I agree with HymnToLife - try the Alternate installer instead. Also, yes it could just be a problem with the CD. If in doubt, chack the MD5 chacksum of the downloaded image, and burn at the lowest possible speed.

---

### Post by Sef on 2006-11-07
For some reason, the alternate CD is more likely to work than the Live CD for installing.

---

### Post by Katagai on 2006-11-07
Thank you so much, the Alternate CD did in fact work, but now I'm stuck trying to figure out how to get my wireless card working. At the moment, I'm giving this ndiswrapper package a try.

---

### Post by localuser on 2006-11-07
> **Katagai said:**
> Thank you so much, the Alternate CD did in fact work, but now I'm stuck trying to figure out how to get my wireless card working. At the moment, I'm giving this ndiswrapper package a try.

Have a look at the wifi HOWTO: 

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

---

### Post by Katagai on 2006-11-07
Well I'm stuck trying to compile ndiswrapper. I keep getting errors and I don't know what I'm doing wrong.

---

### Post by localuser on 2006-11-07
> **Katagai said:**
> Well I'm stuck trying to compile ndiswrapper. I keep getting errors and I don't know what I'm doing wrong.

Can you be more specific.  What are you doing *exactly* (as in commands) and what are the error messages?

---

### Post by Katagai on 2006-11-07
Well I don't think I need to worry about ndiswrapper anymore. Apparently I already have the correct driver installed. Problem is my wireless card is disabled. I don't know how to enable it. I read that some laptops have a FN+key command to enable/disable stuff, but I don't think my laptop has that, and I'm having no luck with searching on google. If it's of any help, my wireless card is a Dell TrueMobile 1300 and the driver is bcm43xx.

And as for my problems with compiling ndiswrapper, I'm getting alot of implicit declarations and undeclared variable errors when building the modules in step 2.

The instructions I followed were:

- Go into directory ndiswrapper-1.28
- *make distclean*
- *make* *Problems begin here*
- As Root *make install*

---

### Post by dca on 2006-11-07
First go to System -> Administration -> Device Manager
 
Find the Dell wireless card and see what driver(s) it is using on the right-hand column.  I may be blowing smoke, but I think the Dell is based on the Intel ProWireless series card (probably same thing, just a Dell sticker added) which should work out of the box...
 
Then go System -> Administration -> Networking
 
There you should see your wireless device and config accordingly...


I know it's not much help...

---

### Post by TheFD2 on 2006-11-07
I too am having a problem installing Ubuntu. I am using the Alternate CD. The CD asks me if I want to install in text mode or OEM. Which ever I choose, I get to the point where I can eneter an http proxy if I want to, the system freezes and I get a blue screen with a grey bar across the bottom. I am using the Alternate CD version 6.06.

Thanks.

---

