---
title: "Installing ubuntu 7.10 while maintaining recovery partition"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Bigguy2468 on 2007-10-21
Hello to one and all.
I recently purchased a new Compaq computer that came with Vista Home Basic. I ended up finding out later that they didn't make any drivers for XP and that you must use Vista. At any rate, I wanted to put Ubuntu 7.10 on a partition I will create. The HD is 120GB so I have lots of room to spare. 

Anyhow, Compaq puts a partition on the HD that it calls the "Recovery Partition". The idea is that if you mess up you can press F11 and do a full system recovery from this partition.

When I installed Ubuntu on other machines, I usually am only dealing with the Windows and the Linux partitions choosing to write GRUB to the Master Boot Record. I am worried that GRUB will mess up this recovery partition and am looking for some advice. I still want to be able to be given the choice of recovery and don't want GRUB to only leave me with the options to boot windows or Linux. I guess part of the answer is where this option to press F11 comes in, if before the boot record maybe I'm OK?

Has anyone dealt with this before and if so, I would look forward to hearing your input.

Cheers!

---

### Post by raul_ on 2007-10-21
Humm. My packard bell also has a recovery partition and i think it didn't affect anything.

the thing is, when you press F11 you don't actually load the MBR, so it shouldn't make a difference. I could be wrong though

---

### Post by Gazneth on 2007-10-21
Does your recovery partition give you the option to make DVD's?: I use a Toshiba lappy and made discs then formatted it all for Ubuntu.:)

---

