---
title: "No wireless in JoliOS 1.2 on ASUS EeePC 1025C"
date: 2012-11-08
forum: Any Other OS
---

### Post by richtathamjr on 2012-11-08
The newest Joli OS is ver. 1.2 and is based on ubuntu 10.04 LTS.  

The ASUS EeePC 1025C is a new netbook, and uses the Atheros AR9485 Wireless Network Adapter chip on a PCI bus on the motherboard.

Problem:  Joli OS works on a _wired_ network connection, but it doesn't see any _wireless_ network.  

[LIST]
[*]any OS based on ubuntu 10.04 LTS does not see any wireless network (eg: ubuntu desktop, lubuntu, easy peasy, Joli OS...)
[*]however, in ubuntu 12.04 LTS & derivatives like lubuntu the wireless works fine.
[*]in 12.04 LTS lshw -c network says the driver=ath9k & driverversion=3.2.0-29-generic-pae.
[/LIST]
So my question is, can I use the information about the driver in 12.04 LTS to make the 10.04 LTS see the ASUS's wireless chip?

---

### Post by varunendra on 2012-11-10
> **richtathamjr said:**
> The newest Joli OS is ver. 1.2 and is based on ubuntu 10.04 LTS.
..
..
So my question is, can I use the information about the driver in 12.04 LTS to make the 10.04 LTS see the ASUS's wireless chip?
Please clarify whether your objective is to make 10.04 work or is it Joli OS.

For 10.04, you may try backported modules : [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)
In short, you'll have to add this line at the end of your /etc/apt/sources.list file -
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse
Once done, do -
```
sudo apt-get update
sudo apt-get dist-upgrade
```

But I don't know if Joli OS supports Ubuntu repositories or not. So can't say how to implement it there.

---

### Post by richtathamjr on 2012-11-10
Desire is to make Joli OS work.  Belief is if I can make 10.04 work I can make Joli OS work also.

---

