---
title: "Enabling Broadcom 43xx?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by elzzirf on 2007-11-25
Hi all, I just downloaded Edubuntu 7.10 couple of days back. When I use the restricted drivers manager and try to enable the firmware for Broadcom 43xx chipset, I get an error message saying bcm43xx-fwcutter is not enabled. How do I enable bcm43xx-fwcutter?

Also, I used Synaptic to download ndiswrapper but I can't find windows wireless drivers.

This is my first time using Linux and would really appreciate any help.

Thanks in advance!

---

### Post by Yellowdog428 on 2007-11-25
You need the Firmware for the card.  There should be an option to download it if you have a wired connection.  Or if you have the disk laying around from either a old Windows install or when you bought the card.

The reason it is not provided is because broadcom holds rights to it....

If the Resticted drivers dont work well try this
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6)

or this
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

Both are for festy, but should still work

Cheers

---

### Post by elzzirf on 2007-11-25
Thank you, Yellowdog. Really appreciate your help. Finally able to log on to the Internet on Ubuntu! THANKS AGAIN! The links you gave were really helpful even though I took awhile to understand them. (:

---

### Post by KhaaL on 2007-11-25
good it worked out for you :) you should try ndiswrapper if you're not content with the performance of fwcutter (it's very flaky for me and dies sporadically). The windows wlan driver should be in your manufactorers homepage.

---

