---
title: "UBUNTU 16.04.03 LTS WIFI connection working but No Internet (i-Mac )"
date: 2017-11-05
forum: Apple Hardware Users
---

### Post by fabiobaj on 2017-11-05
Hi I have the same problem (Ubuntu 16.04 on MAC) 
THe Wired connection works but the WIFI dose not get to Internet

here is the link at the WIFI-Info Script execution log   [http://paste.ubuntu.com/25898728/](http://paste.ubuntu.com/25898728/)
Ping either does not work or works randomly and very slowly



thanks for helping me

---

### Post by Hadaka on 2017-11-05
This may help you connect but you have many issues that need correcting.
from a working wired connection please copy and paste every line..one line at a time..
```
sudo apt-get update
[COLOR=#000000]sudo apt-get remove --purge bcmwl-kernel-source
[/COLOR][COLOR=#000000]sudo rm /etc/modprobe.d/blacklist-bcm43.conf
[/COLOR][COLOR=#000000]sudo apt-get install firmware-b43-installer
[/COLOR][COLOR=#000000]sudo modprobe b43[/COLOR]
```
remove wired connection and ANY usb's, boot and test wireless.
then run a new wireless report for pastebin and post the results to your
own thread.
thanks.

---

### Post by fabiobaj on 2017-11-06
Thanks a log Hadaka
I saw later the instructions at the beginning of the forum, and removed and installed the correct Driver, as indicated in your reply.
Now wifi Internet connection works fine

I will re run the wireless report and post in separate tread
thanks

---

### Post by fabiobaj on 2017-11-06
Installed UBUNTU on iMac Intel® Core™2 Duo CPU E8235 @ 2.80GHz × 2 

Wired connection to Internet Router was working fine
WIFI connection to the same router seems to work,  but no Internet
ping 8.8.8.8 either says no Host or randomly works, loosing most of the packets

I solved it by following the instructions at the beginning of the Forum (related to Broadcom Drivers)

 sudo apt-get update
 sudo apt-get purge bcmwl-kernel-source
 sudo apt-get install  firmware-b43-installer


as requested here I repost the result of the wifi-report-script  after the change

[http://paste.ubuntu.com/25902119/](http://paste.ubuntu.com/25902119/)

---

