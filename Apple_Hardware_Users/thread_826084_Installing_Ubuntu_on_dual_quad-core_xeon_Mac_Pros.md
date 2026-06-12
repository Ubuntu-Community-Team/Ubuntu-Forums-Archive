---
title: "Installing Ubuntu on dual quad-core xeon Mac Pros?"
date: 2008-06-11
forum: Apple Hardware Users
---

### Post by david_finlayson on 2008-06-11
I've got two quad-core xeon workstations that I am considering converting full time to 64-bit Linux. It doesn't look like Apple hardware is turn-key yet. Any advise/HOWTO's etc? Note these are not MacBooks, I don't care about laptop-specific issues.

These are number-crunching machines and I've had about enough of Apple OS X. The main issue is package management and dependency resolution. I use a lot of standard Unix tools that are easy to keep up-to-date in Ubuntu and a PITA in OS X.

---

### Post by cyberdork33 on 2008-06-11
First thing to note is that, since Macs have EFI, Linux doesn't quite work like we would like yet, but, you can just pop in the Ubuntu CD, format and install. Dual-booting, or keeping an install of OSX on an external drive is recommended so that you will be able to perform Firmware updates in the future. You will also likely get long delays at bootup because the EFI system searches for EFI executables.

WiFi is a pain, like all the other Macs out there... Fan control is not working right. There are issues if you have multiple hard drives that can be resolved.

Though you do not have a Macbook, the basic installation steps are the same.

---

### Post by david_finlayson on 2008-06-12
> **cyberdork33 said:**
> 
WiFi is a pain, like all the other Macs out there... Fan control is not working right. There are issues if you have multiple hard drives that can be resolved.

Uncertain fan control on a workstation sounds like a disaster waiting to happen.

---

### Post by cyberdork33 on 2008-06-12
> **david_finlayson said:**
> Uncertain fan control on a workstation sounds like a disaster waiting to happen.
yep. They seem to keep themselves cool for the most part (firmware controlled), there is just not manual control in the OS (yet).

Support probably needs to be added to the applesmc module if it hasn't been already.

---

