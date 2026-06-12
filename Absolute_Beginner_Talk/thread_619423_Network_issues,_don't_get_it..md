---
title: "Network issues, don't get it."
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by MaxXL on 2007-11-21
Hi,

I'm completely new to Linux, and just finished installing Ubuntu 7.1.

Installation went flawless as I installed Ubuntu along with WinXP, as dualboot that is. 
I tried to acces the internet, but apparently it couldn't connect to my network. I tried the possible settings such as DHCP and static, but none of them worked.

Now here's the wierd part that I don't get. When I logged into Windows again, it announced that the network cable was unplugged! I traced it down to my router and found out that the fysical port in the router's switch was disabled somehow. There was no connection through that port. 

I thought my router was going dead, but all the other ports on the router worked, that is, untill i started Ubuntu while connected to another port. Now that port went dead too..!  Luckily I was able to get the ports functioning by resetting the router. 

But how is Ubuntu able to stop my routers fysical ports from functioning? 

Thanks in advance!

---

### Post by dstew on 2007-11-21
It may be that during your Ubuntu session, you unintentionally accessed the router setup routines, and changed its settings. This can happen if you connect to 192.168.1.1 or similar address by http or telnet, and then some information is sent. When you manually reset the router, it should work ok again.

If you tell your Ubuntu that the gateway is 192.168.1.1, you might get this behavior. Look at your Network Settings to see if this is the case. Usually, your router will tell your Ubuntu system what the correct gateway is using DHCP, if it is capable of this.  If you have to use Static setup, you have to know the gateway address (and your own IP address) ahead of time.

You can get a display of your current internet configuration by issuing the command```
ifconfig -a
```in a terminal window also.

---

### Post by lespaul_rentals on 2007-11-21
Move up the layers of the OSI Model:

Is your cable connected?
Is it plugged into the correct port?
Is your BIOS set up to properly use your LAN card?
Does your network manager detect a network cable?
Is your DNS/default gateway set up incorrectly?
Have you connected using DHCP?

If you've done all this, it's entirely possible that dual-booting with XP is causing the problem.  Sometimes shutting down XP will bring your network card down with it.  Strange, but true.  That's likely what's happening if you are not able to connect in Ubuntu but it works fine in XP.

---

