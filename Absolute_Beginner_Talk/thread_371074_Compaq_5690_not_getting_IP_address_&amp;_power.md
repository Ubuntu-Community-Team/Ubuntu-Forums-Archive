---
title: "Compaq 5690 not getting IP address &amp; power"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by tamundson7 on 2007-02-26
I just installed 6.10 on a gateway and it is doing great.  I also installed it on a Compaq Presario 5690 and it seems two work but two things are not working.  It shows the enet card, built on the motherboard, but it won't pick up an ip address.  The Gateway picks it up just fine.  Also when I try and shut down the Compaq it goes through the shut down sequence then restarts.


Any ideas?

---

### Post by Quintin Riis on 2007-02-26
I need the following information: 

lspci 
lspc -n 
ifconfig 
/etc/network/interfaces

---

### Post by johnlh on 2007-02-26
Sounds somewhat like my issue.  I see only MAC (unique identifier for  network card), no ip or client name.
[http://www.ubuntuforums.org/showthread.php?t=369673](http://www.ubuntuforums.org/showthread.php?t=369673)
  I don't if it'll be a problem when I try to network everything in the house through the router, it just seemed odd.

---

### Post by tamundson7 on 2007-02-27
> **Quintin Riis said:**
> I need the following information: 

Where is the following? Can't seem to find it.

lspci 
lspc -n 
ifconfig 


Here is this...:) 
/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by Quintin Riis on 2007-03-07
Those are commands to type at a terminal.

---

