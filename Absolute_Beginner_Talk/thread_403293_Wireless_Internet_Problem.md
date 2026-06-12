---
title: "Wireless Internet Problem"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by wtfchuck on 2007-04-06
I JUST freshly installed Ubuntu. I have no internet. I've messed around with the network connections, not sure how to browse or scan for connections like in windows because it should automatically find it.

I've tried a lot of things that involved the terminal, nothing really worked.

Where do I start?

Under my network card this is what i see. BCM4318 [Air Force One 54g] 802.11g Wireless Lan Controller.

I have a Dell Inspiron B130 laptop.

Linksys Router.

I didn't dual boot as far as I know.

---

### Post by caffienefree on 2007-04-06
Give this ([http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/](http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/)) a try. Worked for me, I could never get the whole firmware cutter job to work, using ndiswrapper was easier.

EDIT: Keep in mind you'll need the drivers specific to your card. Check on dell's website.

---

### Post by wtfchuck on 2007-04-06
Error: module ndiswrapper does not exist in /proc/modules

EDIT: I don't know how to download something without internet.

---

### Post by caffienefree on 2007-04-06
ndiswrapper utils should be on your cdrom. However, you're going to need to get your driver from somewhere, either brought over on a floppy/USB or on a previous installation?

That message is fine. It means you didn't have it installed to begin with, which is okay, because you're about to install it.

---

### Post by wtfchuck on 2007-04-06
the cdrom is no longer opening like a program. now its opening like a folder.

can i get my driver from a windows disk?

edit: ndiswrapper is in my package manager.

---

### Post by wtfchuck on 2007-04-06
When trying to install the driver.

Error: No Suitable Application

Cannot open /media/cdrom0/base/r115321.exe: No application suitable for automatic installation is available for handling this kind of file.

---

### Post by caffienefree on 2007-04-06
That .exe is a self-extracting archive that contains the files you need: the .inf file and the .sys file. The problem is that linux doesn't treat .exe the way windows does. You need to extract those on a windows partition, and then use them.

---

### Post by wtfchuck on 2007-04-06
How do I do that?

---

### Post by caffienefree on 2007-04-06
Well, actually, scratch that. I was just messing with the file on my laptop, it looks like you can just unzip it. Download [http://ftp.us.dell.com/network/R102320.EXE](http://ftp.us.dell.com/network/R102320.EXE) . Open up a terminal, go to wherever you saved the file. Then type:

unzip R102320.EXE

and that will give you bcmwl5.inf and bcmwl5.sys, which are what you need.

---

### Post by wtfchuck on 2007-04-06
lol it cant find it. this is ridiculous.

---

### Post by caffienefree on 2007-04-06
What do you mean, it can't find it?

Keep in mind that the work is worth it in the long haul. :D

---

### Post by wtfchuck on 2007-04-06
when i typed what you told me in terminal it said it could not find the file.

unzip: cannot find or open R1023020.EXE, R102320.EXE.zip or R102320.EXE.ZIP

do you have aim or msn?

---

### Post by caffienefree on 2007-04-06
AIM -> chaosisreality13

---

