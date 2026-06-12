---
title: "Booting Ubuntu from an external HD"
date: 2007-04-09
forum: Apple PPC Users
---

### Post by Lefkows on 2007-04-09
I recently downloaded Ubuntu 6.10 LTS and was able to run it as a LiveCD. I was thinking of installing it on an external HD. Tiger does not recognize the LiveCD as a system I can boot from, i.e.,  when I go to the Startup Disk in the System Preferences the Ubuntu CD is not shown so I can't select it as a startup disk. So my question is how do you boot Ubuntu from an external HD? The only thing I can think of that might work is using the key combination at startup that tells the system to ignore the internal HD. If the only other system I have is Ubuntu on my external HD it might boot from it. Has anyone been able to boot Ubuntu from an external HD?

---

### Post by pxwpxw on 2007-04-15
**Lefkows**

This is xubuntu610 on an external 160GB firewire drive with a powermacg5 with 2 sata drives, and macosx and other linux.

Firewire is the best solution, usb is also possible but not with direct booting. (tried both).

My preferred configuration is to put the yaboot Apple_Bootstrap partition on the local hard drive (where i have to have it for internal multibooting) and include an entry in yaboot.conf for the external and that works. If you have multiple macosx partitions this can be done.

But I also can run with a bootstrap partition on the external, booting that straight from apple openfirmware. And it works with the graphical boot selector.

Either way, some editing of the yaboot.conf file may be needed to sort out the details, but it is possible to do this from macosx ( by using the macosx unix terminal application), or using the ubuntu rescue option from the alternate CD.

Macosx will not show any non-macos systems as a startup disk selectiion, but you can still multiboot using the graphical boot selector (option key at startup) or a small text menu produced by linux ofboot and yaboot. 
You can set the menu to default to macosx.

More details if/when you need them.

---

