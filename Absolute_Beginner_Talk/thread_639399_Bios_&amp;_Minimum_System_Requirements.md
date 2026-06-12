---
title: "Bios &amp; Minimum System Requirements"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Scocha on 2007-12-13
Having just installed Gutsy on on old Compaq P111 I am having problems with shut down, is this problem because of the very old bios as I get some kind of error message regarding  APIC & ACPI . Is there anywhere I can get minimum system requirements as I would like to install the new lts version when available.

---

### Post by d0nny2600 on 2007-12-13
This is an issue with power management. It may be due to the old bios but I'm not 100% sure. What you can do is:
You need to pass a parameter while booting to enable apm:
If using Grub, when booting you have the option to change the kernel parameters (by pressing "e").
The parameter to add is "apm=on". This allows the kernel to use the APM extensions and will power-down instead of simply giving a "Power down." message.

Installing the latest version of Ubuntu may blindly fix this problem too!

---

### Post by Scocha on 2007-12-13
Getting partial shut down now, get the ubuntu splash screen showing shut down but have to put power off to kill the splash screen, when I restore the power to the wall plug the machine starts up its self.

---

### Post by plucky on 2007-12-13
To add to what **d0nny2600** wrote also add ACPI=off to the kernel line in menu.lst

Also 
```
gksudo gedit /etc/modules
```

add this line to the end of the file
> apm power_off=1

Hope this helps

---

### Post by Scocha on 2007-12-14
Thanks guys it`s looking good at the moment:)

---

