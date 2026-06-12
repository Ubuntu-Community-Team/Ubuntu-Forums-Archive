---
title: "Help - Installing Scanner Drivers"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by steve-shinn on 2007-07-08
Please help out a newbie.....

I have attached an Epson perfection 4490 photo scanner to my PC when I type lsusb into terminal I get :-
Bus 003 Device 003: ID 04b8:0119 Seiko Epson Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:08ad Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 

However when I launch Xsane it does not detect the scanner .... only the webcam

I have subsequently downloaded some linux drivers from Espon which currently reside on my desktop :-
epson31411eu.zip

Can someone please advise me how to install the drivers ??

Thks in advance SteveS

---

### Post by steve-shinn on 2007-07-08
bump

---

### Post by phidia on 2007-07-08
The best thing to do IMO is to check out the how to at the sane website [http://www.sane-project.org/docs.html](http://www.sane-project.org/docs.html) or the hardware docs here.

Having said that have you opened a terminal and tried > sane-find-scanner
refer to this [http://www.sane-project.org/man/sane-find-scanner.1.html](http://www.sane-project.org/man/sane-find-scanner.1.html)

---

### Post by steve-shinn on 2007-07-09
> **phidia said:**
> The best thing to do IMO is to check out the how to at the sane website [http://www.sane-project.org/docs.html](http://www.sane-project.org/docs.html)

Tried that link and can find no reference to the Epson perfection 4490 photo

---

### Post by steve-shinn on 2007-07-09
bump

---

### Post by linuxwizard on 2007-07-09
I have looked every where I can think of. Their is no listing of that scanner working on Linux. To new of a unit or just untested yet. 

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

### Post by Rui Pais on 2007-07-09
> **steve-shinn said:**
> Please help out a newbie.....

I have attached an Epson perfection 4490 photo scanner to my PC when I type lsusb into terminal I get :-
**Bus 003 Device 003: ID _04b8_:_0119_ ** Seiko Epson Corp.
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:08ad Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 

However when I launch Xsane it does not detect the scanner .... only the webcam

I have subsequently downloaded some linux drivers from Espon which currently reside on my desktop :-
epson31411eu.zip

Can someone please advise me how to install the drivers ??

Thks in advance SteveS
Hi,
try first:
```
gksudo gedit  /etc/sane.d/epson.conf
```

and add a line:
```
usb 0x04b8 0x0119
```

```
gksudo gedit /etc/udev/rules.d/45-libsane.rules
```
and add a line:
```
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0119", MODE="664", GROUP="scanner"
```

good luck

---

### Post by hackeron on 2008-03-06
bump

---

### Post by luca.mg on 2008-03-09
[http://ubuntuforums.org/showthread.php?t=705566&highlight=4490](http://ubuntuforums.org/showthread.php?t=705566&highlight=4490) 

I understand this is a solution only for 32 systems HTH luca

---

