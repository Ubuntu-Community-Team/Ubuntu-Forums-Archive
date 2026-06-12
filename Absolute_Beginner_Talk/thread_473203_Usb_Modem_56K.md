---
title: "Usb Modem 56K"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by raphenry on 2007-06-13
Okay i have looked for days and cant find what i am looking for. I am brand new to linux, installed Ubuntu last weekend, but havent been able to find out how to get my usb 56k modem to work. I downloaded and ran the scan tool, it tells me somethng, but i cant find what i am to do to make the modem work. I cant find anywhere that can and one place told me to use an acm, but i cant even do simple things in the now GUI screen.  I am very familar with dos and upto XP windows. i even tried the ppp programs and they cant locate my modem.

Here is my info....
CPU=i686,(AMD)  Ubuntu 7.04 
Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007
 scanModem update of:  2007_June_06


ALSAversion 1.0.13
  idVendor           0x054c Sony Corp.
  idProduct          0x0243 
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc00e M-BJ69 Optical Wheel Mouse
Bus 001 Device 005: ID 0483:7554 SGS Thomson Microelectronics 56k SoftModem
  idVendor           0x0483 SGS Thomson Microelectronics
  idProduct          0x7554 56k SoftModem

Please, how do i make it work??
Step by step please.....

thanks

---

### Post by oilchangeguy on 2007-06-13
your best bet for an external modem is to use a serial modem.

---

### Post by Shazaam on 2007-06-13
It looks like the chipset for your modem was sold to Conexant. Did you try the SmartLink driver?
Worst comes to worst go to linuxant.com to get the drivers. They have .deb files so it should be easy to install.

[http://www.smlink.com/smlink.asp](http://www.smlink.com/smlink.asp)
[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

---

### Post by raphenry on 2007-06-14
found more info and found that i need to install slmdm.  Did that but now what.  still cant get connected.  learned a lot though, now have rpm installed, know what sudo is for, and have found the manual.  help is a good thing to type when lost.](*,)

---

### Post by foxmulder881 on 2007-06-14
Before I moved to broadband, I had a USB external dial up modem. From my experience, I gave up trying to get it to work. I stuck with Windows until I got broadband. The day it was connected was the day I migrated to Ubuntu.

Seriously, if you're going to stick with dial up, stick with Windows. Otherwise, you'll be ripping your hair out trying to get it to work.

---

### Post by nutz on 2007-06-14
56k is overkill anyway. Who really needs a connection that fast...

---

### Post by foxmulder881 on 2007-06-14
> **nutz said:**
> 56k is overkill anyway. Who really needs a connection that fast...

I hope you're kidding... :(

---

### Post by nutz on 2007-06-15
> **foxmulder881 said:**
> I hope you're kidding... :(
;)

---

### Post by cebobbitt on 2007-06-15
> **nutz said:**
> ;)
I have been using Ubuntu for about a year now and I am on dial up also. I never did get the software modem to work so I bought a hardware modem and it was detected immediately. So the best advice, I think, is like oilchangeguy said, get a serial port hardware modem. Your modem will be on ttyS0. I got mine at Best Buy for something like 60 bucks and it has worked flawlessly. That's my 2 cents worth

---

