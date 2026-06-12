---
title: "Partitioning with Lubuntu"
date: 2014-03-14
forum: Apple Hardware Users
---

### Post by bgriffinn on 2014-03-14
I have a 160 (149 usable) GB hard disk. I already installed OS X 10.4.11 on 119 GB and left about 29 GB of free space for Lubuntu.

I noticed in the automatic installation of Lubuntu (Lubuntu alongside Mac OS X, which was already installed) that the installation had created only 1.28 gb of swap space. But I still ran the automatic installation because it created the partitions automatically, correctly taking up all the 30 GB of free space. Otherwise I would have had to create all the necessary partitions of the right kind etc.

My machine is as follows

iBook G4 933 MHz
1.12 GB Ram
160 (149 usable) GB HD

As Lubuntu is a bit slow and the fan runs a little too often (which never happens with OS 10.4.11) I thought I'b better expand the swap space. Now, since Lubuntu is already installed, I can't simply take away space from my directory and add it to the swap space. I suppose that would cause trouble.

1) If I take away space from my Ubuntu directory (from 27 GB to 25) and add 2 GB to the swap space partition in GParted in live mode (just to be an the safe side, 3 GB in total), **I expect I'd better reinstall Lubuntu, right** (I'm not using unallocated space, but resizing the directory of a current installation)**?** I wouldn't care since I have nothing on it yet. Now, this time I'd have to choose to "create/resize my own partitions" in the installer (otherwise it would again create the standard size partitions), and I would leave the partitions untouched (having already resized them in GParted). But **would the installer** (in this non automatic mode) still make use of all the created partitions (**"understand" that they're the relevant partitions** for Lubuntu) **and most of all leave my mac hd partition (119 GB) untouched**?

2) As far I as I can see in the Disk Utility of Mac OS X, OS X only has the one 119 GB partition. I can't see any other partitions, boot partitions and stuff like that. Now, **as long as I mess around with the other partitions in GParted**, specifically the 27 GB Ubuntu directory and the swap space, **nothing could happen to my OS X partition and to my OS X installation on this partition**, right? **Can I be sure of this?** I can delete and change the Ubuntu directory and swap space partitions and reinstall Lubuntu as many times as I want and I wouldn't have to worry for my Mac partition and the stability of that installation, correct?

3) Am I right in thinking that unallocated space, free space, has absolutely no function? I mean, it doesn't serve any purpose at all, does it? Or is it desirable to leave some in certain places?

Thanks for your patience. I hope I've made myself understood. Please let me know if more information is necessary.

bgriffinn

---

### Post by ajgreeny on 2014-03-14
I don't think enlarging the swap space partition will make any difference at all to the way your lubuntu works; the problem is really that your cpu is comparatively old and slow.

If you really do want to try it is easiest to do with a live DVD/USB, though even using that you will need to right click on the existing swap partition and choose "swapoff"

---

### Post by bgriffinn on 2014-03-14
I did it anyway... because I had nothing to lose and plenty of space. At the moment, I only see myself using Lubuntu (as opposed to OS X) for some internet websites, today I discovered Minitube and things like that. A bit of swap wouldn't hurt, I guess.

All went well in GParted, but the Disk Utility, while it sees the expanded swap partition, sees the directory EXT4 partition as the same size as before (Swap went from 1.28 to 3 but the EXT4 still appears to be 29 GB instead of 27). 

I don't much care because I have nothing on Lubuntu, should it crash. But I'd rather reinstall. With these partitions, though. Or with enough free space to add later to the swap partition without "hurting" a legitimate partition. I've found plenty of messages of people asking if they'd better expand the swap partition with free space they happen to have, but I don't know how they got to have free space in the first place without messing with partitions already created and in use or providing for such space in the installation process.

The swap partition being 1.5 to 2x the RAM size does seem to be the rule, but the standard installation created a swap the same size as the ram.

bgriffinn

---

### Post by ajgreeny on 2014-03-14
> **bgriffinn said:**
> I did it anyway... because I had nothing to lose and plenty of space. At the moment, I only see myself using Lubuntu (as opposed to OS X) for some internet websites, today I discovered Minitube and things like that. A bit of swap wouldn't hurt, I guess.

All went well in GParted, but the Disk Utility, while it sees the expanded swap partition, sees the directory EXT4 partition as the same size as before (Swap went from 1.28 to 3 but the EXT4 still appears to be 29 GB instead of 27). 

I don't much care because I have nothing on Lubuntu, should it crash. But I'd rather reinstall. With these partitions, though. Or with enough free space to add later to the swap partition without "hurting" a legitimate partition. I've found plenty of messages of people asking if they'd better expand the swap partition with free space they happen to have, but I don't know how they got to have free space in the first place without messing with partitions already created and in use or providing for such space in the installation process.

The swap partition being 1.5 to 2x the RAM size does seem to be the rule, but the standard installation created a swap the same size as the ram.

bgriffinn
Swap partitions being 1.5 - 2x ram is a very old rule of thumb from when computers had only a few MB of ram, not the amounts current machines, including yours, now have.

It could be useful to see a gparted screenshot of your disk to see exactly what we're dealing with currently before suggesting further moves.

---

### Post by bgriffinn on 2014-03-15
I didn't know about that being an old rule that doesn't apply even to my old iBook. In this case, it's not worth it to bore you with the current state of my HD. I have nothing on either OS X 10.4 or Lubuntu yet, so I have no great interest in trying to salvage the current installation.

I will probably just reinstall both systems and be done with it. I thought perhaps I might create a second Mac OS Journaled (or not journaled) partition in the OS X Disk Utility when formatting again (a couple of GBs) and leave it empty. The standard "Lubuntu alongside Mac OS X" installation would be sure not to touch that. Later I could delete it and use it for swap. But you're telling me that I shouldn't bother, so I won't.

Thank you very much for your help.

bgriffinn

---

