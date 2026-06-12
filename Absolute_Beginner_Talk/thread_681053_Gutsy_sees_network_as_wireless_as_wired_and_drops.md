---
title: "Gutsy sees network as wireless as wired and drops"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by robsonthejob on 2008-01-28
Hi - eventually got my adaptec awan 8020 (prism chipset) wireless working on gutsy. The network manager saw it as a wired not wireless connection and when it did work it dropped out every few minutes. De-installed the gnome network manager stuff (sudo apt-get remove network-manager-gnome network-manager
 )and it works now when the machine starts but still drops every few minutes. anyone any ideas.

This is the contents of my interfaces file. Confused of liverpool here !!

Thanks

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

iface wlan0 inet static
address 192.168.0.15
netmask 255.255.255.0
gateway 192.168.0.1
wireless-key 6fa7bdnnnnnnnnnnnnnnnnnnn
wireless-essid ROBSHOUSE

auto wlan0

LSMOD output:-----
usbcore               138632  7 prism2_usb,ndiswrapper,xpad,usbhid,ehci_hcd,uhci_hcd

---

### Post by spiderbatdad on 2008-01-29
how did you generate the interface? You may want to remove it and begin again with network-manager. Why a static address...sever?

---

### Post by robsonthejob on 2008-01-29
> **spiderbatdad said:**
> how did you generate the interface? You may want to remove it and begin again with network-manager. Why a static address...sever?

part network manager part me looking at different posts , what looks wrong ??

---

### Post by spiderbatdad on 2008-01-29
not sure anything looks wrong. I've seen some say essid needs to be in quotes, but that is usually in reference to connecting, not getting dropped. Sometimes NM is finicky, and it seems to takes several tries before it sticks. I was wondering why you chose to configure static addresses...not that it's any concern of mine. Just making sure you had considered dynamic.

---

### Post by spiderbatdad on 2008-01-29
i believe gw is optional you might try removing it from each interface.
```
#
# See the interfaces(5) manpage for information on what options are 
# available.
######################################################################

# We always want the loopback interface.
#
# auto lo
# iface lo inet loopback

# An example ethernet card setup: (broadcast and gateway are optional)
#
# auto eth0
# iface eth0 inet static
#     address 192.168.0.42
#     network 192.168.0.0
#     netmask 255.255.255.0
#     broadcast 192.168.0.255
#     gateway 192.168.0.1
```

---

### Post by robsonthejob on 2008-02-01
> **spiderbatdad said:**
> i believe gw is optional you might try removing it from each interface.
```
#
# See the interfaces(5) manpage for information on what options are 
# available.
######################################################################

# We always want the loopback interface.
#
# auto lo
# iface lo inet loopback

# An example ethernet card setup: (broadcast and gateway are optional)
#
# auto eth0
# iface eth0 inet static
#     address 192.168.0.42
#     network 192.168.0.0
#     netmask 255.255.255.0
#     broadcast 192.168.0.255
#     gateway 192.168.0.1
```

De-installed network manager tried WICD no success reverted back no change.
Config file now like this but wireless still drops every few minutes

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1


auto wlan0
iface wlan0 inet static
address 192.168.0.15
netmask 255.255.255.0
gateway 192.168.0.1
wireless-key 6fa7bd0d305axxxxxxxxxxxxxxx
wireless-essid ROBSHOUSE


Given up got cable running over the floor all the time now. Pith really everything else works so well
:confused:

---

