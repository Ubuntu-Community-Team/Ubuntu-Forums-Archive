---
title: "ndiswrapper error messages"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by wwk2310 on 2007-04-06
with the command sudo ndiswrapper -i I tried to install a driver for a Netgear usb wifi receiver.
When the command was given an error message came up saying "couldn't install netwpn11.inf at usr/sbin/ndiswrapper-1.8 line 144"
When I do a ndiswrapper -l the result is "netwpn11 invalid driver"
Could I have the ndiswrapper set up wrong?
This is very frustrating.
Any comment would be appreciated.

Wendell 
cross posted to usenet Ubuntu forum

---

### Post by mi_were on 2007-04-06
> **wwk2310 said:**
> with the command sudo ndiswrapper -i I tried to install a driver for a Netgear usb wifi receiver.
When the command was given an error message came up saying "couldn't install netwpn11.inf at usr/sbin/ndiswrapper-1.8 line 144"
When I do a ndiswrapper -l the result is "netwpn11 invalid driver"
Could I have the ndiswrapper set up wrong?
This is very frustrating.
Any comment would be appreciated.

Wendell 
cross posted to usenet Ubuntu forum

it looks like you need to start over.

Uninstall the netwpn11 driver using

sudo ndiswrapper -e "name of driver"

then post the type of usb wifi receiver your using then we can take it from there.

---

