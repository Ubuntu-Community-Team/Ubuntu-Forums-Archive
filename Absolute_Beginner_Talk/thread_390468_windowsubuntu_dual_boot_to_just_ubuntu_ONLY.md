---
title: "windows/ubuntu dual boot to just ubuntu ONLY?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by BeastlyKings on 2007-03-22
My laptop has a 40GiB HDD in it that has both windows XP and Ubuntu on it.
The windows partition is 30+Gib with a NTFS file system, and the other two partitions are Ubuntu at 9 1/2GiB and Linux swap at 512MiB.
What I want to do (in the future not atm) is get rid of the windows partition and give all that space to the Ubuntu partition, without hurting or endangering the Ubuntu partition.

If someone could give some advice?

-BK

---

### Post by seshomaru samma on 2007-03-22
easy . open gparted (if you dont have it installed then 'sudo apt-get gparted')
format the windows partition as ext3 and mount it (mounting instructions [here]("http://www.psychocats.net/ubuntu/mountlinux"))
that's it.

---

### Post by devnulljp on 2007-03-22
Depending on partiiton layout (and I guess XP is on /dev/hda1), you might need to use gparted to delete the XP partition, clone your ext3 partition(s) into that space (then test it) and delete the original ext3 and expand the new partition to fill the space.
IIFRC you can't expand a partition backwards only forwards.... depends on your partition structure though. Give us your /etc/fstab

---

### Post by floke on 2007-03-22
Good point - but you could simply delete XP, format as ext3 as per above post, and then mount it as your home directory. Or - keep a dual boot structure but with 2 Ubuntus - one stable and one developmental - eg atm I have edgy + feisty, when feisty+1 comes out I replace edgy; when +2 comes out I replace feisty etc. If each have their own home dir. then its a piece of cake. This way you run cutting edge ubuntu but with a stable back-up if/when things go wrong.

---

