---
title: "/home on a different disk (feisty)"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Lieter on 2007-04-15
Hello, i'm running a dual boot feisty/winXP now but ive decided to completely switch to ubuntu, but i have a question, ive read the forums but they only have info on putting /home on a different partition, not a different disk.

My setup:
Asus P4P800 SE Mainboard
P4 Prescott 3.2 GHz
120 GB Maxtor DiamondMax 10 P-ATA disk (6Y120P0)
200 GB Maxtor DiamondMax 10 S-ATA disk (6B200M0)

now i want to install ubuntu on the 120 GB disk(everything except /home) and /home on the 200GB one. But how can this be done in the graphical installer, i have not yet tried cause i still need my PC for school(my laptop is in RMA). so any help on this matter would be appriciated. :)

---

### Post by Wim Sturkenboom on 2007-04-15
If I remember the graphical installer correctly, it will somewhere give you the list of all partitions. It will have /dev/hda1 and possibly others) and /dev/sda1 and possibly others. /dev/hda is your pata disk (hda1 is the first partition on it) and /dev/sda is your sata disk (sda1 is the first partition on it).
'Simply' assign the home mountpoint to /dev/sda1 should do the trick.

You can use *sudo fdisk -l* to see all disks and the partitions. If in doubt, post the output here.

---

### Post by confused57 on 2007-04-15
> **Lieter said:**
> Hello, i'm running a dual boot feisty/winXP now but ive decided to completely switch to ubuntu, but i have a question, ive read the forums but they only have info on putting /home on a different partition, not a different disk.

My setup:
Asus P4P800 SE Mainboard
P4 Prescott 3.2 GHz
120 GB Maxtor DiamondMax 10 P-ATA disk (6Y120P0)
200 GB Maxtor DiamondMax 10 S-ATA disk (6B200M0)

now i want to install ubuntu on the 120 GB disk(everything except /home) and /home on the 200GB one. But how can this be done in the graphical installer, i have not yet tried cause i still need my PC for school(my laptop is in RMA). so any help on this matter would be appriciated. :)

I wouldn't recommend putting /home on a 2nd hard drive, if it failed for some reason, you wouldn't be able to boot into Ubuntu.  You might want to consider partitioning your 2nd hard drive with ext3 partitions for data storage, instead.  A separate /home on a 2nd hard drive should be pretty easy to set up during install, as Wim Sturkenboom has already mentioned.

---

### Post by Lieter on 2007-04-15
so a 200 gb etx3 partition and mount it as /home would do the trick ?

---

### Post by confused57 on 2007-04-15
That should work fine.

---

### Post by Wim Sturkenboom on 2007-04-15
confused57, now you confuse me :) In your first post you advice not to place /home on the 2nd HD, but you don't repeat that 'warning' in your last post while TS is going to do what you warned against (if I understand it all correctly)..

---

### Post by confused57 on 2007-04-15
> **Wim Sturkenboom said:**
> confused57, now you confuse me :) In your first post you advice not to place /home on the 2nd HD, but you don't repeat that 'warning' in your last post while TS is going to do what you warned against (if I understand it all correctly)..

It appears that Leiter prefers to set up his /home partition on the second drive, I was just trying to point out the possible caveats of doing it this way in my first reply...When he posted what he was going to do, I assumed he was willing to take the chance of installing home on another drive & I was informing him  that this would work OK, since he's planning on setting up his system this way.  Either setup will work, I was just making a suggestion in my first reply & didn't think it warranted repeating.

---

### Post by Wim Sturkenboom on 2007-04-16
OK. Thanks for the warning anyway as I would have not thought about it. But at the other hand, the problem does not apply to me as I always enable the root account.

---

