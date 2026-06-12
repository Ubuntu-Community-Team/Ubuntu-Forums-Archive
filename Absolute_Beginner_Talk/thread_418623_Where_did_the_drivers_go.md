---
title: "Where did the drivers go?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by LaidbackBill on 2007-04-22
I decided that if I'm going to get rid of Windows for everyday use I need a few things in ubuntu to work.  So far the internet works fine, external modem, have 3-D graphics working, next on my list is getting the printer to work.  I went over and checked several printer how-to's and pulled out a old HP 540 from the closet, supposedly it should work for my basic printing jobs.  Next went and downloaded the HPLIP 1.7.4 drivers.  I wasn't quite ready to enable printer as I need a ink cartridge for it but thought I'd download drivers and be ready.  Now as I go to find them they are nowhere to be found.  I thought they would be downloaded to the desktop, using Firefox,  but that doesn't seem to be the case.   I tried searching in the file system but nowhere to be found.  Any clues? 
Thanks Bill

---

### Post by gorkur on 2007-04-22
Weird..

What is Firefox's default save folder on your system? Maybe the files went there?

If they've truly and completely disappeared then you could always just redownload the drivers ;)

---

### Post by Patrick K on 2007-04-22
A check in Firefox's preferences main page should tell you where they were downloaded.

---

### Post by Buffalo Soldier on 2007-04-22
Assuming your printer is HP Deskjet 540C. According to this site-> [http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_540C](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_540C) your printer should work perfectly with the openly available linux driver. And from my experience that usually means the printer should work perfectly with Ubuntu and the required driver is already "built-in" Ubuntu.

All that you need to do is plug it in your computer and go to System -> Administration -> Printing.

---

### Post by amohanty on 2007-04-22
I am not sure about fiesty but edgy comes with HP druivers (hplip and hpijs) installed by default. So all you really need to do is to System->Administration->Printing->Add Printer.

HTH
AM

---

### Post by LaidbackBill on 2007-04-22
In firefox's tools-downloads it is supposed to go to desktop.  But it's not there only my only previously downloaded nvidia drivers are there.  Strange, that altough the modem lights were downloading there was no % or speed visible as normal when downloading, plus the fact that hp didn-t give a choice but just started downloading.  Oh well I guess I could try again, what's another hour and a half out of my life.  Thanks

---

### Post by LaidbackBill on 2007-04-22
Yeah I found that out looking in the package manager although these were newer than what is installed initially.  Still wonder where they went.

---

### Post by adam s on 2007-04-22
in a terminal type :

cd /
sudo find . -name hello.world -print


changing hello.world for the driver name. The file name can use wildcards (* or ?) but the file names will be case sensitive.

Adam.

P.S. If you have a firefox download bar installed, it is possible to delete files directly this bar - and this could be the reason you have lost the file.

---

### Post by LaidbackBill on 2007-04-22
Thanks, I'll give it a try.  Tried to get back earlier but couldn't get on, probably feisty questions.
Thanks Bill

---

