---
title: "Windows n00b having trouble..."
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by THEpiGUY on 2007-02-04
First off, I'd like to say hello; I'm new here. Please be as patient as possible with me, because I have very limited knowledge on this. My system specifications are in my sig for reference, so if anything's incompatible with Linux you can let me know. I downloaded a distribution of ubuntu overnight, "Ubuntu 6.06 LTS, Ubuntu with Long Term Support" for "PC (Intel x86) desktop CD." So this morning, I burned the image to a CD-R. I went to try to boot off the CD, and I'm having some problems. I checked the CD for errors and it said 0 found. Afterwards, I went to Start or install Ubuntu, and it resulted with the following problem: "Failed to start the X server (your graphical interfacee). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? <yes> <no>" I pressed "yes," and a list popped up. Here's how it read,

(==) Log file : "/var/log/Xorg.0.log", Time: Sun Feb 4 10:39:52 2007
(EE) Unable to locate/open config file
xf86AutoConfig: Primary PCI is 3:0:0
Running "getconfig -X 70000000 -I
/etc/X11,/usr/etc/X11,/usr/lib/xorg/modules,/usr/lib/X11/getconfig -v
0x10de -d 0x0092 -r 0xa1 -s...

That was all I managed to write before the following popped up underneath:

User not known to the underlying authentication module [7-8 of these]
* INIT: Id "1" respawning too fast: disabled for 5 minutes.
* INIT: Id "2" respawning too fast: disabled for 5 minutes.
* INIT: Id "5" respawning too fast: disabled for 5 minutes.
* INIT: Id "6" respawning too fast: disabled for 5 minutes.
* INIT: Id "4" respawning too fast: disabled for 5 minutes.
* INIT: Id "3" respawning too fast: disabled for 5 minutes.


I then restarted and tried safe graphics mode. I got pretty much what's stated above again, except after the last line, I had "* INIT: no more processes left in this runlevel." Does anyone know what's going on, or what to do next? I'm open to any suggestions. Like I said, I'm new to this, so I may not understand all terminology. If you need any more information, let me know and I'll see what I can get. Thanks in advance for any help.

---

### Post by lamego on 2007-02-04
When the LiveCD can't setup the graphical interface you should try install using the Alternate CD .

---

### Post by THEpiGUY on 2007-02-04
Could you tell me where I can download that? Is the alternate CD something I must buy? I googled it and couldn't come up with it, sorry. Thank you though for the suggestion, I'll try whenever I figure out where to get it.

---

### Post by Maestro23 on 2007-02-04
> **THEpiGUY said:**
> Could you tell me where I can download that? Is the alternate CD something I must buy? I googled it and couldn't come up with it, sorry. Thank you though for the suggestion, I'll try whenever I figure out where to get it.

No need to google, its at this site: [http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

---

### Post by THEpiGUY on 2007-02-04
> **Maestro23 said:**
> No need to google, its at this site: [http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

Oh, wow. :lolflag: Can't believe I didn't see that. Thank you very much, I'll give it a try now.

edit: oooh, big file. It'll probably take around 5 hours to download. I'll let you know if I'm having problems later on today. So far though, thanks everyone!

---

