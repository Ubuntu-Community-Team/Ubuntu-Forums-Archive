---
title: "Cant connect to internet with Ubuntu"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Catalyst91 on 2007-06-24
So I have Ubuntu running from a live CD on my laptop, and I can't connect to a wireless network.
I went to the site, and Ubuntu supports my card (Dell wireless 1390 WLAN minicard.) I have a Dell Inspiron 1501

Do I need to have Ubuntu installed to my harddrive or something?

Note: When I press the wifi key on the keyboard to turn it on, the wifi logo DOES NOT light up

I am a total Noobie at Ubuntu, so try and explain things in detail.

---

### Post by James.Dedon on 2007-06-24
I had the same problem with my Dell laptop.  First you need to verify the chipset of your wireless card (mine was Broadcom 43xx).  If yours is a Broadcom also you only need to run the firmware cutter tool.  The forums have all kinds of confusing steps to take that didn't matter for me.  I got the package [here ]("http://packages.debian.org/testing/utils/bcm43xx-fwcutter").  You do need to install the OS though for any of it to work.  So, install Ubuntu, run the bcm43xx-fwcutter and you should be up and running.

---

