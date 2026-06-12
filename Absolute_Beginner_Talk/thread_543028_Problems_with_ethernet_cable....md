---
title: "Problems with ethernet cable..."
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-09-04
...I'm using the same ethernet cable, same modem, same ip address, same gateway, and same netmask to try and connect to the internet in the same house, only on a different computer.

Is this supposed to not work? If so, why? I'm using static ip on both as well.

---

### Post by dwhitney67 on 2007-09-04
Can you please clarify your post?  Do you have 2 PCs that are powered-on at the same time trying to share the same IP address???  That is not a good idea.

---

### Post by ARandomKid on 2007-09-04
Only one is connected to the internet at a time...that just gave me an idea!

With the one that works, it takes a while for it to actually connect. I'll get back to you tomorrow after leaving the cable in the one that doesn't work and doing a network restart.

This COULD work. ;^.^

If not, yes, I have two sharing an IP, but they aren't both connected at once. I'm guessing it would be a bad thing if they were connected at the same time?

In fact, I'm planning to ditch this one (currently connected and functional) for the other one if I can get it working. 3MB more RAM to bring               total up to 126MB, and sound works constantly.

Also, it's functional without requiring an external keyboard/mouse.

OH, and this is what I have...tell me if something needs changed:;;

> 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.***
netmask 255.255.255.0
gateway 192.168.1.1

auto wlan0
iface wlan0 inet dhcp


The wlan0 is left over and doesn't do anything (it's for a wireless card that I couldn't find any linux drivers for), should I take it out?

---

### Post by dwhitney67 on 2007-09-04
Why don't you assign your "new" computer its own IP address, and once you have verified everything works to your liking, then you can remove the "old" computer and then adjust the IP address of the "newer" one.

Also, your router, if you have one, maybe tying the IP address to the MAC address of the NIC in the computer.  Make sure the router, or at least the connection it manages, is released before using the second computer.

---

### Post by nitro_n2o on 2007-09-04
There wire has nothing to do with this. You should examine your pc's NIC... it might be malfunctioning... 
router configurations might be wrong... probably the router gets confused whenever you change the machine MAC address by switching computers and wants more time to build it's routing table (but that shouldn't  be a huge amount of time)... 
I'd say try to run you machines on DHCP for now 
that is comment the static binding and keep it auto 

auto eth0 
iface eth0 inet dhcp 

and see what will happen...

---

### Post by ARandomKid on 2007-09-04
> **nitro_n2o said:**
> There wire has nothing to do with this. You should examine your pc's NIC... it might be malfunctioning... 
router configurations might be wrong... probably the router gets confused whenever you change the machine MAC address by switching computers and wants more time to build it's routing table (but that shouldn't  be a huge amount of time)... 
I'd say try to run you machines on DHCP for now 
that is comment the static binding and keep it auto 

auto eth0 
iface eth0 inet dhcp 

and see what will happen...

How would I go about examining it?

---

### Post by ARandomKid on 2007-09-04
I get no offers when I use DHCP.

It tries to detect...whatever it is...

and then gives out "No DHCPOFFER recieved"

This was my problem before I set it to static.

---

### Post by ARandomKid on 2007-09-04
How exactly would I go about examining the NIC?

---

