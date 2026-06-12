---
title: "Activating network on startup"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by originald on 2007-07-07
Hi,

Does anyone know how I can make my wireless network connection activate on startup ? At the moment I have to goto System > Administration > Networking and then select the adapter for the wireless networking and uncheck and recheck it for it re-activate. Once I do this the network works fine.

Using Ubuntu 6.10

originalD

---

### Post by mikeyphi on 2007-07-07
Strange to say - I had the same problem, initially, with 6.10 - it corrected itself after a couple of weeks or there was an update? However the problem didn't arise when I moved over to 7.4 - which I suggest you consider!!

---

### Post by originald on 2007-07-07
OK,

I upgraded to the newest version of ubuntu but the problem still exists.

Anyone else have any suggestions ?

OriginalD

---

### Post by annda on 2007-07-07
it can be a problem with your card (i had a similar problem with my father's d-link, but an asus worked right after boot on his computer).

or it could be configuration... can you post your /etc/network/interfaces file?

---

### Post by originald on 2007-07-07
Hi,

Here is a copy of my /etc/network/interfaces files

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ath0 inet dhcp
wpa-driver madwifi
wpa-ssid linksys
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk *************************************************** < i blanked this for this post
wireless-essid linksys

---

### Post by annda on 2007-07-07
try adding
auto ath0

before
iface ath0............

reboot. i hope it helps. otherwise i have no idea except a script that will automatically shut down and restart your connection on startup.

---

### Post by originald on 2007-07-07
I just tried this and restarted but this time the network icon showed connected (normally it would have the disconnected icon) but the network was not working. Went into System > Adminstration > Network and my wired adapter was shown as activated as was my wireless, so disabled my wired adapter and disabled and re-enabled my wireless adapter and is working again. Checked my /etc/network/interfaces file and auto ath0 line I added has been removed. So still the same

---

### Post by annda on 2007-07-07
so this is a madwifi issue - it has taken control of your configuration. you have to keep on looking there. i can't help you, sorry.

---

### Post by originald on 2007-07-07
I think I am just going to do this from a script at startup.

One thing I'm unsure of though is how I can make the script use ifup / ifdown without asking for password as these commands require me to place the sudo command in front of them but then this required a password entering. How do I achieve this ?

Thanks

---

### Post by annda on 2007-07-07
i'm VERY bad at bash scripting, so it may not work and it is an ugly way to do things, but at least it won't hurt your system.

```
gksudo gedit /usr/bin/dirty_wireless_reset
```

put there:

> #!/bin/bash
ifdown ath0 && ifup ath0

then

```
sudo chmod +x /usr/bin/dirty_wireless_reset
```

and add the script to your startup sessions: system>preferences>sessions

unless it gets executed before madwifi takes over, it should work.

---

