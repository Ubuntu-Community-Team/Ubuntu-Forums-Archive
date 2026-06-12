---
title: "[SOLVED] network connection"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by dougleduck on 2007-03-31
The other day I tried to connect to my uni wirless network and fiddled with my settings. I thought I'd changed everything back but now i can't connect to my BThomehub with my *wired * connection

My connection worked previously with the default settings...so perhaps if someone could provide me with these or how to get them back it would work.

Also while trying to change settings something went wrong with the network program, and it wont even open. I now get the following message.

jody@jody-laptop:~$ gksu network-admin

(network-admin:5618): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(network-admin:5618): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `PangoFcFont'


P.S. i use xubuntu, and connect to the bt home hub with a wired PCMCIA card. The network and card itself work as I'm currently using the internet on windows.

---

### Post by chili555 on 2007-03-31
May I please see your whole, entire, unedited (except for any encrytion codes) /etc/network/interfaces file? You may need to boot into the fail-safe mode and, after logging in, issue the command:```
cat /etc/network/interfaces
``` Write it down and post back.

---

### Post by dougleduck on 2007-03-31
sure...here it is. unedited acccept for the password.

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid  
wireless-key s:xxxxxxxx

auto wlan0

auto eth1

---

### Post by chili555 on 2007-03-31
I would add, just above the eth0 stuff:```
auto eth0
```Also, if you have wired available, I would temporarily comment out:```
auto wlan0
```Unless you have a whole pile of wireless cards, you can safely delete ath0 and eth1. My own interfaces file only has lo, eth0, without auto and eth1, my wireless connection, with auto.

Does your ethernet respond when you do:```
sudo dhclient eth0
```> GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
I get this, too, but it runs just fine, so I'd ignore it.

---

### Post by dougleduck on 2007-03-31
i happily right this from xubuntu. Thanks for your help!

---

