---
title: "sonic stage on ubuntu through wine"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by dcalvani on 2007-06-20
hello there

I'll be eternally grateful to anyone who can explain what I should do to open Sonicstage 3.4 - which I installed on Ubuntu 7.04 through Wine. 

Sonicstage and MDburner are now sitting in my start menu under Wine. If I click on either, I get the following message:

"Before you can use the program you must restart your computer. After starting the computer, please log on as administrator". 

I don't understand what this means. Nothing happens if I restart my computer. I also tried to launch the program through Terminal 

~$ sudo env WINEPREFIX="/home/daniele/.wine" wine "C:\Program Files\Sony\SonicStage\Omgjbox.exe"

and I get exactly the same box with the same message. I seem to understand that Vmware might help. Is that correct?

Thank you.

---

### Post by Damanther on 2007-06-20
Not to avoid your problem. But have you tried any of the linux audio utils? Some of them work very well.

You can browse the multimedia pages on this forum to find popular ones.

---

### Post by eZtaR on 2007-06-20
It's always a good idea to check the [wine AppDB](http://appdb.winehq.org/appview.php?versionId=3876) before installing any application, to see what works and what doesn't.. and in this case the application does not work :(

But yeah i'd try to VMware it :)  [Here's](http://ubuntu1501.blogspot.com/2007/05/installing-vmware-in-feisty.html) a guide on how to install and use it :D

Hope my reply was helpful
/eZtaR

---

