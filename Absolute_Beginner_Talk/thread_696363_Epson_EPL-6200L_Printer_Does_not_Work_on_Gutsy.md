---
title: "Epson EPL-6200L Printer Does not Work on Gutsy"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by teacher bai on 2008-02-13
I have an EPSON EPL-6200L printer and am using Gutsy. But I have not been able to get the printer to work.  I looked on the web and searched the forums here, but all I found was really old posts or posts where the problem was not really solved. So is there anybody out there using this printer successfully with Gutsy? If so, what did you do? Thanks!

---

### Post by mikeyphi on 2008-02-14
> **teacher bai said:**
> I have an EPSON EPL-6200L printer and am using Gutsy. But I have not been able to get the printer to work.  I looked on the web and searched the forums here, but all I found was really old posts or posts where the problem was not really solved. So is there anybody out there using this printer successfully with Gutsy? If so, what did you do? Thanks!

A good guide here: [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-6200L](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-6200L)

---

### Post by marlus on 2008-05-11
Hi, I finally managed to get the printer working in 
Hardy, i suspect the same solution might apply on
Gutsy also.

**Download epsoneplijs-0.4.0.tgz;**
[http://sourceforge.net/projects/epsonepl/](http://sourceforge.net/projects/epsonepl/)

**Compile and install:**
tar zxvf  epsoneplijs-0.4.0.tgz
cd epsoneplijs-0.4.0
./configure --prefix=/usr
./make
sudo make install

**Then install the printer using this PPD file:**
[http://www.nemesys.fi/tiedostot/ubuntu/EPL-6200L-Hardy.ppd](http://www.nemesys.fi/tiedostot/ubuntu/EPL-6200L-Hardy.ppd)

There u go!

---

