---
title: "Network problem (NIC) (linux noob)"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by HotRodKcsF on 2007-06-18
Hi, im trying to get the linux box on my network.
I have tried several distros but all say that my nic is not active.

Setup:
Win2003 Domain, with Win2003 DHCP.
Linux box:
P4 2,4Ghz, 2GB ram, 80GB PATA HD, Realtek RTL8169S GB eth or Marvell onboard, tried both.

I can't  seem to get an IP from the DHCP, tried with the routers DHCP, disabling the Win2k3 DHCP, same problem.
This is the same in all linux distro's I have tried. I know for a fact that the ethernet cards are working (had win2k3 on the box earlier).

I have searched for a answer for this problem but without any luck.

I have now installed the box with Ubuntu Server 7.04.
Error when trying to get info from DHCP.

Some help would be great. Thanx.

---

### Post by Crafty Kisses on 2007-06-18
> **HotRodKcsF said:**
> Hi, im trying to get the linux box on my network.
I have tried several distros but all say that my nic is not active.

Setup:
Win2003 Domain, with Win2003 DHCP.
Linux box:
P4 2,4Ghz, 2GB ram, 80GB PATA HD, Realtek RTL8169S GB eth or Marvell onboard, tried both.

I can't  seem to get an IP from the DHCP, tried with the routers DHCP, disabling the Win2k3 DHCP, same problem.
This is the same in all linux distro's I have tried. I know for a fact that the ethernet cards are working (had win2k3 on the box earlier).

I have searched for a answer for this problem but without any luck.

I have now installed the box with Ubuntu Server 7.04.
Error when trying to get info from DHCP.

Some help would be great. Thanx.

Sounds like you're running a Wireless connection, if that's the case you'll probably have to use "NDISWrapper".

This thread may be useful to you:
[http://ubuntuforums.org/showthread.php?p=40016](http://ubuntuforums.org/showthread.php?p=40016)

---

### Post by reset3x on 2007-06-18
Those are both onboard nics.... I have the same ones.... Do you have both nics configured to use dhcp? Also you may want to enable one at a time.. ie: eth0... then make sure you have the cable plugged in the right port... Just a thought...

---

