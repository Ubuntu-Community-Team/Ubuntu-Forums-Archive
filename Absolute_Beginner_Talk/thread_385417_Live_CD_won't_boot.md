---
title: "Live CD won't boot"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by gspaulding on 2007-03-15
I've downloaded and burned both the cd and dvd iso's for Ubuntu 6.10 i386.  They passed the md5 checksum tests and both will boot into Ubuntu and pass the disk tests on my amd64 laptop.  Neither will boot on my new core 2 duo, WD sata II, Ati x1600pro, LG dvdrw computer.  They load to the menu, but if I choose to start the live cd (or dvd), the Ubuntu logo comes up, the bar starts going back and forth, the then the bar stops moving and computer hangs.  Do I need a special boot code for the core2 duo?

---

### Post by mikewhatever on 2007-03-15
For Core2Duo no, but you may need a few for ATI. I'd suggest trying Alternate Installer.

---

### Post by gspaulding on 2007-03-16
This is an odd one.  After trying 6 different live cd's from 3 distributions, I hooked up a usb  external cd drive and booted to Ubuntu 6.10.  That seems to have been the problem all along.  I don't know why my internal LG DvdRam GSA-H42N would not boot, but it seems it would not read the linux image from cd (or dvd).  Once in Ubuntu, the Gparted editor seems to see my hd just fine, but I haven't tried partitioning.  Any thoughts about why my internal dvd won't allow booting to linux would be appreciated.

Gary

---

