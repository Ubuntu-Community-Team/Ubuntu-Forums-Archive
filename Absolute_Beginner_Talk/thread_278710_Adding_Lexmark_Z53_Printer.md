---
title: "Adding Lexmark Z53 Printer"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by Craftycorner on 2006-10-16
Please guide me through the addition of my Lexmark Z53 printer to Cups or another of the installed printing systems.   Printers-Systems Settings list five.](*,)

---

### Post by ReaderRat on 2006-10-16
> **Craftycorner said:**
> Please guide me through the addition of my Lexmark Z53 printer to Cups or another of the installed printing systems.   Printers-Systems Settings list five.](*,)
Have you tried going to....System>Administration>Printing and adding the printer there?

---

### Post by ReaderRat on 2006-10-16
I have read that it is a real bummer to try and use a Lexmark. Only one class of them works with Ubuntu, and I don't remember which one.

---

### Post by Craftycorner on 2006-10-16
is there any way to make Ubuntu think this is just a generic printer or another type?  I'm not fussy aobut how it looks as I'm looking for only black & white print.

---

### Post by ReaderRat on 2006-10-16
I believe it would have to be a generic **Lexmark** driver, and I did not see any. Follow the Guide  Below (in my signature to go to Hardware Compatibility lists.

---

### Post by raqball on 2006-10-16
Here you go

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z53](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z53)

---

### Post by wsscott on 2006-10-29
Had the same problem. Upgraded to Ubuntu 6.10 and it now works!  Set up using the printer administration procedure under (System --> Administration --> Printing) Selected the gutenprint-ijs-simplified.5.0 driver and Z53 was then available as a lexmark printer.  Also using "local printer" and "printer port LPT#1"

I used the upgrade script gksu "update-manager -c".  Took a while but worked great.

Good luck

---

### Post by kanys on 2008-02-24
Got the Lexmark Z53 to work in Dapper (6.06 LTS).  Here's how I did it.  Following advice posted by the good folks on Launchpad, I

Logged on to [ftp://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu_packages/gutenprint/](ftp://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu_packages/gutenprint/)

then downloaded and installed these packages (in this order)

libgutenprint2_5.0.0-2ubuntu1_i386.deb
cupsys-driver-gutenprint_5.0.0-2ubuntu1_i386.deb

(I got some kinda message saying that older software was available in a software channel, but just clicked "OK" on that and it went away)

After this, I installed the Z53 by clicking System, Administration, then Printing, then doubleclicking on New Printer and choosing Lexmark, then Z53.  Lo and behold, it printed a test page (rather than shooting out a blank)

Just to doublecheck, I printed these notes from Text Editor (on the back of the test page, to save paper and natural resources).  Worked great!

Evidently, there's some kinda known problem with out-of-date Gutenprint drivers in Dapper that the packages above update.  Hey, it worked for me, and if it works, it's good!

---

