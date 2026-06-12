---
title: "Which 56k Modem is better under Ubuntu?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-03-18
Which 56k modem do people recommend for Ubuntu, Software or Hardware? I have a software modem and am seriously thinking about changing to a hardware modem as I can't get the software modem going, and would like to hear the ubuntu communities opinion on which type works better.

---

### Post by Paul_world10 on 2007-03-18
I enjoyed using the   US  Robotics   5610 B   internal PCI  unit.  Its basically plug and play when you set it up with    'pppconfig'.

---

### Post by yabbadabbadont on 2007-03-18
A hardware based modem will, by definition, work better than a software based one.  It places almost no load on the system and is guaranteed to be compatible.

---

### Post by Matchless on 2007-03-18
Your best bet is using an external serial port modem, as this does not require any driver installations this is not the same as an external USB modem!
 I have managed to get Smartlink, Lucent, Intel536, Intel537 and Conexant internal PCI modems working. 
Conexant can be a bother as the free opensource linux drivers are limited to certain models and also to what version of Ubuntu you are using, there are also issues when you start with later versions such as Edgy. On a bit of a downside, you can get a free Conexant linux driver from Linuxant, but it has a max speed of 14400, which you can open up to 56k on by registering and paying them a fee, but will get you on line for free or just for testing.
Search the Ubuntu forums for your modem, there are many howto's. Also have a look at the wiki dialupmodemhowto. The Intel modems have native linux support.
Enjoy

---

### Post by Sam Clemens on 2007-03-18
Have you tried the scanmodem tool at the linmodem site to get your 56k software modem going?

[http://www.linmodems.org/](http://www.linmodems.org/)

Another option is to try installing slmodemd and see if it just works.

You've probably done all this but I had to ask.

---

### Post by Wake Rider on 2007-03-19
> **Sam Clemens said:**
> Have you tried the scanmodem tool at the linmodem site to get your 56k software modem going?

[http://www.linmodems.org/](http://www.linmodems.org/)

Another option is to try installing slmodemd and see if it just works.

You've probably done all this but I had to ask.

I have used the scan modem and it couldn't find a modem in my computer.

---

### Post by argie on 2007-03-19
I have an old Motorola VoiceSURFR which works (after a fashion), I just have to "Activate" in network-admin and it connects, "Deactivate" and it disconnects. Unfortunately I need to use gksudo to do that. But it works straight out of the box with nothing to do but enter the number to dial and user/pass.

---

### Post by unisol on 2007-03-19
i use a diamond supra 56k external modem on ttyS0 and it worksflawlessly in both dapper and debian etch. you can purchase one cheap on ebay.

---

