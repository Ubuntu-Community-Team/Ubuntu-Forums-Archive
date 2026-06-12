---
title: "read/write"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-11-22
hi all,
well i already posted on the NTFS mounting subject but the stuff i got were how to mount a NTFS drive, but when i boot my ubuntu they are already mounted but with read-only permission how can i mount them with read/write?
one is my main hard drive which is part NTFS part EXT3 and the other one is my USB external drive which is NTFS.
I also read a couple HowTos but no help there mayb i didn't understand but they only make me mount the drive and most of the time wheni mount it it doesnt mount! i had to uninstall the stuff and reboot to mount...if that gives a clear idea.
Thanks,
Mazen

---

### Post by izmaelis on 2006-11-22
Mounting NTFS partition with read/write permission is not safe as far as I know. You can corrupt entire partition just by deleting/writing/editing/whatevering something there from your ubuntu installation.

---

### Post by Mazen on 2006-11-22
well i know that i've heard it many times but it seems not so bad actualy cuz i saw a post from the manager of the NTFS-3G project and he said that they haven't got any complaints yet from anyone and that it's perfectly safe
well i do not want to edit LARGE files, just small docs and stuff.

---

### Post by neuroplasma on 2006-11-22
[https://wiki.ubuntu.com/ntfs-3g](https://wiki.ubuntu.com/ntfs-3g)

There's a walkthrough for installing ntfs-3g. It is in beta, so beware.

---

