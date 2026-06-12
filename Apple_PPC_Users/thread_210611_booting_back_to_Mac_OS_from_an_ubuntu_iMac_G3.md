---
title: "booting back to Mac OS from an ubuntu iMac G3?"
date: 2006-07-07
forum: Apple PPC Users
---

### Post by ruftytufty on 2006-07-07
I'm helping to set up a lab with a bunch of old iMac G3's, all 400/450MHz. One of them has ubuntu installed on it, but it hangs when I try to log in.  Having both OS's on the machine would be useful, but for now we'd like to get it useful as quickly as possible, which means not spending a lot of time trying to debug the ubuntu install.  So, I'd like to get Mac OS X back on the machine for now, and have some questions:

Does installing ubuntu on a G3 alter the firmware or anything else that would prevent me from installing OS X on the machine again?

I've tried booting from a Mac OS Firewire drive, but the machine seems to ignore the Option key, which would normally give me the option of choosing a boot volume.  And, I haven't been able to get booted far enough into ubuntu to select an alternate boot volume (if firewire booting is supported).

Haven't tried booting from a CD yet.  That's probably the next step, but I get limited access to the machines, and don't have internet access at the lab (sounds odd, yes, but it's in a locked drug/alcohol treatment facility for teens, and they don't get such niceties).

Thanks!

---

### Post by 3rdalbum on 2006-07-08
Installing Ubuntu doesn't alter the firmware. It does, however, set the computer up to boot Yaboot, which is the Linux bootloader for Macs.

When you boot from an OS X CD, the boot settings will be changed back to OS X. If OS X is already on the hard disk, you will just be able to restart and it will go straight back into OS X. Otherwise, just do a reinstall and you'll be fine.

---

