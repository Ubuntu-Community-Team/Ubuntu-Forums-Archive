---
title: "Computer does not shut down after fresh LXLE 14.04 install"
date: 2014-07-20
forum: Any Other OS
---

### Post by Caveat_Emptor on 2014-07-20
I've read many people having this problem, although seems to be with different root causes. Tried the solutions suggesting adding to the GRUB_CMDLINE_LINUX_DEFAULT parameters in grub but no avail.

Running LXLE 14.04 64 bit. I've never had this problem before with older releases of Lubuntu or Ubuntu for years.

When I shutdown or restart, the computer starts halting processes, and seems to get stuck at a point that says something like:

activating wifi adapter
Applying Power Save Settings ata3.000 (Error...)
....
....

ata3 is my only hard disk on this computer (SATA). ata1 and ata2 are the dvd and cd drives.
The funny thing is, I have not enabled my wifi adapter, although it's attached.

It looks like it's trying to do something with the hard disk, and hanging.

Any help ppreciated. It's driving me nuts.

Regards

---

### Post by QIII on 2014-07-20
[I]Moved to **Other OS/Distro Support.**
[/I]
LXLE is *based on *Ubuntu, but is a separate OS in its own right.

---

### Post by kc1di on 2014-07-21
Hi Caveat_Emptor  and Welcome to the Ubuntu forums,

LXLE is not an official ubuntu release, so it may be better for you to ask on LXLE's forum or chat channel.
Forum found [here: ]("http://lxle.net/forum/")
freenode chat found[ here.]("http://lxle.net/forum/#/discussion/52/finding-help-in-the-lxle-chatroom-/p1")

I seem to remember that some machines have a buggy ACPI implementation and you shut down problem may be solved by 
booting without acpi enabled.

---

### Post by Caveat_Emptor on 2014-07-21
LXLE is based on Lubuntu, and comes with a lot of default packages. It's not really a totally new distro.

I posted here because this bug is a known one and lots of people have had the same kind of shutdown issue in all  ubuntu variants, so I don't believe it has anything to do with the Desktop environment or window manager etc.

---

### Post by kc1di on 2014-07-23
have you done an upgrade of the software on your machine?  This bug has been fixed according to bug tracker. It seems it was a bug in lxsessions. 
Which version of LXLE are you using 32bit , 64bit Stable or beta?  if it's beta let the developers know about the bug. So they can fix it before final is released.
you can always shutdown for now with the terminal command ```
sudo shutdown -h now
``` or reboot ```
sudo shutdown -r now
```
if that does not work it should at least give you an error message that may give something to go on.

---

### Post by Caveat_Emptor on 2014-08-06
sudo shutdown -h now does not work. Same behavior. No error messages.

I have LXLE 14.04 64 bit stable and have the latest updates.

FYI, I've had this configuration for 8 years, and was working fine with Ubuntu, Lubuntu variations till 13.04. The issue appeared the moment I upgraded to 14.04 within Lubuntu. I thought there was a bug in the distro, so did a clean install of LXLE. Same behavior. On searching Ubuntuforums, I see a lot of people with similar issues in 14.04. The most common fix is to change flags in grub, and I've tried all of them without result.

---

