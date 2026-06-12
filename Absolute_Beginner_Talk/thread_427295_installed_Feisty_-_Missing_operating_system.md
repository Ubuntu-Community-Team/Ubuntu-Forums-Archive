---
title: "installed Feisty - Missing operating system"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by treeby on 2007-04-29
hi i just installed Feisty onto my 500gig sata drive (have a duo core processor and msi mother board)
then when i went to restart it said "Missing operating system"
the grub menu didn't even start up.

i had installed vista on the drive previously and after trying to get it to dual boot with feisty i just
gave up and wiped the drive with gparted and then just did an automatic install on biggest
blank space with the ubuntu installer...everything went fine..it made the ex3 partition, installed
the files but then when i went to reboot...nothing. do i need to defrag the drive from partitioning
it around so much? is there any way to do that from the liveCD? this is really frusterating..i've been
trying to get ubuntu to work for three days now. i've wasted so much time i feel like i'm about to
give up.

thank you so so so so much if you can help me

---

### Post by reality_hunter on 2007-04-29
do you have two hard drives????  If you have two hard-drives, then goto bios setting and change the boot priority to the other one and it should work~!

---

### Post by attelas on 2007-04-29
The first partition of your hard disk (the one you want to boot from) might not be set 'active' anymore (since you wiped your hard disk).
Look for an old boot disk containing fdisk and set the partition active.
I don't know if this solves your problem but I just checked  and mine (on which GRUB is located)  happens to be set active.

---

