---
title: "Get ip address"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by IDeus on 2006-08-06
I can see my notebook connected to my router in my router status window. But I cannot get firefox to go online and I cannot ping anywhere?? Seems like I may need an ipdaddress I am thinking? I am using wpa_supplicant. Here are my settings

wpasupplicant file :

ENABLED=1
OPTIONS="-w"


wpa_supplicant.conf file:

network={
ssid="MyNetworkSSID"
proto=WPA
key_mgmt=WPA-PSK
psk=my loooooooooooooooooooooooooon hex number
}

interfaces file:

auto eth1
iface eth1 inet dhcp
pre-up /etc/init.d/wpasupplicant start
pre-up sleep 5


why can't i get online???

---

### Post by eXisor on 2006-08-06
Try do the wireless setup without any form of security, and when that works, get the security going.

---

