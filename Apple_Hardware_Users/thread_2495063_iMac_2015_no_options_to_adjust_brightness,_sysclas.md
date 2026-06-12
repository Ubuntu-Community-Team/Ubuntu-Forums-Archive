---
title: "iMac 2015: no options to adjust brightness, /sys/class/backlight folder is empty"
date: 2024-02-06
forum: Apple Hardware Users
---

### Post by x-achilles-o on 2024-02-06
Dear fellows,

my iMac 16,2 from 2015 with [COLOR=#333333][FONT=&quot]Intel Iris Pro Graphics 6200 has no options to adjust brightness. It is constantly on max, which is really not pleasant to the eyes. Many solutions found on the net involve the /sys/class/backlight folder but in my case this ones empty. I already tried from [this wiki]("https://wiki.ubuntuusers.de/Grafikkarten/Intel/#Helligkeitsprobleme") the kernel options - no change - and the XServer config - creating the 20-intel.conf file also brought no changes.
Is this even solvable? I would love to understand why its not working on my iMac.[/FONT][/COLOR]

---

### Post by x-achilles-o on 2024-02-06
Output of
```
[COLOR=#262626][FONT=&amp]lspci -k | grep -EA3 'VGA|3D|Display'[/FONT][/COLOR]
``` says [HTML]00:02.0 VGA compatible controller: Intel Corporation Iris Pro Graphics 6200 (rev 0a)    DeviceName: Integrated Video Controller    Subsystem: Apple Inc. Iris Pro Graphics 6200    Kernel driver in use: i915[/HTML]
 and [CODE]lsusb | grep "Apple"[CODE] says [HTML]Bus 001 Device 005: ID 05ac:8294 Apple, Inc. Bluetooth USB Host ControllerBus 001 Device 004: ID 05ac:8511 Apple, Inc. FaceTime HD Camera (Built-in)[HTML] so shows no display device.

---

### Post by ictme on 2024-07-25
Solution:

**In a terminal:** ```
sudo nano /etc/default/grub
``` 

**Find a line like:**

 ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor acpi_osi=linux"
```

Change **"acpi_backlight=vendor"** to **"acpi_backlight=video"** and save out the file. Next,

```
sudo update-grub
```

**Then, reboot the computer.** You should be able to adjust the brightness at the login screen and thereafter.

Note: I have a 2015 iMac with the very same graphics card so this should work for you. Good luck!

---

