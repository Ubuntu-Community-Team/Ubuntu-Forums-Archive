---
title: "Installation issue"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Khiamal on 2007-03-16
I at first mistakenly installed the alternate CD, in OEM mode, and couldn't write to a hard drive.  So, I tried to install the regular 6.06 CD, and I keep getting the following:

"Kernel panic - not syncing: No init found.  Try passing init= option to kernel."

I've Googled this without finding anything resembling an answer that I was capable of understanding - this is my first attempt at installing Linux.  I tried adding "init=/kernel" to the end of the boot string revealed by pressing F6, with no change.

Any suggestions?

By the way, the laptop I'm attempting to install this on is a Dell Smartstep 250N, with the original 40G drive, 2 gig of memory, a dual-layer DVD burner, P4-2.4 desktop processor, and an aftermarket battery (not sure what effect that might have, but, hey - it seems to have some effect on booting XP on battery - locks up sometimes, as opposed to the old, worn-out battery).

---

### Post by mahy on 2007-03-16
this sounds pretty gross. Have you tried booting some other distro? (e.g. Knoppix) Just to make sure your computer is alrite.

---

### Post by Khiamal on 2007-03-16
The laptop works properly with XP (on a different hard drive).  I'm attempting to install this on a clean 40 Gig drive that originally came with this laptop, so I know it's compatible.  I can try taking the 2Gig of memory out, in case that's too much for Linux in a machine this old.

I've attempted thus far to load Ubuntu 6.06 and 6.10, Linux Mint, Freespire, and Debian. I got the following results:

Ubuntu 6.06 Alternate: Successfully installed, but I was unable to write to the hard drive, as the OS did not recognize me as the owner (not sure why, as I was the only user, and I'd gone through the oem-config-prepare command.

Ubuntu 6.10 Alternate: Same as 6.06 Alternate.

Ubuntu 6.06 Regular - Kernel panic - not syncing: No init found. Try passing init= option to kernel.
Ubuntu 6.10 Regular - same as 6.06 regular.

Linux Mint - same as Ubuntu 6.06/6.10 regular

Freespire 1.0.13: Kernel panic - not syncing: VFS: Unable to mount roos fs on unknown-block(1,0)

Debian: VFS: Cannot open root devide "hda1" or 03:01
Please append a correct "root=" boot option
Kernel panic: VFS: Unable to mount root fs on 03:01

Any suggestions?

---

