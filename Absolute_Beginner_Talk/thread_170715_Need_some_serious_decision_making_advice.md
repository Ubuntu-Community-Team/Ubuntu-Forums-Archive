---
title: "Need some serious decision making advice"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by a_0000 on 2006-05-05
For the past 7 days I have been testing with Ubuntu 6.06 beta-1, 6.06 beta-2 and 5.10 DVD to see which one to make my permanent OS (to replace XP). 

I downloaded all 3 and live-CD's/DVD and tested them out, installed a few of them (one at a time) and yesterday I settled with ubuntu 6.06 beta-2 because it detected my usb wireless adaptor (3com zd1211) out-of-the-box. however for me 6.06 seemed really buggy, crashed a lot and by the afternoon after just a reboot would cause it to freeze and the mouse would no longer move.

So i decided to go with 5.10 Breezy because it's stable, with the hard task of having to compile/install the wireless drivers (my situation is such that this computer can be onlines ONLY through wireless no cables).

The problem is: I can't install the drivers :( i've tried and tried but i cant understand some of the instructions so staying with Breezy seems undesirable and now going back to 6.06 seems stupid due to the unstability... what should i do? what can anybody advise me for my situation??

---

### Post by az on 2006-05-05
[QUOTE=a_0000]detected my usb wireless adaptor (3com zd1211) out-of-the-box. however for me 6.06 seemed really buggy, crashed a lot and by the afternoon after just a reboot would cause it to freeze and the mouse would no longer move.[/QUOTE]

Probably because of the zd1211.  Dapper should not lock up like that.  The driver is getting some love, but it is still young.  Don't count on it.  Try blacklisting the zd1211 driver and using ndiswrapper or wait another six months or so.

---

### Post by a_0000 on 2006-05-05
[QUOTE=azz]Probably because of the zd1211.  Dapper should not lock up like that.  The driver is getting some love, but it is still young.  Don't count on it.  Try blacklisting the zd1211 driver and using ndiswrapper or wait another six months or so.[/QUOTE]

I started to get Dapper problems after installing VMWare 5.5 and restarting the computer while it was hanging during a XP install inside a VM. So... I guess I will be going BACK to Dapper lol, i'll re-install that tonight because otherwise I can't get online without my wireless card hence I have no choice really :S

---

### Post by az on 2006-05-05
If you still have your Dapper install, completely remove vmware to see if that's the problem.

VMware wireless networking can be a big source of instability.  Vmware anything, actually.

---

