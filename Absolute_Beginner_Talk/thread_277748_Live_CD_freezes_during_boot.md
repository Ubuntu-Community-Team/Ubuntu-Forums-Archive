---
title: "Live CD freezes during boot"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by MadsTinggaard on 2006-10-15
I can't even boot the live cd (6.06 LTS).
It freezes while trying to mount the root filesystem, the second checkpoint in the boot sequence.

Drives:
The disk boots from a DVD drive that is placed as secondary slave on a native P-ATA. I have an 80GB IBM harddrive placed as a secondary master. My windows disk is placed on my SATA band.

---

### Post by Kateikyoushi on 2006-10-15
Because you are using a sata and a pata disc I would recommend to use the alternate install cd. You might run into [this bug]("https://launchpad.net/distros/ubuntu/+source/grub/+bug/8497").

---

### Post by MadsTinggaard on 2006-10-15
Thanks for the quick reply.

I've ruled out that problem, tried disabling the SATA in bios, problem is still there.

Can i force the system to bypass looking for swap partitions?
Why isn't it mounting the root system from the disk or in memory?

Update: turned off splash and quiet mode and got the following:

hdd: cd-rom_pc_intr: the drive appears confused (Ireason = 0x01)

Continuing endlessly...

---

### Post by MadsTinggaard on 2006-10-15
oh well, back to Mepis. This is the second release of Ubuntu that I have never been able to even boot.

---

