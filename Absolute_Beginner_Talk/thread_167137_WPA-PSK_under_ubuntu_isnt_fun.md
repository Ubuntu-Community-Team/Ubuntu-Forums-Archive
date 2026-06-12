---
title: "WPA-PSK under ubuntu isnt fun?"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by stanna on 2006-04-27
i have my asus M5000 laptop, which has an intel wireless nic built in. with a fresh install of ubuntu (5.10) everything seems fine and dandy. the network interface shows up. but whats the idiot proof way to get the wireless network to connect to my router with the wpa-psk password? 

it cant be that hard. i also couldnt get windows XP to work until i installed service pack 2, then it would accept the wpa-psk password. is ubuntu similair? do i need a more recent kernel or something for it to connect using the password?

any suggestions would be greatly apreciated.

---

### Post by hw-tph on 2006-04-28
You need to use [wpa_supplicant](https://wiki.ubuntu.com/WPAHowto). My configuration snippets for reference follow.

/etc/wpa_supplicant.conf:```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

network={
        ssid="mynetwork"
        psk=seriouslylonglonglineofcharacters
}
```
The network={} section can be generated using the wpa_passphrase command.


/etc/network/interfaces (only relevant part):```
# Wireless
auto wlan0
iface wlan0 inet dhcp
pre-up /etc/init.d/wpasupplicant start
pre-up sleep 3
post-down /etc/init.d/wpasupplicant stop
```

Works like a charm.


Håkan

---

### Post by joshrobinson on 2006-04-28
wpagui is a nice little tool to have too, to connect/reconnect or whatnot
you can get it in synaptic or apt-get

---

