---
title: "newbie - network autoconfig"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by mattabs on 2007-07-16
hello all,

i installed 7.04 server edition last night and wasn't hooked up to an internet which messed up my network autoconfig.  now i am unsure of how to go about the autoconfig since i am on the network.  i browsed a few topics and most of them mention "system > admin" etc. in order to do this.  the problem is that i can't use aptitude install to setup x-windows until i'm online.

i'm on my work's network which is through a proxy so my ip is 10.10.x.etc and i'm really not completely sure of how to manually setup the DHCP.

any suggestions are greatly appreciated.

thanks in advance!

---

### Post by mattabs on 2007-07-16
anyone?  :(

---

### Post by Yasumoto on 2007-07-16
I'm hoping this'll help out.

[http://ubuntuforums.org/archive/index.php/t-10078.html](http://ubuntuforums.org/archive/index.php/t-10078.html)

---

### Post by mattabs on 2007-07-16
i tried a few of those commands and got nothing but  SIOCSIFFLAGS errors.

i think i could get it with this but i don't really know what to enter with my office setup.  i have a static ip that is assigned on this computer and the laptop i've installed ubuntu on usually has an ip of 10.1.1.x when i ipconfig in windows.

```
you need to edit /etc/network/interfaces

# This is /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 123.123.123.123
netmask 255.255.255.0
gateway 123.123.123.1
network 123.123.123.0
broadcast 123.123.123.255
# Alternatively:
# iface eth0 inet dhcp
```

---

### Post by mattabs on 2007-07-16
i think the problem is how i've setup my network.

i'm not quite sure where i enter my DNS information.  also i'm unsure about assigning ip address 10.1.1.x .. :confused:

---

### Post by mattabs on 2007-07-16
if anyone can help a noob setup the interfaces / resolv.conf file it would be greatly appreciated.  :D

---

