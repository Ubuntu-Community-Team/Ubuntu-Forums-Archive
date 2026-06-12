---
title: "2nd Hard-drive and workplaces"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Maupertus on 2007-11-18
Hiya guys, 

I searched but couldn't really find an answer so I hoped you could help.
I've got a second NTFS harddrive in my box (250 Gig Maxtor) that I can find in f-stab.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x190e190d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       19332    73360822+  83  Linux
/dev/sda3           19333       19457     1004062+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2256f17d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

So it's SDB1, only problem is that when I want to mount it with the ntfs config tool it wants to mount the windows partition. (which it cant by the way)

Can anybody help me how to get it mounted?

Second (albeit small) question....can I have 4 workspace again? If yes, please...how!? :)

---

### Post by Stebbins on 2007-11-18
in response to your second question:

if you have the workspace switcher in one of your panels, you can right-click and go to the Preferences menu.  You can then set the number of workspaces.

if you don't have a workspace switcher, you can add it to a panel by right-clicking the panel, selecting "Add to Panel", and choosing "Workspace Switcher" from the menu.

---

### Post by teryowen on 2007-11-18
try
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1

see what that does, otherwise i dont understand what your asking exactly.

---

