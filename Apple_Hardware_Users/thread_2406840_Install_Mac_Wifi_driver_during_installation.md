---
title: "Install Mac Wifi driver during installation"
date: 2018-11-26
forum: Apple Hardware Users
---

### Post by chlhardy on 2018-11-26
Hi,

I'm trying to install Lubuntu 16.04 on a newer Mac but it seems to not have the Mac driver.  It can connect during the first part of the install wizard but as soon as I go to the part about installing updates and proprietary drivers it disconnects and no longer sees the network card.  This is an issue because it needs the video driver but cant download it.  

Anyone know how to include the driver along with the install package? 

Also, this is a Macbook Air and does not have a ethernet port.

---

### Post by QIII on 2018-11-26
Moved to Apple Hardware Users for a better fit.

---

### Post by gsahli on 2018-12-01
Can you confirm what macbook air model - especially what wifi card? does it use a broadcom BCM943xxx chipset?
I "think" it uses the Broadcom STA driver.

---

### Post by chlhardy on 2018-12-03
I cant tell because I cant get to any of those details.

Its a A1466 EMC 2632

---

### Post by chlhardy on 2018-12-03
From what I can tell by replacement cards for this model, it is a BCM943

---

### Post by pteryges on 2018-12-05
My experience with my Mac Pro is that unless I have ethernet plugged in, it won't install the Wifi drivers. As they're proprietary, I don't think they're on the install medium. Can you borrow a USB-ethernet dongle for the install?

---

### Post by gsahli on 2018-12-05
I don't have 16.04 installed, but on 18.04 you can use a terminal to install like this:
sudo apt install broadcom-sta-common
(Maybe this is available on the installer CD/DVD/USB media, without internet? Or try the dongle for ethernet)

---

