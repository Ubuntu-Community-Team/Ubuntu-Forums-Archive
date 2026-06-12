---
title: "madwifi drivers.weird, device dissapeared"
date: 2008-04-03
forum: Apple Intel Users
---

### Post by dustynus on 2008-04-03
My madwifi drivers worked fine for the last week until I booted up today, and the ath0 device is gone! ifconfig shows no ath0 of wlan0 created before.

I run:
sudo modprobe -r ath_pci
sudo modprobe ath_pci
ifconfig
> 
iwconfig ath0
ath0      No such device



DMESG:
> stox@stox-laptop:~/Desktop/trunk$ dmesg | grep ath_pci
[   41.552015] ath_pci: 0.9.4
[  354.913674] ath_pci: driver unloaded
[  530.901493] ath_pci: 0.9.4

any ideas?
[  609.076160] ath_pci: driver unloaded
[  653.372493] ath_pci: 0.9.4

This is my dmesg

Disregard. I fixed the problem, a little messing around and a reboot fixed it.

---

### Post by mrsteveman1 on 2008-04-03
Mark the thread solved

---

