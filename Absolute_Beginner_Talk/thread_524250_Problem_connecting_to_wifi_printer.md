---
title: "Problem connecting to wifi printer"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by pepe0818 on 2007-08-12
I am trying to connect to a HP PSC1600 series printer through a Airport Express router. I thought I had it working but I found that the printer is only detected when I have my Mac computer turned on. I have Ubuntu installed on a dual boot Fujitsu laptop with Win XP. From Win XP the printer is detected and I can print. If I have the Mac on when I boot Ubuntu then after the wifi connection is established the printer shows in "Printers" but if the Mac is off the printer is not detected and does not show in "Printers".  I have no problem connecting to the internet. 
How do I set it up so I can print without having the Mac turned on?

Computers
Powerbook G4 - Mac OS X
Fujitsu Lifebook Dual boot Win XP and Ubuntu 7.04

Router
Airport Express

Printer
HP PSC1610

---

### Post by pepe0818 on 2007-08-13
I think I've finally solved this problem. I installed "avahi" and "airport-utils" and added the printer address obtained from "avahi-directory" and it seems to be working.

---

### Post by theox26 on 2007-08-22
just to clear this up for those who found this and also didn't understand exactly how it was done.

My HP Deskjet worked by using the IP address of my router and the HP directjet printer driver ( or socket://). see here (towards the bottom) [http://svenand.blogdrive.com/archive/14.html](http://svenand.blogdrive.com/archive/14.html)

I think most should be set to that option.

Alternatively, you can put [http://localhost:631](http://localhost:631) in a web browser to configure through cups system, which i am also told works. see here [http://ubuntuforums.org/showthread.php?t=343542](http://ubuntuforums.org/showthread.php?t=343542)

hope that save some people any more searching

---

### Post by JEBB on 2007-08-23
I just used the directions as given in: [http://svenand.blogdrive.com/archive/14.html](http://svenand.blogdrive.com/archive/14.html) and it worked!!  Thanks for the reference.  

Following directions I found on this forum I had been blindly fooling around trying to get my Linux computer to print to my Canon BJC 2100 attached to my AEBS for many months and had pretty much given up.  Now I can print to that printer from my Mac, my Windows machine and my Ununtu machine.  What a struggle!

---

