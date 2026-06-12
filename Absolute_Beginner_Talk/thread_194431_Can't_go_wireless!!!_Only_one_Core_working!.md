---
title: "Can't go wireless!!! Only one Core working!"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by elraval on 2006-06-11
I'm a real newbie... and i just installed 6.06Desktop as dual boot on my ACER Aspire 5672 (Intel Core Duo T2300 1,66GHz, 512MB DDR2, ATI X1400). 

I installed Ubuntu at home, were i don't have neither wired or wireless internet access...

When i got to school where there's Wireless LAN everywhere and it always went fine in XP home, i don't know how to make it work!

Besides that it seems that only one of the cores is working... I read something about SMP, but i have no idea on what it is???

I apreciate any help i can get! Thanks

Diogo Pereira... 
from Portugal to the World Cup Final... (I hope)

---

### Post by jpkotta on 2006-06-11
For the wireless there are two options. One is Network Manager, which attempts to make wireless work like it does on Windows (i.e. automatically connecting to networks).  There is a page in the wiki about it.  The other is to do things manually, which is what I prefer, because Network Manager never quite worked for me.  I use network-admin (the network configurator that you get from the menu).  You can define different profiles, like home, school, wired, etc.  

SMP means symmetric multi-processor.  I think that the default kernel in Dapper has SMP enabled.  You can make sure by looking at /proc/cpuinfo, if it lists more than one CPU, you have it enabled.

---

### Post by Aurelias on 2006-06-11
Wireless stuff tends to be annoying until you get it set up right, I've found.  I use KDE and I've heard good things about kwirelessmanager to set up wireless access, but have never used it.  What you should do first is get connected using an ethernet cable and get familiar with how internet connections work in ubuntu.  Look up the man pages for ifup, ifdown, ifconfig, and iwconfig by opening up a console and typing "man ifup", then reading it and hitting 'q' when you're done.  Repeat for the rest.

Once you're used to what these do and more or less how they work, you'll find that you can connect to a wireless interface by doing something like this:
```
ifdown eth0 (assuming this is your wired interface; can't have more than one on at a time, usually.  you can enter "ifconfig -a" to list all the ethernet devices you have and get info about them)
ifup eth1 (turns on the wireless device)
iwconfig eth1 essid NAME (where NAME is the essid of the access point)
iwconfig eth1 channel 6 (or whatever channel the AP is using)

```
This *should* work.  But, it's error-prone and makes for a lot of tedious work to get wireless access.  To get around this, you could use network-manager, which tries to do it all automatically, but I could never get it working right.

Also, it's worth noting that there's probably a far easier way to manually connect to a wireless AP than what I detailed above.  I don't use gnome, so I don't know what kind of utilities ubuntu includes for this purpose.

Sorry for the long-winded, super-detailed post, but I think it's worthwhile to understand how wireless works before you let a program do it for you.  Wireless access tends to have problems, so if you know how it works, you can understand what's going wrong and fix it later on.
Regards,
Aurelias

---

### Post by jpkotta on 2006-06-12
[QUOTE=Aurelias]
 Wireless access tends to have problems, so if you know how it works, you can understand what's going wrong and fix it later on.
[/QUOTE]

Indeed, good advice.  Here's a trick I use when the connection is really bad:
```
sudo iwconfig eth1 rate 1M
```
It sets the rate to 1 Mbit/s (which is actually much faster than the actual data rate, because of all the error correcting bits and other overhead).  It is almost paradoxical, but on a bad connection, slowing down results in more throughput.  The optimal rate is a function of the the hardware (both yours and the AP) and the channel, so try different rates to see which is best.

---

