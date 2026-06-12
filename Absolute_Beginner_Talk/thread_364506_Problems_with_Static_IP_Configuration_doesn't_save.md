---
title: "Problems with Static IP: Configuration doesn't save"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by winsum on 2007-02-18
Dear all,

I'm new to ubuntu and have installed edgy v 6.10 on IBM Thinkpad T43. I've both wireless and ethernet card installed. I want to use eth0 for static ip.

Whenever I reboot or re-login, I have to re-add DNS server and down the wifi0 and ath0, to make internet work

Moreover after 15-20 minutes, the settings automatically reset and internet stops working until I repeat the same process to activate net

I have tried editing the resolv file using **sudo gedit /etc/resolv.conf** and added a single nameserver. but after a while when internet stops working, i recheck and there is default nameserver n host

This is my /etc/resolv.conf file
search lan
nameserver 192.168.1.1

which i want to replace permanently with nameserver xxx.xxx.xxx.xxx

This is my /etc/network/interfaces file
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 193.166.80.111
netmask 255.255.255.0
gateway 193.166.80.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Thanks in advance for the help,
/win

---

### Post by zvacet on 2007-02-19
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
Replace Exec=gksudo /opt/rp-pppoe-3.8/go-gui with Exec=gksudo tkpppoe

---

### Post by winsum on 2007-02-19
I tried, didn't help on reboot. Is there any other way to fix it?
Each time I've to down the wifi0 & ath0, and add DNS server in resolv.conf

---

### Post by gwpritch on 2007-02-19
You want to comment out all the lines in your /etc/networking/interfaces file except those refering to eth0 and lo. Alternatively deactivate your wireless connection in System>Administration>Networking. 

With both eth0 and ath0 (or wifi0) active, you are going to be continually losing your internet connection.

---

