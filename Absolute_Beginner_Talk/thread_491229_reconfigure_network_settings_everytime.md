---
title: "reconfigure network settings everytime??"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by fireflyfx on 2007-07-03
Hi newbie using xubuntu 7.04 on an old laptop. I've managed to sort out the wifi internet connection with no problems initially. 

However, each time I reboot I need to reconfigure the network settings in order to get back on the net (actually just unticking and reticking the box next to wireless connection in network settings does the trick)  Surely this cant be right though? When i was using a wired connection this never happened. Any ideas?

---

### Post by Erdaron on 2007-07-03
Does your /etc/network/interfaces file include the line to automatically bring up your wireless adapter?

Something like:

```
auto ra1
```

---

### Post by fireflyfx on 2007-07-03
Thanks for the reply. The file looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid 
	wireless-key1 s: 
	wireless-key s: 



auto eth0

(I've blanked out the ssid and keys). Using a 3com pcmcia card and xubuntu 7.04. All i want is to be able to start up my pc and open the web browser straight away. Surely configuring network settings is a one time thing?

---

