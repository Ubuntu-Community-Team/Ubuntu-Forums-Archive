---
title: "network interfaces take too long on boot"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2005-12-14
Hey, i was wondering if there was a way to skip over the network interfaces part of the boot up... it takes too long for it to come for me and slows down the whole boot... the only way i know how to skip it is to interupt it.. but is there an easier way???


~Lance

---

### Post by yoyoned on 2005-12-14
It probably takes a long time because it's waiting on a DHCP server to assign it an IP address.  If you not on a network, dissable the device.  From the gnome toolbar System>Administration>Networking

Enter your password

Ethernet Conection>Properties

uncheck Enable this connection.

---

### Post by noob_Lance on 2005-12-14
im always in range of a wireless network... im never out of range to one... i usually use my laptop at school or at home... both of which have wireless internet..

---

### Post by carlosqueso on 2005-12-14
It may be set to check your wired network too if you have a wired network card.  Type ```
 sudo gedit /etc/network/interfaces 
``` and comment out the ```
auto eth0
``` line.  That seemed to work for me.

---

### Post by noob_Lance on 2005-12-14
i went into the interfaces file earlier... but didnt want to touch anything incase i screwed it up... but ill try this now

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid MOHAWK-GUEST

auto wlan0

#auto eth0

```

thats my interfaces file now.... MOHAWK-GUEST is the name of the wireless network im on atm..

---

