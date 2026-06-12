---
title: "Help with Broadcom BCM4318...detected, drivers installed, but will not let me configu"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by iamsm151th on 2007-01-07
Hello, I am on a laptop with a Broadcom BCM4318. I have tried several methods to get my wireless working...the one I got the furthest on was

[http://www.ubuntuforums.org/showthread.php?t=265284&highlight=broadcom+4318+ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=265284&highlight=broadcom+4318+ndiswrapper)

I got to step 4 of this part but when I type in the code and try to add the final step of 4
(Simply add a # at the beginning of the line that assigns a persistent name to your wireless network card.)

I see no network card in the file that has been opened up...

If anyone can help me with this method or one of their own please do. Im new to linux as of yesterday afternoon and need all the assistance I can get.

---

### Post by teaker1s on 2007-01-07
good guide here
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")


[COLOR="Red"]sudo modprobe ndiswrapper[/COLOR]

[COLOR="Red"]sudo ndiswrapper -l[/COLOR]

should see something like this if you have ndiswrapper is installed correctly

installed drivers:
bcmwl5          driver installed, hardware (14E4:4324) present (alternate driver: bcm43xx)

---

