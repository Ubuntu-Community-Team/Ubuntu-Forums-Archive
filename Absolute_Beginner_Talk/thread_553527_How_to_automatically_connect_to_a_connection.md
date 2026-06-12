---
title: "How to automatically connect to a connection?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Roxlo on 2007-09-17
Each time I log onto ubuntu I have to click the connection icon and click wired connection. It doesn't automatically connect. How can I make it automatically connect to my wired connection? Thanks

---

### Post by cubeist on 2007-09-18
try clicking on the connection icon and selecting "Manual Configuration" and under wired select automatic (DHCP)... also make sure the checkbox beside wired is checked...

---

### Post by saisho on 2007-09-18
happened to me also. Not sure if this is a bug or just some problem with certain network cards not initialising early enough during boot. 
Any way, the way to workaround the problem is to configure a STATIC IP (Under "Wired Connection", click on Manual Configuration, then Properties  and set a static IP  - gateway, mask etc.). (Don't remember if you need to reboot now or not). Then configure it back to DHCP and voila - it connects automatically on start-up (also the Wired Connection option is gone). 
HTH,

---

### Post by Roxlo on 2007-09-24
Didn't work. :(

---

### Post by Hospadar on 2007-09-24
do you have a wireless connection as well?  if so you might try disabling that.  If this is a desktop that only connects to one network, you could try setting up a static connection, and then uninstalling "network-manager" and "network-manager-gnome"  this will make it so ubuntu doesn't try to auto-configure your network and just uses a static connection setup.

---

