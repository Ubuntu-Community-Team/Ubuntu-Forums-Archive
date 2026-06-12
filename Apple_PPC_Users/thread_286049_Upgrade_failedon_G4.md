---
title: "Upgrade failedon G4"
date: 2006-10-27
forum: Apple PPC Users
---

### Post by shadie on 2006-10-27
Did the upgrade using the upgrade tool, everything looked fine so I left it downloading the upgrades, next time I checked the XFCEScreensaver would not accept my password, no SSH and no other console to see what was going on so I shutdown.

Now I have a tv test pattern around 15 seconds into the boot cycle and after a minute a I get a (initramfs) prompt with a few basic commands available.

I'm downloading the 6.10 CD at the moment, any ideas?

---

### Post by pauljwells on 2006-10-31
I had very stable, and more or less identical installs of Dapper on a PC and on a mac powerbook. I upgraded both using the proper tool. The pc went perfectly and is working fine right now. The mac looked OK, but I had several lock-ups and crashes, it hosed my partition (fsck found dozens of errors) and finally just refused to boot.

A clean install from the CD went fine and it is all working as well as ever now.

The only regression, for me, is that powernowd makes the system lockup, whereas on the last update of dapper it worked ok. I disabled powernowd in 'system-administration-services' and all ok now.

back up your data!!

---

