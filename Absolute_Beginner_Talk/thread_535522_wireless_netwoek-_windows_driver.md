---
title: "wireless netwoek- windows driver"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by aanpudur on 2007-08-26
I need to install the drivers for wireless network .

i am using INSPIRON E1405 laptop. I have downloaded the ndiswrapper module and did a make.
as per the instrctions i need to install widnows driver for it.
where can i find the driver to instal?
I could not find it in sourceforge.ndiswrapper.net site 

thanks in advance

---

### Post by tuito on 2007-08-26
1. Start Synaptic and type ndis  ......... install ndiswrapper and ndisgtk
2. Locate in system menu WWD /Windows Wireless Driver/ or type ndisgtk in "Run Command"
3. Locate and install Windows driver for your card

Have fun:guitar:

---

### Post by anewguy on 2007-08-26
If you are not sure what your driver files are called and where they are located so that you can use them with ndiswrapper, try going to Dell support for your laptop and downloading the driver there.  It may be a self-extracting archive (.exe).  If so, open the file with archive manager and extract the .inf and .sys file for your wireless.

Since I don't know what you have, could you also post the output of  "lspci"  back here?  It may very well be that there is an already existing tutorial for your wireless card.:)

---

### Post by chrome307 on 2007-08-26
I managed to do this .... have a look at this thread for instructions:

[http://ubuntuforums.org/showthread.php?t=534617](http://ubuntuforums.org/showthread.php?t=534617)

---

