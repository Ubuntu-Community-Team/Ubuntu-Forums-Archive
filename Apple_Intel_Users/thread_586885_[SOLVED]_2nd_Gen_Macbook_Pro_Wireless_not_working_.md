---
title: "[SOLVED] 2nd Gen Macbook Pro Wireless not working after reboot"
date: 2007-10-22
forum: Apple Intel Users
---

### Post by CPUFreak91 on 2007-10-22
Hi, I downloaded and installed the latest madwifi drivers from the madwifi.org svn, compiled and installed them on 64-bit Kubuntu Gutsy 7.10. They worked flawlessly until I rebooted and then modprobe ath_pci gave me this error:
```

FATAL: Error inserting ath_pci (/lib/modules/2.6.22-14-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Dmesg | tail returns:
```

[ 475.683567] ath_pci: Unknown symbol ath_hal_process_noisefloor
 [ 475.683931] ath_pci: disagrees about version of symbol ath_hal_computetxtime
 [ 475.683935] ath_pci: Unknown symbol ath_hal_computetxtime
 [ 475.684272] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
 [ 475.684275] ath_pci: Unknown symbol ath_hal_mhz2ieee
 [ 475.684546] ath_pci: Unknown symbol _ath_hal_detach
 [ 475.687038] ath_pci: disagrees about version of symbol ath_hal_init_channels
 [ 475.687045] ath_pci: Unknown symbol ath_hal_init_channels
 [ 475.687357] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
 [ 475.687361] ath_pci: Unknown symbol ath_hal_getwirelessmodes
```

I have hostapd and madwifi-tools installed could they be causing any problems?

EDIT: Fix:
> **CPUFreak91 said:**
> Hi thanks for the link. I blacklisted the ath_pci module and then added ath_pci in /etc/modules and now it works. If I reboot several times and the wireless disappears I'll be sure to add ath_hal to the list of DISABLED_MODULES in /etc/default/linux-restricted-modules-common.

---

### Post by cyberdork33 on 2007-10-22
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

Make sure you have completed the first section.

---

### Post by CPUFreak91 on 2007-10-22
Hi thanks for the link. I blacklisted the ath_pci module and then added ath_pci in /etc/modules and now it works. If I reboot several times and the wireless disappears I'll be sure to add ath_hal to the list of DISABLED_MODULES in /etc/default/linux-restricted-modules-common.

---

