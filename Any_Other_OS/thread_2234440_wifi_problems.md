---
title: "wifi problems"
date: 2014-07-14
forum: Any Other OS
---

### Post by kevin101 on 2014-07-14
Having problems with wifi on dual boot ChrUbuntu.

Results from dmesg | grep ath
```

[    2.926756] Modules linked in: sdhci_pci(+) nm10_gpio sdhci mmc_core tg3(+) ath9k mac80211 ath9k_common ath9k_hw ath cfg80211
[    2.929283]  [<ffffffff8145a412>] system_call_fastpath+0x16/0x1b
[    2.960871] Error: Driver 'ath9k' is already registered, aborting...
[    2.963481] ath9k: No PCI devices found, driver not installed.

```
It says driver registered, but isn't installed.
Tried a system reset and reinstall via chrome:imageburner to no avail. I did, however, notice that ChrUbuntu took up 200MB less space even though I installed it with the same script (odd, shouldn't it install the exact same as the first time with a factory reset? did I accidentally modify some of the hardware?)
Wifi works on Chrome OS just fine.
When I do ifconfig there is no wlan0 or eth0.
I went to additional drivers under settings and it said that the ath9k driver was activated but not in use.

It occured after I tried to install a new custom image (3.4.0) to get a new version of VirtualBox.
Crouton doesn't support VirtualBox as far as I know, and it seems to only have 1 core anyway so I'd have a tough time running VMs even if I got it to work.

EDIT: OK, I tried a third reset, but it also failed. I noticed that at the end of installing ChrUbuntu I got an error about newkern not found and installing the kernel, and when I boot I get error -16 about a probe. However, it says that the Atheros WiFi is working properly in the drivers section.

---

### Post by kevin101 on 2014-07-15
Never mind, I fixed it with a (lol) 4th reinstall with trusty instead of precise. I wonder why the previous ones didn't work.

---

