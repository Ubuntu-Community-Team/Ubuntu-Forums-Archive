---
title: "Wireless using LIVE CD - Broadcom controller"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by HumbleGod on 2006-09-04
Even though I'd consider myself a power Windows user, I'm pretty new to Linux (never installed a Linux OS before), and I'm considering installing Dapper Dan. To see if it's worth installing on another partition, I've been playing around with the Live CD, and would like to see how much of my system I can get working that way BEFORE installing. But to do this, it would help to have internet access while booting with the live CD, which brings me here.....

I live in college housing and connect via wireless internet ONLY--cannot connect via ethernet cable. And I have a Linksys card (WMP54GS) which relies on Broadcom 4318 network controller (according to *lspci -v*, subsys vendor ID 1737, subsys product ID 0042), which according to the resources here will not work with Ubuntu or any other Linux OS. I've been poking around the forums for solutions, but the closest one I found was [this]("http://ubuntuforums.org/showthread.php?t=197102&highlight=wireless+%22live+cd%22"),  which appears to only work with the Live CD boot if you can also connect via ethernet cable (wouldn't be able to download the necessary archive otherwise).

Is there any workaround to this--can I get this card to work WITHOUT installing, using the LIVE CD only?

Thanks!

---

### Post by HumbleGod on 2006-09-04
bump - any input welcome....

---

### Post by HumbleGod on 2006-09-05
bump again....Would really appreciate any input at all...

---

### Post by maelgwynffn on 2006-09-05
To be honest with you, the Live installation is rather limited in what it can do.  You would probably need a program such as NDISWrapper to run the drivers, then use the original driver cd to set it up.  Can you use a thumbdrive or something similar with your windows box so that you can get the tarballed archive (or is it a deb...?) and then install it on this (CD) system?

Just a thought

Maelgwyn

---

