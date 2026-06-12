---
title: "Installing wireless usb?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-07-23
Hi I just got a U.S.Robotics MAXg wireless USB and I was wondering if someone knows how to get it installed on Feisty.
I insert it in a USB port but nothing happens. 
Any ideas please?

---

### Post by weijie90 on 2007-07-23
What is the model of the usb adapter? USR5421?

---

### Post by ROUBOS on 2007-07-23
USR Model 5421

---

### Post by weijie90 on 2007-07-23
You are in luck. This is supported by the bcm43xx driver.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty") should help.

---

### Post by ROUBOS on 2007-07-23
thanks a lot. will look through it.

---

### Post by weijie90 on 2007-07-23
no problem! post here if you need help.

---

### Post by ROUBOS on 2007-07-23
need to have internet in order to download the drivers. So will need lan cable before i setup the wireless

---

### Post by oomisilekootsi on 2007-09-09
Sorry to butt in on this thread but I am having the same problems with the usr5421.  I was able to install bcm43xx-fwcutter and extract the firmware but iwconfig returns no wireless extensions.

---

