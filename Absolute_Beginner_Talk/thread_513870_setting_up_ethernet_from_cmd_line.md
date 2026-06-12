---
title: "setting up ethernet from cmd line"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by sjubu on 2007-07-31
Hello all,

I am in a sticky situation.

I am trying to install ubuntu on my machine which has a ati radeon x850 xt video card.  the screen goes black when I start it up; according to these forums I need to "apt-get" the ati fglrx drivers to run x and get into a gui.

however, my ethernet is not working and i cannot download the video drivers without setting up my ethernet.

ifconfig only shows my loopback connection.

if i do "ifconfig eth0" it shows the hardware address of the device, so i assume its recognizing the card, but its not getting set up.

i am connected via cat5 cable to a router which plugs into a cable modem.

any ideas how to set it up so i can get video drivers?

---

### Post by kevinlyfellow on 2007-07-31
You need the lines
```

auto eth0
iface eth0 inet dhcp

```

in /etc/network/interfaces

EDIT: to edit the file
```
sudo nano /etc/network/interfaces
```
:TIDE

Then try 
```
ifup eth0
```
or
```
ifconfig eth0 up
```

---

### Post by tomcheng76 on 2007-07-31
i did something like this
```

ifconfig eth0 192.168.0.2 broadcast 192.168.0.255 netmask 255.255.255.0 up
route add default gw 192.168.0.1

```
which is setting for the client pc of internet sharing  (this is the method if your network is not using DHCP)

---

