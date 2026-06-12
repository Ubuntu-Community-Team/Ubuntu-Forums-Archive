---
title: "[SOLVED] HP Laserjet 1018 Does not work"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by fuwkej on 2008-02-28
On Ubuntu 7.10, the HP Laserjet 1018 does not work (Feisty Fawn did not work either). At first it recognized the device and appeared in printers but would not print or respond to printing test page. After following several different postings, going through one it said to remove the printer and after that I was unable to reinstall the printer. Now my computer cannot even find the printer, this may be simple but I cannot find the URL for the printer so I can install it in CUPS. I thought it was USB://HPLASERJET%201018 or something but several variations were not right.. Anyhelp in this matter is appreciated, thanks.

Here are the results of lsusb.. which looks like it no longer registers (the printer is on and I attempted rebooting it)

[HTML]lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
[/HTML]

Dell preinstalled Inspiron 1420, outstanding computer.
Intel Centrino, n series.

---

### Post by oedha on 2008-02-28
i'v check it in [http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)
it shoulg work fine....
maybe you can try :==> [http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018)

---

### Post by fuwkej on 2008-02-29
Those posts were of no use, I had tried them previously. I finally got my computer to recognize the printer, I just let it sit overnight.

After that I mixed and matched stuff from the help files and figured out how to do this. You have to install the firmware, I mixed and matched from the forums (since download locations changed)

First, download the firmware here:
[http://foo2zjs.rkkda.com/firmware/sihp1018.tar.gz](http://foo2zjs.rkkda.com/firmware/sihp1018.tar.gz)

Then, extract sihp1018.img

Next go to the directory the .img file is in, in terminal and do this:

[HTML]sudo bash[/HTML]

enter your password

[HTML]arm2hpdl sihp1018.img > /usr/share/foo2zjs/firmware/sihp1018.dl[/HTML]

I rebooted the HP Laserjet 1018 and printed a test page, it took a few seconds, I restarted the printer with CUPS (if it's installed, [http://localhost:631/printers/](http://localhost:631/printers/)) and the test page flew out. 

A lot of work but it works now! Hopefully this will help someone else in the future.:)

---

### Post by fuwkej on 2008-03-09
Well now my printer is on the scitz again and does not want to print. Even the steps I tried before now don't work. No impact, no idea.

---

### Post by Malta paul on 2008-03-09
Hi,
I must admit I don't Know what your problem is. If its any comfort I also have a HP Laserjet 1018 printer which has worked great for me with Ubuntu 7.04 and now with 7.10. I did have to mess about a bit to get it to work! 
You are correct saying that the first thing that this type of printer requires is firmware to be installed first (once only), which I did installed again when I upgraded to 7.10. then I installed the driver.
Here a link that may be of help:[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)
Wish you luck :(

---

### Post by fuwkej on 2008-03-10
Okay, I started at the link you gave me and followed the steps to a tee, and no joy. Then I tried the directions for Ubuntu 7.10, no joy. Then I figured what the hey, and followed the steps for 7.04 and changed the printer from network printer to local detected printer and it works like a charm again! I know I use to temp fix this printer by hooking it up to a windows computer and not turning it off, it always seem to print once windows initiated it. So this time I'm not turning that badboy off! (Eventually the power will go out and I'll see if it still works afterwards). Thanks for the assistance!  :)

---

### Post by fuwkej on 2008-03-15
This thing is horrible, it was working great until today and now for no reason it stopped working again. Ubuntu is not very well configured for this printer and it needs to be removed from the supported list. My last notebook did the same thing when I had Feisty Fawn, I'm now using Gutsy on a prebuilt Dell inspiron 1420. I seem to beable to temp fix it after I mess with things for about 4-5 hours but nothing every works indefinately even if I leave everything on. :confused: And now I have two printer links in adminastration, but that's the least of the problems.

---

