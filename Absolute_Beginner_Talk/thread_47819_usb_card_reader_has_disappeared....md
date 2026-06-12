---
title: "usb card reader has disappeared..."
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-10
Since I installed ubuntu I have not been able to get my usb card reader working (it's an internal one that came with the pc). Any tips on this?

---

### Post by Soulfly on 2005-07-10
[QUOTE=gammyhand]Since I installed ubuntu I have not been able to get my usb card reader working (it's an internal one that came with the pc). Any tips on this?[/QUOTE]

1. is it listed in /proc/bus/usb/devices ?  Are your USB Controller there? What chipset do you have? --> $ less /proc/bus/usb/devices
2. Is it mentioned by kernel boot?   --> $ dmesg | less
3. which kernel are you running?  --> $ cat /proc/version
4. what usb modules is loaded?  --> $ lsmod | grep usb
5. Which kernel image package version du you use?  --> $ dpkg -l "linux-image*" | grep "^ii"

---

### Post by gammyhand on 2005-07-10
[QUOTE=Soulfly]1. is it listed in /proc/bus/usb/devices ?  Are your USB Controller there? What chipset do you have? --> $ less /proc/bus/usb/devices
2. Is it mentioned by kernel boot?   --> $ dmesg | less
3. which kernel are you running?  --> $ cat /proc/version
4. what usb modules is loaded?  --> $ lsmod | grep usb
5. Which kernel image package version du you use?  --> $ dpkg -l "linux-image*" | grep "^ii"[/QUOTE]
 I am a bit of a noob :) What would it be listed as in the devices file?

---

