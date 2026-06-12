---
title: "USB Wifi Driver Install Help"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2006-04-08
Hello

I was previously trying to connect my Ubuntu box to my network via a crossover cable to my XP box which is then connected to a wireless router. A day and a half later and I am no closer to getting online. 

So I am moving on, I have a usb 802.11g NIC that I would like to use in the Ubuntu box to connect to my wireless router. Of course I immediately hit a brick wall with the driver](*,) . The wireless NIC is a ZD1211, which seems to be a generic chipset used in various wifi brands. 

Here is a link to Linux install instructions
[http://zd1211.ath.cx/](http://zd1211.ath.cx/)

I can untar the file usung the GUI but after that I am lost with the "make" and "makefile" stuff. I am sure that once I get the driver installed I can figure out the config stuff. Any suggestions?

---

### Post by Sef on 2006-04-10
To compile u need build-essential, have you downloaded it?

sudo apt-get update

sudo apt-get install build-essential

---

