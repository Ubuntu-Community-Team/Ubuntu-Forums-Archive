---
title: "Notebook Asus N750JV-T4069H: Power Adapter And Battery State"
date: 2013-11-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by aljosa2 on 2013-11-25
Hi all,
happy with 7 months Linux experience on old HP desktop, few days ago I deleted Windows from my brand new notebook Asus N750JV-T4069H (Intel® Core™ i7-4700HQ; Bit 64; Nvidia GeForce GT750M) and installed Xubuntu 13.10. I'm not sure but it seems to me that my problem is Xubuntu bug. If this is the case, I would be very grateful if someone can communicate the problem to the development team 'cause I get lost inside the more than complicated bug reporting procedure: 


- When power adapter is plugged in, connection is not recognized and battery state is wrong

---

### Post by Toz on 2013-11-25
See [https://wiki.debian.org/InstallingDebianOn/Asus/N750JV/Jessie]("https://wiki.debian.org/InstallingDebianOn/Asus/N750JV/Jessie") - perhaps the **acpi=** kernel parameter will fix this issue as well.

---

### Post by aljosa2 on 2013-11-25
ORIGINAL /etc/default/grub


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


Thanks for reply :)
I've tried 4 different scenarios, but nothing changes: 


GRUB_CMDLINE_LINUX="acpi= nolapic. 'acpi='"
GRUB_CMDLINE_LINUX="'acpi='"
GRUB_CMDLINE_LINUX=acpi= nolapic. 'acpi='
GRUB_CMDLINE_LINUX='acpi='

---

### Post by aljosa2 on 2013-11-26
I have reinstalled Xubuntu once again. Don't know if it is of any importance, but in my computer ther'e no a single trace of Windows 8 (uefi/boot).
During installation, everything ok with power adapter connection and battery state. After installation, problem appears again- 
Nothing changes with different acpi= kernel parameter.

---

### Post by Toz on 2013-11-26
In that case can you try a few other parameters:

First try:
```
GRUB_CMDLINE_LINUX="acpi_osi="
```

Then try:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```

In both cases, ensure you run:
```
sudo udpate-grub
```
...afterwards and reboot. And on each reboot, first check to see if things are working better then post back the contents of your dmesg log file in the following manner:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by aljosa2 on 2013-11-28
Hi, 
thank you once again for your assistance.
"acpi=" and "acpi_osi=\"!Windows 2012\"" are useless, but with "acpi_osi=" we're almost there :)

If I unplug the power supply, correct battery notification appears. When I connect again power adapter, notification says battery is charging but adapter not connected. 

**GRUB_CMDLINE_LINUX="acpi_osi="**

> pastebinit /var/log/dmesg

[http://paste.ubuntu.com/6488928/](http://paste.ubuntu.com/6488928/)


> cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.11.0-13-generic.efi.signed root=UUID=737be188-c475-4521-a764-c484a80d404c ro acpi_osi= quiet splash vt.handoff=7


**NOT OK:**
Power Adapter shows not connected
No keyboard backlightng
FN (F3) Decreases keyboard backlighting
FN (F4) Increases keyboard backlighting
FN (F9) Enables or disables the touchpad

**OK:**
Battery shows 100%
FN (F1) Puts the Notebook PC into Sleep mode
FN (F2) Turns Airplane mode on or off
FN (F5) Decreases display brightness
FN (F6) Increases display brightness
FN (F7) Turns the display panel off
FN (F8) Activates the second screen
FN (F10) Turns the speaker on or off
FN (F11) Turns the speaker volume down
FN (F12) Turns the speaker volume up

---

