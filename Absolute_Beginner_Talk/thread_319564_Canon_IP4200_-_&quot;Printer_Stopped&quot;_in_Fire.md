---
title: "Canon IP4200 - &quot;Printer Stopped&quot; in Firefox, Works Elsewhere"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by linux4me on 2006-12-15
I installed the driver for my Canon IP4200 according to the information in the wiki here: 

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

and it seems to work fine in Open Office, but it won't print in Firefox. I get a pop-up that says the print job has begun, the printer icon appears in the panel, but I don't get any print output. If I open the print dialog, it shows "printer stopped" and resuming it manually does no good.

I tried using the BJC4200 and IP4000 drivers. The former works, but prints 1/3 actual size. The IP4000 driver didn't work at all. Since the BJC4200 driver works, I'm thinking it's something particular to the driver I'm using (Canon's own Linux driver v. 2.60). 

I'm such a noob I haven't been able to figure out where to go from here despite reading all the posts I can find on the IP4200, Canon, and printing. 

It's a fairly new printer, so I would like to get it working and don't want to buy a new one if I can avoid it.

I would really appreciate some help.

---

### Post by linux4me on 2006-12-16
Still working on this...

I found out there is an error log for CUPS in /var/log/cups and found this is the error that is generated when I try to print from Firefox:

E [16/Dec/2006:10:25:11 -0600] PID 5587 (/usr/lib/cups/filter/pstocanonij) crashed on signal 11!

Now I have to figure out what in the world that means! 

I'll post if I find more or find a fix. It looks like there are others with the same problem, and it may not be just the IP4200.

---

### Post by linux4me on 2006-12-16
I found a solution to my Canon IP4200 problem.

I bought an HP Photosmart C3180--which I found on the 'prints perfectly' list at linuxprinting.org--and it prints, well, perfectly.

---

### Post by mapman on 2007-01-18
I recently purchased a pixma ip1600 and had similar issues even after following instructions here : [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

My problem was that I couldn't print from firefox, it kept saying stopped in my printer properties.  On a hunch I changed my paper size from A4 to letter and from then on it worked!  So far so good.

---

