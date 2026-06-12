---
title: "Macbook Pro Santa Rosa - Undefined symbols in Ath_pci"
date: 2008-08-01
forum: Apple Hardware Users
---

### Post by almahtar on 2008-08-01
Heya all - I'm running Hardy quite happily on my new Macbook Pro 3.1 (Santa Rosa).  Everything was working quite nicely until I installed the Virtualbox kernel modules so I could run a Windows XP virtual machine.

After a reboot, my wireless didn't work.  After attempting to manually run modprobe ath_pci it said it failed and to check dmesg.

dmesg | grep ath gives me the following:
```

[   48.435993] ath_hal: module license 'Proprietary' taints kernel.
[   48.459330] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   48.750604] ath_pci: disagrees about version of symbol _ath_hal_attach
[   48.750608] ath_pci: Unknown symbol _ath_hal_attach
[   48.750696] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[   48.750697] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   48.751037] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[   48.751038] ath_pci: Unknown symbol ath_hal_computetxtime
[   48.751263] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[   48.751264] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   48.751418] ath_pci: Unknown symbol _ath_hal_detach
[   48.751921] ath_pci: Unknown symbol ath_hal_print_decoded_register
[   48.752412] ath_pci: disagrees about version of symbol ath_hal_init_channels
[   48.752414] ath_pci: Unknown symbol ath_hal_init_channels
[   48.752626] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[   48.752627] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[  108.824858] ath_pci: disagrees about version of symbol _ath_hal_attach
[  108.824872] ath_pci: Unknown symbol _ath_hal_attach
[  108.825164] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  108.825169] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  108.826475] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  108.826484] ath_pci: Unknown symbol ath_hal_computetxtime
[  108.827293] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  108.827299] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  108.827787] ath_pci: Unknown symbol _ath_hal_detach
[  108.829588] ath_pci: Unknown symbol ath_hal_print_decoded_register
[  108.831313] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  108.831319] ath_pci: Unknown symbol ath_hal_init_channels
[  108.832058] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  108.832065] ath_pci: Unknown symbol ath_hal_getwirelessmodes


```

I tried uninstalling the virtualbox modules, reinstalling the madwifi drivers, recompiling the madwifi drivers, all to no avail so far.  I still get the undefined symbols.  Between when the drivers worked and when they didn't I haven't upgraded my kernel - I just installed the vbox kernel modules through synaptic.

---

### Post by flaggh on 2008-08-01
are you recompiling/installing the same exact madwifi drivers you used before?  With my computer (MacBook 2,1) the latest drivers aren't working and I'm forced to use an older one.  I do need to recompile them every so often depending on what I install.

I would suggest retrying the madwifi installation:
```
sudo modprobe -r ath_pci
cd /path/to/madwifi/source
make clean
make
sudo make install
sudo modprobe ath_pci

```
if that doesn't work, shutdown the computer and then boot it up again rather than just reboot.

---

### Post by jav20a on 2009-05-05
I found the solution, just uninstall the restricted drivers package...

---

