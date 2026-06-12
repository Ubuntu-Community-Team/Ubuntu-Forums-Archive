---
title: "LAN problem"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by PaulKolbovich on 2007-06-02
Please, help me!
I need access to Internet by local proxy 172.24.3.125, by I have problem with LAN.
I can't ping proxy and other machines too :-(.
This is my /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.24.3.231
netmask 255.255.0.0
gateway 172.24.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
 
```
If you need something else, please writing.

P.S. I read and tried some solutions, but vain.:'(

P.P.S. Sorry about my English.

---

### Post by kernel tom on 2007-06-02
those first couple of lines should be...

auto eth0
iface eth0 inet static
        address 172.24.3.231
        netmask 255.255.255.0
        network 172.24.3.0
        broadcast 172.24.3.255
        gateway 172.24.3.1


then run this in the terminal to restart ur network

sudo /etc/init.d/networking restart

---

### Post by Swab on 2007-06-02
> **kernel tom said:**
> those first couple of lines should be...

auto eth0
iface eth0 inet static
        address 172.24.3.231
        netmask 255.255.255.0
        network 172.24.3.0
        broadcast 172.24.3.255
        gateway 172.24.3.1


then run this in the terminal to restart ur network

sudo /etc/init.d/networking restart

Where did you get that mask from?

---

### Post by PaulKolbovich on 2007-06-02
Thanks to all! :-)
I don't remember what I did, but after reboot network is working. Cool!

[SIZE="5"]Problem is SOLVED![/SIZE]

---

