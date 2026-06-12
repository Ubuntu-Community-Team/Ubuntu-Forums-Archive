---
title: "Fixing Dual  Boot?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-02-05
Okay, so I'm going to be installed Ubuntu soon, but I had this going on, XP On HDD 1, Vista on HDD 2, Me being the crazy stupid person decides to be lazy and instead of properly getting rid of Vista I just logged on to XP and formatted the second HDD. Doing so, when I restart my computer I have the option of choosing XP or Vista but I can't choose vista for obvious reasons. How do I fix this so Windows XP just boots.

---

### Post by Linux_Man on 2008-02-05
It is a bug in the Windows boot manager. When you install Linux it will have GRUB replacing the Windows boot manager so I don't know how to fix this (haven't used a Windows box in 6 months) from Windows but when you install Ubuntu it should be gone.

---

### Post by Blue Sassley on 2008-02-05
> **blasteryui said:**
> Okay, so I'm going to be installed Ubuntu soon, but I had this going on, XP On HDD 1, Vista on HDD 2, Me being the crazy stupid person decides to be lazy and instead of properly getting rid of Vista I just logged on to XP and formatted the second HDD. Doing so, when I restart my computer I have the option of choosing XP or Vista but I can't choose vista for obvious reasons. How do I fix this so Windows XP just boots.

If you have your Windows XP CD Boot up with it and go into the recovery console (I believe its R and then C from the install menu) Select your WINDOWS install and then type FIXMBR... to make it super easy I would temp disconnect the second HD (the one that had VISTA) and then start those steps.

Here is the info about the command from Microsoft KB:

FIXMBR
fixmbr device name
Use this command to repair the MBR of the boot partition. In the command syntax, device name is an optional device name that specifies the device that requires a new MBR. Use this command if a virus has damaged the MBR and Windows cannot start.

Warning This command can damage your partition tables if a virus is present or if a hardware problem exists. If you use this command, you may create inaccessible partitions. We recommend that you run antivirus software before you use this command.

You can obtain the device name from the output of the map command. If you do not specify a device name, the MBR of the boot device is repaired, for example:
fixmbr \device\harddisk2
If the fixmbr command detects an invalid or non-standard partition table signature, fixmbr command prompts you for permission before rewriting the MBR. The fixmbr command is supported only on x86-based computers.

Taken from:
[http://support.microsoft.com/kb/314058/en-us](http://support.microsoft.com/kb/314058/en-us)


Blue

---

### Post by Shazaam on 2008-02-05
A few things you should do before you install Ubuntu.

1. Fix boot.ini either from the XP cd "Recovery Console" (if you have an XP disk) or follow these directions--- [http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)
2.In XP DEFRAGMENT DEFRAGMENT DEFRAGMENT! Then resize/install Ubuntu.

---

