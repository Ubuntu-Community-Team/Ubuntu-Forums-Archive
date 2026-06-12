---
title: "Looking for drivers for Canon BJC4200"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by sandman55 on 2007-03-09
Hi I've just installed Ubuntu 6.06 Dapper Drake and I'm trying to get my canon printer BJC4200 to work I think I have found a PPD file for a BJC600 (which should work) but I get to a dead end when trying to find a CUPS driver I would appreciate any help finding a driver and any advice installing it. Also would I find it easier if I downloaded and installed ubuntu 6.10 Thanks in advance any help would be appreciated.

---

### Post by oilchangeguy on 2007-03-09
i'm running 6.06, and just opened the add a printer wizard, clicked on cannon and scrolled down the list, and there it was. bjc4200, try again.

---

### Post by sandman55 on 2007-03-09
Thanks I hope its as easy as that I'll give it a go.

---

### Post by sandman55 on 2007-03-10
Hi I just tried it and it looked like it was going to work it found the ppd driver that I downloaded yesterday and it showed the new driver but when I tried to print the print prompt comes up I click ok then nothing happens.

I think I need to find the CUPS driver

---

### Post by ramjet_1953 on 2007-03-10
Follow this link and see if it helps

[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-4200](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-4200)

Regards,
Roger 8)

---

### Post by sandman55 on 2007-03-10
Thanks for that I've already been around that site quite a bit and the only link that looks promising for the BJC600 that is supposed to have the same drivers leads to a dead end with 
"Not Found
The requested URL /doc/gnu/7.05/Devices.htm was not found on this server."
I joined their forum but I'm not able to login, so I'll give them a bit of time and in the mean time I'll keep looking.

---

### Post by sandman55 on 2007-03-11
I seem to be coming to a dead end Ive found the pps driver but not the cups driver I'm begining to wonder if anyone has managed to get this printer to run on Linux.:(

---

### Post by Erlander on 2007-03-11
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

worked well for me.

Rob

---

### Post by sandman55 on 2007-03-11
Thanks Erlander last night I downloaded Turboprint drivers and now I'm struggling to get them to work. If I'm not successful I'll try your suggestion.

---

### Post by sandman55 on 2007-03-12
Just reporting back that I've got my printer going with Turbo print the free version in medium quality print which I think is good enough. With high quality print you get their logo on the page till you buy it.

Thank you to the guys that offered help =D> 

For anyone with the same printer I downloaded it [_**HERE**_](http://www.turboprint.info/) and clicked on the link "Download and try the FreeEdition now!" where I filled in their form including my printer BJC4200 hit download then you have the choice of two download sites at "DEB package for Debian / Ubuntu" 
I double clicked on the Zipped package and then I double clicked on TurboPrint-setup here I went wrong I just accepted what it said (I should have read it correctly and clicked add ) I tried all sorts to get it going but to make the story short I went back and double clicked TurboPrint-setup deleted the printer I had there and clicked add and folowed the prompt see item 7 [_**HERE**_](http://www.turboprint.info/)selected my model. Note item 10 where the picture has "/dev/lp0" that shows you have a parrallel port selected when you finished double click on "TurboPrint-Config" and set up your cartridge mine is black  and quality set at medium (no TurboPrint Logo) when you have finished here you can click apply then go to tool box and try printing a test page

---

