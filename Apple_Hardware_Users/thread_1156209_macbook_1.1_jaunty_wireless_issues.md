---
title: "macbook 1.1 jaunty wireless issues"
date: 2009-05-11
forum: Apple Hardware Users
---

### Post by firemoth on 2009-05-11
Hey guys,

In Intrepid, everything was working correctly with the MadWifi (ath_pci) driver.  In Jaunty, using ath5k I got frequent errors like this (especially after sleeping, but sometimes just randomly:
```

May 11 00:25:27 MacBook kernel: [ 8846.331445] ath5k phy0: noise floor calibration timeout (2437MHz)
May 11 00:25:38 MacBook kernel: [ 8856.786371] ath5k phy0: gain calibration timeout (2412MHz)
May 11 00:25:38 MacBook kernel: [ 8856.786379] ath5k phy0: can't reset hardware (-11)
May 11 00:25:38 MacBook kernel: [ 8856.786384] phy0: failed to set freq to 2412 MHz for scan
May 11 00:25:38 MacBook kernel: [ 8857.132614] ath5k phy0: gain calibration timeout (2417MHz)
May 11 00:25:38 MacBook kernel: [ 8857.132621] ath5k phy0: can't reset hardware (-11)
May 11 00:25:38 MacBook kernel: [ 8857.132625] phy0: failed to set freq to 2417 MHz for scan
May 11 00:25:38 MacBook kernel: [ 8857.152792] ath5k phy0: noise floor calibration failed (2417MHz)
May 11 00:25:39 MacBook kernel: [ 8857.478762] ath5k phy0: gain calibration timeout (2422MHz)
May 11 00:25:39 MacBook kernel: [ 8857.478769] ath5k phy0: can't reset hardware (-11)
May 11 00:25:39 MacBook kernel: [ 8857.478774] phy0: failed to set freq to 2422 MHz for scan
May 11 00:25:39 MacBook kernel: [ 8857.825231] ath5k phy0: gain calibration timeout (2427MHz)
May 11 00:25:39 MacBook kernel: [ 8857.825238] ath5k phy0: can't reset hardware (-11)
May 11 00:25:39 MacBook kernel: [ 8857.825243] phy0: failed to set freq to 2427 MHz for scan
May 11 00:25:39 MacBook kernel: [ 8858.171443] phy0: failed to set freq to 2432 MHz for scan
May 11 00:25:40 MacBook kernel: [ 8858.517643] phy0: failed to set freq to 2437 MHz for scan
May 11 00:25:40 MacBook kernel: [ 8858.863785] phy0: failed to set freq to 2442 MHz for scan
May 11 00:25:40 MacBook kernel: [ 8859.209951] phy0: failed to set freq to 2447 MHz for scan
May 11 00:25:41 MacBook kernel: [ 8859.556632] phy0: failed to set freq to 2452 MHz for scan
May 11 00:25:41 MacBook kernel: [ 8859.902808] phy0: failed to set freq to 2457 MHz for scan
May 11 00:25:41 MacBook kernel: [ 8860.248991] phy0: failed to set freq to 2462 MHz for scan
May 11 00:25:42 MacBook kernel: [ 8860.595187] phy0: failed to set freq to 2467 MHz for scan
May 11 00:25:42 MacBook kernel: [ 8860.941369] phy0: failed to set freq to 2472 MHz for scan
May 11 00:25:42 MacBook kernel: [ 8861.287586] phy0: failed to set freq to 2484 MHz for scan
May 11 00:25:43 MacBook kernel: [ 8861.634954] phy0: failed to set freq to 5180 MHz for scan
May 11 00:25:43 MacBook kernel: [ 8861.981885] __ratelimit: 22 callbacks suppressed
May 11 00:25:43 MacBook kernel: [ 8861.981890] ath5k phy0: gain calibration timeout (5185MHz)
May 11 00:25:43 MacBook kernel: [ 8861.981896] ath5k phy0: can't reset hardware (-11)
May 11 00:25:43 MacBook kernel: [ 8861.981900] phy0: failed to set freq to 5185 MHz for scan
May 11 00:25:43 MacBook kernel: [ 8862.328785] ath5k phy0: gain calibration timeout (5190MHz)
May 11 00:25:43 MacBook kernel: [ 8862.328790] ath5k phy0: can't reset hardware (-11)
```forcing me to SHUT-DOWN the machine to get it to work again.  Also, the connection was VERY unreliable (often disconnecting and reconnecting, and very slow).

Ok, so I enabled the MadWifi driver, which works much better.  The problem is after I suspend and resume, I have to unload and reload the driver manually otherwise it tries to connect, fails and asks me for the password (which is stored already) and proceeds to time out again...in WPA_Supplicant log I get this:
```

Authentication with 00:1d:7e:61:b9:1d timed out.
```As soon as I sudo modprobe -r ath_pci and sudo modprobe ath_pci, it connects perfectly.

I'm willing to use either ath5k or ath_pci as long as I can get them to WORK!!  Help me please.

---

### Post by firemoth on 2009-05-12
Alright well I got it working...

I added "ath_pci" under modules in /etc/default/acpi-support and also created a new file in /etc/pm/config.d/ (I named it 01ath_pci) with one line "SUSPEND_MODULES="ath_pci"" and now it suspends and resumes wireless perfectly.  This was the same hack I used in Intrepid Ibex to get ath_pci to resume properly.  ath5k seems like a lost cause, although I believe the errors I was getting is a known bug with ath5k.

MadWifi connects faster and runs faster...I understand the whole proprietary HAL thing, but until ath5k is working without major issues like this, they should use MadWifi by default (IMO).

---

### Post by anando on 2009-05-12
Thanks for reporting this. Are you able to use a WPA2 Enterprise access point ? The ath5k drivers dont work with WPA2 Enterprise.

> **firemoth said:**
> Alright well I got it working...

I added "ath_pci" under modules in /etc/default/acpi-support and also created a new file in /etc/pm/config.d/ (I named it 01ath_pci) with one line "SUSPEND_MODULES="ath_pci"" and now it suspends and resumes wireless perfectly.  This was the same hack I used in Intrepid Ibex to get ath_pci to resume properly.  ath5k seems like a lost cause, although I believe the errors I was getting is a known bug with ath5k.

MadWifi connects faster and runs faster...I understand the whole proprietary HAL thing, but until ath5k is working without major issues like this, they should use MadWifi by default (IMO).

---

