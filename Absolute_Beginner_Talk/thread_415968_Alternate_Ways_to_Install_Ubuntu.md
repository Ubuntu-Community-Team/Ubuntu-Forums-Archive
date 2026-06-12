---
title: "Alternate Ways to Install Ubuntu"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by guyver on 2007-04-20
Okay here's my situation.  I would like to install Kubuntu / Ubuntu on my GF's laptop except there's a catch.  Her hot swappable CD-ROM drive does not work and her system does not support booting from a USB storage device.

What I'd like to do is somehow boot from a floppy which would either allow me to do one of two things:

1.  Recognize a USB CD-ROM drive and allow me to do a regular install of Kubuntu (preferably) straight from the CD.

2.  Autodetect her onboard ethernet from the boot floppy and from there I might get instructions to type some script commands to get installation underway via the ethernet.

For the life of me I do not know why she's even running Windows XP on this machine because it only has 128MB of RAM.  I also realize I should be looking at Xubuntu for this laptop but she prefers the KDE environment.

If there are other options, I am receptive to this, but I am essentially a Linux newbie, so some of the more exotic ways of doing this may fly over my head.

Any help would be greatly appreciated.

---

### Post by tbg58 on 2007-04-21
Have you tried going into the BIOS to see if there is a selection to allow USB boot?  I had a similar problem and loaded a bootable USB disk image onto a flash key, booted up and installed.
As I recall, I had to go to the manufacturer of the notebook web page and get a bios upgrade (the floppy still worked).
This worked for me -- I'll hunt around and see if I can find the steps, but the BIOS has to allow bootable USB devices.  Your external CD will probably work if you can get over this hump.
Good luck!
-rob

---

### Post by jiminycricket on 2007-04-21
You could do a PXE boot, requires another machine running Ubuntu on the network, and then her machine uses an option in the BIOS: [https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot)

Or the Ubuntu netinstall from a floppy disk with a Windows machine: [https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

---

