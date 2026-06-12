---
title: "Install Assistance"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by mschraier on 2007-10-24
I currrently am runing a dualboot with XP and Frespire.  Freespire is installed on a partition whose name starts with "N", but cannot remember the entire thing.  Anyhow, I am going to be deleting Frespire to install Gutsy.  To wha do I set the new patition to during the install?  I was tpld the current partition is not the best type to use.  Can I gointo XP dsik management and set the partition ahead of time, then during insatll chosse that partition for install?

---

### Post by mikewhatever on 2007-10-24
No, but you can do it with Gparted live CD or by manually setting up partitions during the installation.

---

### Post by rolnics on 2007-10-24
I would get yourself a copy of Gparted Live cd which can be found [here.]("http://gparted.sourceforge.net/livecd.php") Then boot from the Gparted Cd you can then delete your frespire partition and create an new ext3 partition for ubuntu or leave it unallocated.

The other alternative is to boot from the Ubuntu live cd and pick the manual option when going through the install process.

I would personally do the first option, I find it easier and I fell more confident I'm about to use the right partition and not screw up my windows one!!! 

But the most important thing to do is backup all your data before doing any of the above!

---

