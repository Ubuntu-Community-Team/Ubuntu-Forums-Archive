---
title: "[SOLVED] no ath0 in gutsy"
date: 2007-11-07
forum: Apple Intel Users
---

### Post by fredrik_human on 2007-11-07
Hi, i installed gutsy on my macBook today and i cannot get ath0 to appear. I had it working under feisty with some minor interrupts due to kernel updates and such. The atheros chipset works great on mac OSX, but in gutsy, no life at all.

iwconfig says:

if lo        no wireless extensions.
eth0      no wireless extensions.

...and if i try ifconfig ath0 up, i get "no such device"

lspci says: 

02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

lsmod says:

Module                  Size  Used by
ath_pci                98336  0 
ath_hal               192720  1 ath_pci
wlan                  206660  1 ath_pci

(after modprobing around a little)

when i try to install the restricted modules for my kernel the system says i already got...

"linux-restricted-modules-2.6.22-14-generic"

..installed

I'm moderately god at linux in general but i don't know what to do here anymore. Maybe someone had this probelm too?

Regards, fredrik

---

### Post by cyberdork33 on 2007-11-07
try compiling the latest version of madwifi.

```
 sudo aptitude install build-essential
wget _http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz_
tar -zxvf madwifi<tab>
cd madwifi<tab>
make
sudo make install

sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
```

---

### Post by fredrik_human on 2007-11-07
sudo modprobe wlan_scan_sta says:

FATAL: Error inserting wlan_scan_sta (/lib/modules/2.6.22-14-generic/net/wlan_scan_sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by cyberdork33 on 2007-11-07
> **fredrik_human said:**
> sudo modprobe wlan_scan_sta says:

FATAL: Error inserting wlan_scan_sta (/lib/modules/2.6.22-14-generic/net/wlan_scan_sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Sorry, need to block the Ubuntu modules too:
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

Probably best to reboot first also, to get everything unloaded

---

### Post by fredrik_human on 2007-11-07
Thank you very, very much, that did it. I'm writing this via wireless. Thanks again.

---

### Post by cyberdork33 on 2007-11-07
please mark thread as solved.

Glad to help.

---

### Post by fredrik_human on 2007-11-08
I would if i could just figure out how ;)

---

### Post by cyberdork33 on 2007-11-08
> **fredrik_human said:**
> I would if i could just figure out how ;)

There is a menu at the top of the thread that says thread tools

---

