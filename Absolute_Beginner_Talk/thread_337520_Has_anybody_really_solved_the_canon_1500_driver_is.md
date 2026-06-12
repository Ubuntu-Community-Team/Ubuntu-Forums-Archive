---
title: "Has anybody really solved the canon 1500 driver issue"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by birdseye on 2007-01-13
I have read all the earlier posts and tried to follow the routes suggested but still have a printer that wont work. Possibly something like my Sagem modem problem when the key was removing what came with Ubuntu, but in the case of the printer I cant find anything else to remove.

So has anyone got the canon printer working properly under ubuntu. If so, can you put the definitive complete solution to the problem on the board ie in steps that even a newbie like me can follow successfully? Please - so I can finally junk XP. Or try to.

No reflection on the earlier posts by the way - its my lack of linux skills that is the problem!](*,) ](*,) ](*,)

---

### Post by Sef on 2007-01-13
Is it a Canon Pixma ip 1500 that you have?

---

### Post by birdseye on 2007-01-13
yes

---

### Post by Sef on 2007-01-13
Check out [Turboprint]("http://www.turboprint.info").   They have some free drivers and one of them is for you printer.

---

### Post by Enverex on 2007-01-13
Their drivers may be "free" (highly misleading) but they print a massive Turboprint Logo and copyright information over some random point of every printout page as I so annoyingly found out with my S330 Photo, so I'd not recommend them.

Apparently it "mostly" works with the Guttenprint drivers though: [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-iP1500](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-iP1500)

---

### Post by birdseye on 2007-01-13
yes, I tried the turboprint route too and found the same problem. they say you can get round it by printing in draft bmode but that doesnt give good enough results.

---

### Post by Caraibes on 2007-01-13
see that :
[http://www.fedoraforum.org/forum/showthread.php?t=73920](http://www.fedoraforum.org/forum/showthread.php?t=73920)

My experience is that the iP1500 will only work under Red Hat/Fedora/CentOS/Blag, or under Mandriva/PCLinuxOS...

I tried in vain to have it printing under Ubuntu/Mepis, or under Zenwalk... Didn't work.

This is one of the reason I run Mandriva 2007 on my main PC (I run Ubuntu on my laptop, and Edubuntu on another PC)...

---

### Post by Enverex on 2007-01-13
Unless it does anything with the kernel (which I doubt) then that should be generic and work on any Linux distro, there's no reason for it not to.

---

### Post by birdseye on 2007-01-15
That may well be true, but I found that it worked with Mandriva out of the box but not with either Dapper or Edgy. 

Is it possible to take bits of the Mandrake kernel and transfer them? If so which bits? And how?

---

### Post by Enverex on 2007-01-15
> **birdseye said:**
> That may well be true, but I found that it worked with Mandriva out of the box but not with either Dapper or Edgy. 

Is it possible to take bits of the Mandrake kernel and transfer them? If so which bits? And how?

This is the silly mentality with Linux. You wouldn't swap from say, Windows XP to Windows 98 because 98 had a built in driver for your whatever would you? You'd just download the driver, which is exactly the same with Linux (just that distros tend to package a lot of them by default which is why some seem to offer it and others don't).

No, you just either recompile the Ubuntu kernel with support for it (which with it being a printer driver I doubt it's anything to do with the kernel anyway, Ubuntu tends to include everything the kernel has to offer anyway).

Anyway, LP says this: [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1500](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1500)
Which means you need the official Canon drivers

Follow these instructions (half-ripped off from another forums post)
Download these:
[http://www.elinuxstop.com/support_center/Downloads/Drivers/Printers/Canon/bjfilter/IP1500/bjfilter-common_2.50-3_i386.deb](http://www.elinuxstop.com/support_center/Downloads/Drivers/Printers/Canon/bjfilter/IP1500/bjfilter-common_2.50-3_i386.deb)
[http://www.elinuxstop.com/support_center/Downloads/Drivers/Printers/Canon/bjfilter/IP1500/bjfilter-pixmaip1500-lprng_2.50-3_i386.deb](http://www.elinuxstop.com/support_center/Downloads/Drivers/Printers/Canon/bjfilter/IP1500/bjfilter-pixmaip1500-lprng_2.50-3_i386.deb)
[http://www.elinuxstop.com/support_center/Downloads/Drivers/Printers/Canon/bjfilter/IP1500/bjfilter-pixmaip1500_2.50-3_i386.deb](http://www.elinuxstop.com/support_center/Downloads/Drivers/Printers/Canon/bjfilter/IP1500/bjfilter-pixmaip1500_2.50-3_i386.deb)
Save all 3 files to the same directory on your pc, then install them by double clicking on them and selecting "Install" when the dialog comes up (install the "common" one first else the others may complain it's missing)
Once that is completed error free restart cups by typing /etc/init.d/cupsys restart.
Finally install it via the printer Control Panel and it should then work fine.

---

### Post by birdseye on 2007-01-16
Thanks for the effort to help. Did everything you said but the last package failed 4 times to install with an error message along the lines of "error processing tmp/bjfilter-pixmaip1500.....deb trying to overwrite usr/lib/libcnbpess214.so.2.0.5 which is also in package libcnbj -2.5

I would read this as saying that a later version of the lib already exists so it auto stopped overwriting and to install as you suggested I should first remove libcnbj -2.5. Is this correct? Any idea of what other dependencies there might be on this lib?

---

### Post by birdseye on 2007-01-16
moved up a bit in the hope of an answer:-?

---

### Post by ljpm on 2007-01-16
Hi Birdseye,

I managed to get my pixma ip 1600 working following 

[HTML]http://www.ubuntuforums.org/showthread.php?t=204853[/HTML]

I had to use the driver for the ip2200, which is listed as a compatible driver on Canon's web page.

Link to ip 1500 driver
[HTML]http://software.canon-europe.com/software/0022415.asp?model=[/HTML]

I don't know if it will work for the 1500 but is worth a try.  

Post if it work or not.

---

### Post by birdseye on 2007-01-16
Any further ideas Everex?

---

### Post by Enverex on 2007-01-16
I'd try downloading the source files from the Canon website and doing it all manually, but I don't have one of their IP printers to go through it all for.

---

### Post by lentiprishtina on 2008-05-13
k;l> **birdseye said:**
> I have read all the earlier posts and tried to follow the routes suggested but still have a printer that wont work. Possibly something like my Sagem modem problem when the key was removing what came with Ubuntu, but in the case of the printer I cant find anything else to remove.

So has anyone got the canon printer working properly under ubuntu. If so, can you put the definitive complete solution to the problem on the board ie in steps that even a newbie like me can follow successfully? Please - so I can finally junk XP. Or try to.

No reflection on the earlier posts by the way - its my lack of linux skills that is the problem!](*,) ](*,) ](*,)

---

