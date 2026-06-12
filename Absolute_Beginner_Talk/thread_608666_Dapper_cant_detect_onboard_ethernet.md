---
title: "Dapper cant detect onboard ethernet"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by infurnus on 2007-11-10
This issue has probably been posted before but i cannot find an answer anywhere for my problem.

I have a Asus m2x-mn mobo. The onboard Ethernet is not detected.
this is lspci output i have several unkown items i don't known which ones pertain to the internet i have tried the forcedeth driver and it is still not detected.

```
0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 03ea (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 03e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 03eb (rev a2)
0000:00:01.2 RAM memory: nVidia Corporation: Unknown device 03f5 (rev a2)
0000:00:01.3 Co-processor: nVidia Corporation: Unknown device 03f4 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 03f1 (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 03f2 (rev a2)
0000:00:04.0 PCI bridge: nVidia Corporation: Unknown device 03f3 (rev a1)
0000:00:05.0 0403: nVidia Corporation: Unknown device 03f0 (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 03ec (rev a2)
0000:00:07.0 Bridge: nVidia Corporation: Unknown device 03ef (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 03f6 (rev a2)
0000:00:08.1 IDE interface: nVidia Corporation: Unknown device 03f6 (rev a2)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 03e8 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 03e9 (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 03e9 (rev a2)
0000:00:0d.0 VGA compatible controller: nVidia Corporation: Unknown device 03d0 (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```

/etc/network/interfaces this is the default i believe but if i try ifconfig <interface> all of them (eth0,eth1) etc. will say device not found.
```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider

iface ppp0 inet ppp
provider ppp0

iface eth0 inet dhcp

```

i do use the ppp0 that is a usb modem (my cell phone) 
Wondering if anybody has any input and can help.

---

### Post by infurnus on 2007-11-10
Alright so i went out a bought a new ethernet card because i cannot figure this problem out and now i cant boot into windows :( i just get the splash screen but at least it works in ubuntu. I was reading around on other forums it seems that it also happens with Suse but it works okay with Fedora. Hopefully, somebody will have some input :confused: i am going to have to return this card to get one that works with both OS's.

EDIT: upgraded to gutsy 7.10 now everything works!

---

