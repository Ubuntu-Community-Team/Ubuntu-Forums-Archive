---
title: "Internet connection problem"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Jay-P on 2007-10-04
Well , I am new in Ubuntu linux and I 'd like you to give me your lights! A few weeks ago , I installed Ubuntu 7.04 successfully! Unfortunately , I can't connect to the internet. I have the Sagem fast 800 modem , and I 've taken correctly all the steps that I had to! I've done everything that says here [https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm]("https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm") , and i've searched in ubuntuforums to find something to help me , but nothing worked out. My exact problem is that when I have to unplug/plug the modem the lights turned up instantly without having to wait  , and the same happened when I restarted it! When I enter at the terminal "pppd call ueagle-atm" (without the "") it returns me "Plugin pppoatm.so loaded."
Finally when I gave at the terminal "ifconfig ppp0" it returned me "device not found" !!!
I think that maybe this is the problem , that device cannot be found...!
Can you give little help with this? Thanks!

---

### Post by nowshining on 2007-10-04
download gnome-ppp go into setup and select Detect :) and i figure you'll know how to do the rest. To dialup using the CLI or Terminal Wvdial in /etc/wvdial.conf needs to have the correct info and then typing wvdial will let you dial in, see my thread on dialing up thru the CLI wills ya on that. However there is also kppp for dialing up also, both are found in add/remove.

---

