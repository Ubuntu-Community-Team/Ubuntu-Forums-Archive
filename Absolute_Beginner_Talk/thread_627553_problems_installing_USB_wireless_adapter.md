---
title: "problems installing USB wireless adapter"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by shavedchimp on 2007-11-30
Hello,

I am trying to install the software needed for a USB wireless adapter from a CD.

I click on the setup.exe icon and get a message saying:

"cannot be opened, no application suitable for automatic installation is available for handling this kind of file"

What gives everybody?

---

### Post by zabien1970 on 2007-11-30
From your post I'm guessing that you are using ubuntu and you're trying to use the cd that came with the wireless card, on the package it came in it should say which operating systems it's compatible with and linux probably isn't listed.
  Give us the specs of your computer and the make and model of the card and someone should be able to help you find a driver.

---

### Post by shavedchimp on 2007-11-30
laptop is the E-system?  G322 series   (EM-G320L1)

processor VIA C7 - M  1.5GHz, 256MB, 20GB

**LogiLink** 802.11g wireless LAN mini USB adapter - model WL0006

I hope this is all the info you asked for?

Thanks in advance

Peter

---

### Post by shavedchimp on 2007-12-03
bump

---

### Post by Mario247 on 2007-12-03
Hi,

I am guessing you have a Windows driver CD.  In that case you need to first install the CD on a Windows machine in order to extract the driver files (eg *.inf) Copy these files over to your Ubuntu box and then use ndiswrapper to install them to work with Ubuntu.  If you do a Google or forum search you will find examples of how to use ndiswrapper.  Be ware that wireless adapters are one of the more troublesome aspects of Linux, so you will need some patience and perseverance.

---

### Post by tuwe on 2007-12-03
from what i found on google, your stick seems to have a realtek rtl8187b chipset. here are some installation instructions:

[http://briancantin.blogspot.com/2007/11/hacking-rtl8187b-on-linux.html](http://briancantin.blogspot.com/2007/11/hacking-rtl8187b-on-linux.html)

ask again if you get stuck.

---

