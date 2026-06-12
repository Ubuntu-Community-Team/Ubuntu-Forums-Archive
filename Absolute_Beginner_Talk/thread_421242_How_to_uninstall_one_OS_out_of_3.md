---
title: "How to uninstall one OS out of 3 ?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-04-24
I have XP, Ubuntu and Kubuntu installed (Ubuntu and Kubuntu separately).

I want to remove Kubuntu.  How do I do it ? Can not just format the Kubuntu partition,
GRUB may go mad. What is the correct procedure ?

Similarly I may uninstall XP later. 

And Is there any simpler way of selecting OS at start up ?

---

### Post by Pobega on 2007-04-24
You can boot into a LiveCD, wipe the Kubuntu partition and spread the Ubuntu partition across of the new space.

---

### Post by mangoti on 2007-04-24
If Grub is not installed on the Kubuntu partition, you should be able to just format it after backing up your important data of course. Then remove the entry for Kubuntu from the grub menu.

---

