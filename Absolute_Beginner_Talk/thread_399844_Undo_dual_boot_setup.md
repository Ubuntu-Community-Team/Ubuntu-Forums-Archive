---
title: "Undo dual boot setup"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by vatechtigger on 2007-04-02
heracy I know. I have a dual boot XP and feisty setup. I have since been playing around with Ultimate Ubuntu and likes it all in one nature. Can I remove the 7.04 linux partition without jacking my XP install. basically going back to zero so I can install the Ultimate setup? Thanks

---

### Post by Clay_Banger on 2007-04-02
yeah, if u use a tool like gparted to remove the partitions associated with feisty, and pointed the new ubuntu to the free space, it should all work fine.

---

### Post by vatechtigger on 2007-04-02
I guess the main question is about the boot loader. When I install the new ubuntu distro, will the boot loader still have all the right info to make this work. Thanks again

Shawn

---

### Post by Clay_Banger on 2007-04-02
yes, when u install ubuntu again it will automaticly detect windows and have it as an option in the grub startup menu.

---

