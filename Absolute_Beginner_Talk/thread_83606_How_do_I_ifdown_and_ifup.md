---
title: "How do I ifdown and ifup?"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by ramdisc on 2005-10-29
My interface is not configured all of the sudden.  My connection was working before I shutdown my computer. When I turn it on again, the connection doesn't work anymore.  It is telling me my interface is not configured.  How do I configure it? 

And how do I bring up/down if?  "sudo ifup eth#"?

---

### Post by Manny C on 2005-10-29
Yes, as try
```
 sudo ifup eth0 
```
or 
```
 sudo ifup eth1 
```

---

### Post by darth_vector on 2005-10-29
to configure the interface you will have to edit the file

/etc/networking/interfaces

you will need an entry like this (if using a static IP):

auto eth0
iface eth0 inet static
<tab>address 192.168.0.4
<tab>netmask 255.255.255.0
<tab>broadcast 192.168.0.255
<tab>gateway 192.168.0.1

of like this (if using DHCP):

auto eth0
iface eth0 inet dhcp

hope that helps

---

