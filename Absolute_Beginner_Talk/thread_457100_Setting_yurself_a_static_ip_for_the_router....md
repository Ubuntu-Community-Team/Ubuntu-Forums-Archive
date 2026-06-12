---
title: "Setting yurself a static ip for the router..."
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by ltk5 on 2007-05-28
I don't know id the subject is right;  I think it's wrong written ;)

But I have a tiny problem. Back in windows I went to Network connection and Set up my Static IP;
so I could get my ports forwarded. I don't know how to do this in ubuntu. I've checked several
topics, but I can't seem to find where to set up my DNS address, and my Alternate DNS - if that even matters?

Thanks in advance!

---

### Post by Lucifiel on 2007-05-28
Okay, besides your Time and Date, and Volume Control on the top right menu, there is a small computer icon. 

Left-click on it and choose "Manual configuration".

---

### Post by justifier on 2007-05-28
do 

sudo nano /etc/network/interfaces

or replace nano with your favourite text editor.

and change the data to make it look like, or similar too 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```

ammend IP information etc to your needs

---

### Post by ltk5 on 2007-05-28
> **justifier said:**
> do 

sudo nano /etc/network/interfaces

or replace nano with your favourite text editor.

and change the data to make it look like, or similar too 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```

ammend IP information etc to your needs

hm...

so if I want to forward ports to, ip 192.168.2.66 (for example), I change the IP address and nothing else?

---

### Post by ltk5 on 2007-05-29
bump

---

### Post by lazyart on 2007-05-29
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.66
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
```

---

### Post by ltk5 on 2007-05-29
i can see that but I don't understand what's the difference between gateway and ip adress ?

---

### Post by lazyart on 2007-05-29
IP address is the address of your machine.
The gateway is where all network traffic goes that is not addressed to the local network (ie, the internet).  This would be the address of your router, which almost always ends in .1

If you're talking to another computer in your house or maybe a lan printer the traffic stays inside.  If you are fetching a page such as [www.ubuntuforums.org](www.ubuntuforums.org) the traffic is sent to the router, which then forwards the request to the outside world (really, a series of other routers) to ultimately fufill your request.

---

### Post by lazyart on 2007-05-29
Don't confuse anything i just said with port forwarding.  That is different.

---

