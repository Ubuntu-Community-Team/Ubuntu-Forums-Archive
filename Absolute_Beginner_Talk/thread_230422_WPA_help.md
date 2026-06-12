---
title: "WPA help"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by IDeus on 2006-08-05
I am trying to get my wireless setup working. I have installed the wpasupplicant and the wpagui packages, I am running a ipw3945 on my laptop.

When I go into Networking and choose the properties of my eth1(wireless card) there is no option to enter a WPA password, only WEP. I have the same issue when tring to do this through knetworkmanager. What am I doing wrong?

---

### Post by bluegroper on 2006-11-16
Same problem here.
Lenovo T60, ipw3945.
wpa_supplicant installed.
WPA missing from all networking tools, radars, etc.
What we doing wrong ?
TIA's

---

### Post by wieman01 on 2006-11-16
Open this file:
> sudo gedit /etc/network/interfaces
Make a safety copy of the contents & replace the contents with this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
Then restart the computer & see if it works now.

---

### Post by Marsolin on 2006-11-16
[Here]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html") is a recent article that might help.

---

