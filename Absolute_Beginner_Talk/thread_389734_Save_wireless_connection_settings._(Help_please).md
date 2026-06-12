---
title: "Save wireless connection settings. (Help please)"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by camz on 2007-03-21
Hey, I have finally managed to install the driver for a Belkin F5D7050 wireless adapter, and now I need to find a way to save the settings for my connection which I finally managed to set up. The only things I needed to do to get into the Internet were: to add the network name in, request an IP adress (dhclient rausb0), configure the WEP key, and it did everything else as I set it to DHCP. I took the adapter out and I had to do it all over again. How can I get it to save these settings so that whenever the computer is turned off I can easily get it back on just by plugging it in, and so that if it is removed, when I put it back it automatically finds the network and lets me connect.

Thanks,
Cams
(By the way, I'm 13 years old and trying to learn how to use these codes to hopefully make Ubuntu my perfect OS, so if my questions have easy answers, sorry :D)

---

### Post by camz on 2007-03-21
Please help.

---

### Post by devnulljp on 2007-03-21
I'm guessing you're using the Ubuntu networking GUI? Have a look here [http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)
Make sure you save the settings once they're working.

FWIW, your settings are written into a text file  /etc/network/interfaces
Which should look something like this:

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth1
iface eth1 inet dhcp
network xxx.xxx.xxx.xxx
dns-nameservers xxx.xxx.xxx.xxx
default-gateway  xxx.xxx.xxx.xxx
wireless-essid your_essid_id
wireless-key xxxxxxxxxxxxxx

```

You can always save that file somewhere, and copy it back to /etc/network/ then restart your wifi card with 
```

sudo ifdown eth1
sudo ifup eth1
```

I hope I'm understanding your problem OK and that that helps...

---

### Post by camz on 2007-03-21
sorry that hasnt really helped. could someone help. i have configured the connection now i can browse the internet but i need to know how to save all this so that i can simply plug my adapter in and play

---

### Post by camz on 2007-03-21
??

---

### Post by camz on 2007-03-21
need to save the settings

---

### Post by infol on 2007-03-21
hi camz!

as devnulljp pointed out, your network settings are stored in /etc/network/interfaces .

can you post the output of the following command: ```
sudo cat /etc/network/interfaces
```

i use the belkin f5d7051 (which has a different chipset from your network adapter), so my /etc/network/interfaces may look a little different from yours... anyway, mine is as follows:


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid belkin54g
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk [none of your business ;) ]

```

if your interfaces are setup correctly, you can always type the following command after plugging in your wireless adapter:
```
sudo /etc/init.d/networking restart
```

good luck!

---

### Post by camz on 2007-03-21
> root@Cams-Linux:~# sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface rausb0 inet dhcp
wireless-essid simon


there

---

### Post by camz on 2007-03-21
?

---

