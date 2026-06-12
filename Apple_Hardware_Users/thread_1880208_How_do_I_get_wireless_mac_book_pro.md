---
title: "How do I get wireless mac book pro?"
date: 2011-11-13
forum: Apple Hardware Users
---

### Post by Ceiber Boy on 2011-11-13
Started new job (2011). Was offered a laptop or mac book pro (Lion OS), I asked for a mac (thinking it was the best option), I'm not sure now! I want to duel boot, so popped in a live disk but can't get the networking card working, wireless or wired!

I've read around on the www but can't seam to get a definitive way/answer to how to get it working.

I'm desperate to get ubuntu 10.04 LTS installed. How do I get the networking card working?

May thanks

---

### Post by Rankun on 2011-11-13
The MacBook Pro's WiFi should work with the Broadcom STA Wireless driver, at least mine does. After you boot Ubuntu, start the Additional Drivers application and it should be an option there. Activate it, reboot, and the WiFi should work.

---

### Post by cuppido on 2011-11-13
Take a look at:
[https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless)

---

### Post by bradleypariah on 2011-11-14
I had to have my Ethernet cable plugged in *prior* to booting off the Live CD.  In other words, I hooked up my CAT-5 while the MacBook was still powered off.

Ubuntu 11.10 understood the wired connection of my MacBook Pro 7.1 out-of-the-box.  It did not, however, understand my Broadcom wireless device.

Even after choosing to "Install Additional Drivers" after my full install, the installation of the drivers failed.  The error log was seriously thousands of lines long.  TL;DR!!! :P

I went to the Ubuntu Software Center, installed Synaptic Package Manager, then searched Synaptic for "Broadcom".  It came back with four hits.  I chose to install them all.  After that, wireless worked like a charm.

---

