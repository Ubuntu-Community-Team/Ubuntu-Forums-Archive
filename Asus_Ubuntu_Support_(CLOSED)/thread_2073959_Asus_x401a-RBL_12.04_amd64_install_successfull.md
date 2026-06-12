---
title: "Asus x401a-RBL 12.04 amd64 install successfull"
date: 2012-10-20
forum: Asus Ubuntu Support (CLOSED)
---

### Post by kickingvegas on 2012-10-20
Installed 12.04 amd64 on $300 ASUS x401a-RBL notebook from Best Buy. 

Issues:
[LIST]
[*]Default WiFi driver is unreliable with repeated disconnects. Fix was to download, build and install Ralink RT5390 Wireless 802.11n driver from Ralink [website (choose the RT539x PCIe driver source)]("http://www.ralinktech.com/en/04_support/support.php?sn=501").
[*]Install to co-exist with Win7 is not optimal. Cannot boot Win7 from grub, but can if I press Esc key upon powerup, bypassing grub and selecting Win7 to boot. Too many sharp edges in Ubuntu install workflow for EFI-naive users like myself who want to have both Win7 and Ubuntu available. Also concerned what will happen to boot sequence when I try to install Win8.
[*]Touchpad is unusable when typing. Fn-f9 to toggle touchpad operation thankfully works.
[*]Brightness keys (f5, f6) do not work. xbacklight utility in coordination with custom keyboard shortcuts (ctrl-f5, ctrl-f6) used as workaround.
[/LIST]

Observations:
[LIST]
[*]Battery life is about 4.5 hours.
[*]Drag operation in touchpad without clicking is done with a touch-up/touch-down/drag event sequence. 
[/LIST]

---

### Post by tgrossner on 2012-10-24
Does two-finger scolling work with this clickpad?

---

### Post by prostolinux on 2013-01-18
> **tgrossner said:**
> Does two-finger scolling work with this clickpad?

Look [http://prostolinux.ru/kak-ustanovit-wifi-drayver/](http://prostolinux.ru/kak-ustanovit-wifi-drayver/)

---

