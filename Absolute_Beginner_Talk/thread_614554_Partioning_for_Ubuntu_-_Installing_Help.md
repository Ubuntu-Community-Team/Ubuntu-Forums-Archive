---
title: "Partioning for Ubuntu - Installing Help"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by eldara5 on 2007-11-16
When i start installer the only options i have are use all or manual, ive gone into manual created an ext3 partion of 35gb for the data and a swap partion of 2gb. And the rest of my HD (300GB) Is still NTFS for windows. Ok so i select the ext3 and click forward and i get an error message:

No root file system is defined.

Please correct this from the partitioning menu.

I dont know what to do i cant find nothing in the partion menu, so i tried clicking my Swap one and next, the same error, (the mont point on the ext3 partion s set to /home is this ok?)

Thanks in advance,
Eldara

---

### Post by tybalt on 2007-11-16
Hi,

you need to define the partition as ROOT "/" before you go to next step. When you define the partitions, you need to define what use you give to it.

Probably, your 35Gb partition shows it is /dev/hda2 or something like that. instead of that, it should show /.

This is because Ubuntu lets you define more partitions for different folders, like users, etc.

Hope this helps.

---

### Post by erfahren on 2007-11-16
from this tutorial: [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
see this screenshot [http://img216.imageshack.us/my.php?image=feistydual12tj0.png](http://img216.imageshack.us/my.php?image=feistydual12tj0.png)

set the mount point there

BTW: all you really need for swap is 1GB. There was a guideline that said to use twice the size of your installed RAM, but that's a little outdated (from when PCs had about 256 or 512 or whatever).

---

### Post by eldara5 on 2007-11-16
ok thx guys. Will they work in any order? right now i have windows(NTFS),Partion(ext3) and swap at end

---

### Post by doomster on 2007-11-16
yes any order would be fine to work.just make sure you follow the guide given above to avoid malfunction. if you think your problem is solved, edit first post and mark title as [SOLVED] :)

---

