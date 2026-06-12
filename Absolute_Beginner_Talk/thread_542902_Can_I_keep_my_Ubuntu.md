---
title: "Can I keep my Ubuntu?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by felipebarroeta on 2007-09-04
Hello you all!

I wanted to know if Ubuntu stays safe if I install windows XP. I have now a NTFS Win Vista 110GB Partition, but it crashed big time. So bad that I havent been able to run vista since more than one week, and from three days to now, I have even not been able to access the partitions from Ubuntu, which keeps loyal and stable. 

So, does Ubuntu stays safe or does XP erase it with the installation? I'm planning to do that installation on that 110GB Win Partition. Anyway, if someone can give me some piece of advice I'd be much thankful, as I'm a beginner with this...

Peace!

---

### Post by Gone fishing on 2007-09-04
Yes if you delete the Vista partition, using for example gparted you can install this from synaptic . You can then install XP into the free space (XP install program allows this). However, XP will over write the grub boot loader although this can be repaired using the live cd

---

### Post by vanadium on 2007-09-04
My advice: reformat that windows partition to ext3 and gain additional storage space on your computer ... no, I am joking: you must do as you like.

Windows will claim the master boot record and destroy Grub. So, immediately after installing Windows, you will not be able to boot Ubuntu. You will need to restore grub, and after that, you will have the choice at boot time between the two operating systems.

I have no experience myself reinstalling grub, but I have seen a post about it: it is not too difficult. Look on this forum for "restore grub" or perhaps another soul will jump in and provide a link to specific instruction.

---

### Post by alienexplorers on 2007-09-04
Restoring grub is quite easy.   You can follow the link in my signature to reload GRUB.

---

