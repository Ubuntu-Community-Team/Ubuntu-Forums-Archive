---
title: "Struggling with ndiswrapper"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by jmward on 2007-05-15
I'm trying to get my Netgear WG511v2 to work. I have installed ndiswrapper to my laptop. I have the .inf file from my install CD. Wher do I find the ndiswrapper after it in installed from the package manager and how do I use it to install the .inf file?:confused:

---

### Post by AAM on 2007-05-16
jmward, so many questions come to mind, so little information to decide! .... can you give some more information? 

What Ubuntu version?
Have you checked the LiveCD to see there is a ndiswrapper to install?
Do you have internet access by ethernet cable anyway?
The INF file from the CD must be co-existing with the SYS file from the same place when you install. There are lots of guides already to help with ndiswrapper installation.

Your process is firstly to check if WG511v2 is working already. If not and searching says that you have to use ndiswrapper, then retrieve it with synaptic. Look for a good guide and follow it to the letter!

---

### Post by wieman01 on 2007-05-16
From what I know you don't need "ndiswrapper" at all. Just plug the device in and go.

Do a scan and see if it yields any results:
> iwlist scan
If you see wireless networks around you and possibly your own, you are ready to go.

---

