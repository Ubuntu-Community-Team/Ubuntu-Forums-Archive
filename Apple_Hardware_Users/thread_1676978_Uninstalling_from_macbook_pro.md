---
title: "Uninstalling from macbook pro"
date: 2011-01-28
forum: Apple Hardware Users
---

### Post by Rickythemaniac on 2011-01-28
Hi!
I recently installed Ubuntu on my macbook pro in order to test the programming capabilities.
And I were not really pleased, so I want to go back to a windows-partion.

I have created two partions for ubuntu, swap and main os-area.
How do I remove them and join them in a new partion for windows and mac to recognize?

Any help is appreciated.

//Ricky

---

### Post by the8thstar on 2011-01-28
**I'll assume you're using rEFIT or BootCamp to choose your OS at boot prompt.**

Boot from the LiveCD and choose to try Ubuntu.

Once the screen is set up, go to Applications > Accessories > Terminal. In the terminal, type:

> sudo gparted

Gparted will list all the partitions from all your disks. From there, simply right-click on the partitions you want to remove and validate your choice. For the swap, you need to unmount it first (again a right-click should suffice). Don't remove your HFS+ partition of course.

Once all the partitions have been removed, select the empty space and make a new partition to format as NTFS. You'll need NTFS-3G utils to write to your NTFS from OS X, but you'll install that later on once you're back in OS X.

A word of warning: if you have already a NTFS partition with Windows on it, you can't merge it with the new NTFS partition you just created. In this case, instead of creating a new NTFS partition, just use the one that's already showing in Gparted and extend it to the empty space left after you removed you 2 Ubuntu partitions.

Once you log back in Windows, I strongly advise you to run chkdsk to prevent confusions and mishaps for the OS.

---

### Post by Rickythemaniac on 2011-01-28
Thanks for the answer, I thought of a similiar solution, but in mac osx that would not work.

---

