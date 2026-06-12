---
title: "Wireless Connection"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by clemkonan on 2007-01-16
Can anyone help me save my project?

I want to use a Ralink rt2500 driver and a Linksys WUSB54G adapter but I do not have the savvy to follow the the bits of information I have been receiving on how to download, install and set up the driver.

I would appreciate some guidance on :

1) How to download and install the driver
2) How to complete the configuration steps

I would prefer not to use Ndiswrapper unless there is no other hope and or if this is by far the ideal solution. 

Sincere thanks

---

### Post by arochester on 2007-01-16
See "WifiDocs/Driver/RalinkRT2500" at [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

---

### Post by clemkonan on 2007-01-16
Does this article hold true for Edgy? 

I am asked to enter the following:
gksudo gedit /etc/network/interfaces 

I get the response:
Gn UI -Warning ** : While connecting to session manager: Authentication Rejected : None of the authentication protocols specified are supported and host based authentication failed.

then I get :
auto lo
iface lo inet loopback

auto et0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp

auto eth2 
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp

---

