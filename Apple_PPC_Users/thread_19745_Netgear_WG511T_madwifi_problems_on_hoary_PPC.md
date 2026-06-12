---
title: "Netgear WG511T madwifi problems on hoary PPC"
date: 2005-03-13
forum: Apple PPC Users
---

### Post by Entity on 2005-03-13
Since the Aiport Extreme is not supported yet, I'm now trying to use my Netgear WG511T pcmcia wifi card with madwifi but I get the following errors when plugging the card in :

$ dmesg

cs: pcmcia_socket0: voltage interrogation timed out.
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.12.14 (AR5210, AR5211, AR5212, REGOPS_FUNC)
wlan: 0.8.4.5 (EXPERIMENTAL)
ath_rate_onoe: 1.0
ath_pci: 0.9.4.12 (EXPERIMENTAL)
PCI: Enabling device 0001:11:00.0 (0000 -> 0002)
ath%d: unable to attach hardware; HAL status 13

$ sudo ifup ath0
Password:

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device ath0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; No such device.
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
ath0: ERROR while getting interface flags: No such device
Failed to bring up ath0.

$ iwconfig ath0

ath0      No such device


Any suggestions?
Many thanks for your time and help.

---

### Post by Entity on 2005-05-15
Note that the problem was on the preview version and I don't get that error anymore on the official hoary release.

---

