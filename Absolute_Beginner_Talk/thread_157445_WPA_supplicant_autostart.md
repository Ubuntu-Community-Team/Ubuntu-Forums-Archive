---
title: "WPA supplicant autostart"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Carlito. on 2006-04-09
I wondered how to autostart wpa_supplicant?

my /etc/network/interfaces looks like this

auto wlan0
iface wlan0 inet dhcp
pre-up /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

but i have to use these commands before it works:

sudo wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
sudo dhclient wlan0

So i know there is no config errors.

Anyone who knows what to do??

---

