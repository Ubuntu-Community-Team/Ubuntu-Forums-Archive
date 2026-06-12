---
title: "ndiwrapper"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Keithod on 2006-11-04
Hi all,

You were kind enough to help me before, I hope you can do it again!

I'm trying to install my Belkin wireless card with linux. The drivers it uses for Windows are the quiet popular bcmwl5.inf/bcmwl5a.inf however if I install them with ndiswrapper it says drivers installed [after using ndiswrapper -l] but it doesnt say hardware present. I also uninstalled the bcm43xx driver that comes pre-installed with linux, as it says in the tutorial. After doing this my wireless card disappeared from the Networking options when one goes to System>Admin.>Networking....

I downloaded the latest ndiswrapper yesterday with a wired connection in Linux, I cant build ndiswrapper with make commands because it gives me errors [I was logged in as root too.] I am using Ubuntu linux but I dont know if its drapper, hoary or breezy [I dont even know what they are!] All I know is that I downloaded ubuntu as a live CD, tried it out, liked it then installed it on the hard-drive and have had problems with wireless cards.

Oh this information may be useful to you, I found it after doing lspci command:
01:0.0 Net controller Broadcom Corp. BCM4318 [Airforce One 54g] 802.11g Wireless LAN Cont (rev 02)

I'm not very good with the command line and all that I've written above comes from reading tutorials...

Just one note, it said in the tutorial that I need to install all the .sys files aswell, if I install them for ndiswrapper it says installed but after doing the -l command it says they're invalid drivers...does this mean I should remove them??

Sorry for the big long message, again many thanks. It's always appreciated.

---

### Post by Keithod on 2006-11-04
Update:

I managed to get it to say hardware presend. I used this

 ndiswrapper -d devid:driver

Turns out my device id is 14e4:4318 I dont know what that other number I gave you is...

Anyway it now says hardware present BUT still no wirless connection...

---

