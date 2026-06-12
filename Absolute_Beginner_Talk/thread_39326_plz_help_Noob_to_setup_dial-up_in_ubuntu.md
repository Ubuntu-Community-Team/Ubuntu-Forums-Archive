---
title: "plz help Noob to setup dial-up in ubuntu"
date: 2005-06-04
forum: Absolute Beginner Talk
---

### Post by KaRpiX on 2005-06-04
hi, i just installed ubuntu. this is the first time that im using linux. i having great difficulty getting my dial up connection to work.

i have an internal modem. it does detect it in device manager, but should i get other drivers than ubuntu`s? And where?

next, i have absolutely no idea how to set up a dialup connection!!!

plz help, \\:D/

---

### Post by poofyhairguy on 2005-06-04
[QUOTE=KaRpiX]hi, i just installed ubuntu. this is the first time that im using linux. i having great difficulty getting my dial up connection to work.

i have an internal modem. it does detect it in device manager, but should i get other drivers than ubuntu`s? And where?

next, i have absolutely no idea how to set up a dialup connection!!!

plz help, \\:D/[/QUOTE]

What kind of modem is it. Not all are built the same. Some are winmodems, some are hardware modems (yeah!).

---

### Post by KaRpiX on 2005-06-05
its some cheap 56k internal modem. dont know the make. WinXP detecs it as Soft v90 Voice Speakerphone Modem

plz help

---

### Post by mtron on 2005-06-05
That means - most of the time - its a crappy Windows modem, where the processor  does most of the work, that's the reason they can sell them for 10 bucks.

The problem is that the manufacturers are not providing the source code, nor the specifications needed for someone to write a driver.


Quite difficult to get them working in ubuntu. It needs usually a small kernel patch

see [this](http://www.ubuntuforums.org/showthread.php?t=20546)  thread for a tip how to do it, or search the forum, there are many posts around howto do this

---

### Post by Trevor 42 on 2005-06-05
I have found using an external (serial) modem works ok (insofar as the device is recognized by the O/S and it dials when instructed to do so). This device cost me £27.00 but I consider well worth it as (a) It is easily transferrable & (b) It is independant of any particular O/S.

So far I have configured the modem, dial up numbers etc by using PPPConfig in Root Terminal. The modem works (I can hear it dialing etc)

However, I am still having problems connecting to AOL, I believe that this is more to do with the way AOL authenticates users than an Unbuntu problem (not CHAT or PAP but another protocol unique to them). I read that using a script called Pengaol solves this problem - does anyone have any experience of this?

I am grateful for the help I have received from these boards - Thanks.

Kind regards,

Treor

---

### Post by mingus on 2005-06-06
The following may be useful to you:

[http://www.ubuntuforums.org/showthread.php?t=20546](http://www.ubuntuforums.org/showthread.php?t=20546)

Also, this website.  Getting a software modem setup in Linux can take a lot of patience, but they can work.  You will find a simple tool on this site (scanModem) which will tell you your modem's chipset and possibly if there is a driver for it.  There is a section on the site for each of the most common chipsets, with links to drivers and installation instructions.  As a rule, you do not need to touch the kernel but you may need to do some compiling and/or module loading and/or patching.  Each one is different.

[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)

---

