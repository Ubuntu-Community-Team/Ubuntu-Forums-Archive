---
title: "[SOLVED] ath0 suddenly disappeared"
date: 2007-11-16
forum: Apple Intel Users
---

### Post by Wellig on 2007-11-16
When i booted my ubuntu today, the ath0 device was suddenly disapeared. I reinstalled madwifi, but nothing changed...

i really don't know what to do anymore

are there any suggestions?

thanks in advance

Edit: i use a 2nd gen macbook with ubuntu gutsy

---

### Post by tinycamp on 2007-11-16
try:

```

lspci

```


to see the card is still there =)

and try: 

```

lsmod
dmesg 
```

to see if youre loading the right modules

---

### Post by Wellig on 2007-11-17
Hello,

with lspci | grep Atheros, I get this

```
02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

```

the card seems to be still there ;)

after I done sudo  modprobe ath_pci I got with lsmod | grep ath:
```
ath_pci                98208  0 
wlan                  206148  1 ath_pci
ath_hal               192720  1 ath_pci


```

and with dmesg this:
```
[  465.892000] ath_hal: module license 'Proprietary' taints kernel.
[  465.892000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  465.976000] wlan: 0.8.4.2 (0.9.3.3)
[  466.004000] ath_pci: 0.9.4.5 (0.9.3.3)

```

ok, now the question: are these the right modules? (I use madwifi with 2nd gen macbook)

edit:
iwconfig returns this:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by fredrik_human on 2007-11-17
I had the same problem, it tends to occur after kernel-related updates. I suppose you have added ath_hal to the disabled modules in /etc/default/linux-restricted-modules-common? ([http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)).

I got it working again by re-installing madwifi, modprobe wlan_scan_sta and ath_pci and restart my macBook. the ath_hal i had already disabled.

I got some help on madwifi when i installed gutsy. [http://ubuntuforums.org/showthread.php?t=606040](http://ubuntuforums.org/showthread.php?t=606040)

---

### Post by Wellig on 2007-11-18
Thank you, it works again now.

I had to disable the ath_hal. After that I reinstalled madwifi and everything worked well!

---

### Post by dark_harmonics on 2007-11-18
I had this same issue and just had to repeat the sudo make install of the madwifi drivers to get it to work (after a reboot as modeprobe still seems to fail on the device module until i reboot).

---

