---
title: "Adding a  printer  via socket://address"
date: 2007-05-28
forum: Apple PPC Users
---

### Post by louv on 2007-05-28
I have struggled and succeeded to install U_6.06.1 on a G4-PPCdual 450. It is up and running as I am typing this.  I have several EPSON network printers which are accessable by direct communicaitions on other computer platforms. I use the EPSON® Multiprotocol Ethernet Interface Board to print on the network. I have used the System:Administration:Printing menu to Add a printer. I have the PPD driver properly selected Epson Stylus Color  900  etc. The test page however just sits in the queue. In the CUPS documentation indicates the EPSON network card calls for using the "socket://address" connection type as opposed to IPP:\\  or LPD: 
How do I configure this or other?

---

### Post by jrusso2 on 2007-05-28
Print to ip address then socket like this  appsocket/jetdirect 198.168.1.15:9100

---

### Post by louv on 2007-05-30
Thanks for the reply .  No luck yet. The  port must not be 9100 or a different issue. Does one of the background  processes need to be stopped and restarted for changes to take effect?
From a terminal:

The CUPS error log file at /var/log/cups/error_log has a repeating error of:

E [30/May/2007:22:26:32 -0500] cupsdAuthorize: Local authentication certificate not found!
E [30/May/2007:22:26:35 -0500] cupsdAuthorize: Local authentication certificate not found!

I'll keep looking to understand this error. Just too new to Linux to make quick progress.

louv

---

### Post by jrusso2 on 2007-05-31
Never seen that before.  Not sure what the problem is.  Possible some kind of bug?

---

### Post by volkswagner on 2007-06-01
Do you see your printer at web interface?

[http://localhost:631/](http://localhost:631/)

my network printer works best when i enter the dhcp address of the machine in the location field 
ie     no port number

---

### Post by louv on 2007-06-05
I did not see either network printer under 6.06. I have since moved to 7.04 and the printer is auto recognized. Thanks all for your suggestions but I have left 6.06 behind for 7.04

---

