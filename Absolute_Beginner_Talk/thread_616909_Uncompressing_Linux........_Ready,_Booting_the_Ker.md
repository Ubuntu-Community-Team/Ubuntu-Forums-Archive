---
title: "Uncompressing Linux........ Ready, Booting the Kerne."
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by firestorm_v1 on 2007-11-18
Finished battling the kernel demon and thought this would help someone else out there:

Computer configuration:
Cyrix/National Semiconductor Geode 266MHz  processor,
256MB RAM,
Hitachi 30GB HD.
VIA Southbridge,
Cyris MediaGX nrothbridge. 

Issue:
After completing the installation, the computer is rebooted and sits at "Uncompressing Linux......... Ready, Booting the Kernel." then hangs, and doesn't do anything else.

Cause:
(I think) Suspect implemeitation of ACPI and a few other idiosyncrasies of the Geode processor make the processor unreliable in Linux 2.6x kernels.

Resolution: Perform the installation, but leave the CD in the drive.  Reboot, When presented, select "Recover Ubuntu Installation".  Follow the prompts and allow it to take you to a shell.  Since the kernel is not working correctly, you must downgrade:

apt-get install linux-i386

Let apt get the kernel and related packages.  When done, type 'exit' and this will take you back to the menu.  Let the machine reboot, and all should be well.

This also affects Fedora Core3,4,5,6,7 and some bootable CD versions as well.  Remember if you decide to make a custom kernel, you will need to compile for i386 or select "National Semiconductor Geode or Cyrix Media GX" in the processor specification section of the menu config.

---

