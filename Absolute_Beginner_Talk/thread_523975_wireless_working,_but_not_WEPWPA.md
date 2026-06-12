---
title: "wireless working, but not WEP/WPA"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-08-12
my wireless works, and i've got wep working before on it, but im trying to connect to a different AP and it has stopped working.

I've made sure 100x that the key is correct and the router is set to wep 128. (i have access to router)

my interfaces file is this..

```


auto ra0
iface ra0 inet dhcp 
wireless-essid belkin11
wireless-key <64/128 wep key in hex form here.>

```

doing a networking restart, shows the following
```

Listening on LPF/ra0<my MAC>
Sending on LPF/ra0/<My Mac>
Sending on Socket/fallback
DHCPDiscover on ra0 to 255.255.255.255 port 67 interval 6
DHCPDiscover on ra0 to 255.255.255.255 port 67 interval 9
DHCPDiscover on ra0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received
no working leases in persistent database - sleeping.

```

ive tried using the ascii hex, tried 128 wep, tried wpa (but seem not to have correct driver for wpa, wext didnt want to work. nor did others)

tried using static IP, but to no avail.

running iwlist scan
shows the networking i want to connect to.

running without encryption works fine.

please help!

---

### Post by uclalinux on 2007-08-12
[https://help.ubuntu.com/community/WifiDocs/RalinkRT2500Old](https://help.ubuntu.com/community/WifiDocs/RalinkRT2500Old)

---

### Post by PetePete on 2007-08-13
ta. just what i needed.

---

