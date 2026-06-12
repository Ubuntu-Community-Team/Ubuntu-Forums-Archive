---
title: "Gparted won't shrink XP partition (I want to add Gutsy as dual boot)"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-01-08
I booted into a live cd (Parted Magic) and tried using gparted to shrink the XP partition on the used laptop I just bought. Gparted shows the partition but won't allow me to shrink it because gparted says it found "1 or more bad sectors" on the disk. It said to run Win CHKDSK, then boot up twice and return to gparted. I ran CHKDSK, but CHKDSK says the disk is fine--it finds no problems with the disk.  So I booted up twice and then returned to gparted, but gparted still won't shrink the partition because it says there are "1 or more bad sectors" on the disk. What should I do? I want to know if there are really bad sectors on the disk or not; and then I need to shrink the partition.

---

### Post by frup on 2008-01-08
Try something like "hirens boot disc", search it on google. Instead of using gparted, does using the actual installer (which still allows you to resize partitions) work?

---

### Post by Sef on 2008-01-08
1) It could be the hard disk is bad.

2) It could be that gparted is bad.

a) Did you md5sum the download?

b) Did you burn it at 4x or less?

---

### Post by lvleph on 2008-01-08
delete

---

### Post by swarup on 2008-01-08
> **Sef said:**
> 1) It could be the hard disk is bad.

I suppose so, but doesn't it seem strange that the Windows utility CHKDSK checks out everything as being fine? 

Also, for whatever it's worth, I've been using the computer the last couple of days since I got it and it seems to be working just fine.

> **Sef said:**
> 2) It could be that gparted is bad.

a) Did you md5sum the download?

b) Did you burn it at 4x or less?

I've had this gparted cd for around four months and used it already with three other computers, and it worked just fine to shrink those partitions. So it seems to be working fine.

I would have burned it at 4x, yes. Don't know what md5sum is. But as I say, the gparted disc has worked fine with three other computers.

How can I resolve the discrepancy between what CHKDSK says, and what gparted says? And is there some way to get around the issue, to get gparted to shrink the partition?

---

### Post by mikeyphi on 2008-01-08
Another thing to check - make sure your windows is fully Defraged.

---

### Post by swarup on 2008-01-08
> **frup said:**
> Try something like "hirens boot disc", search it on google. Instead of using gparted, does using the actual installer (which still allows you to resize partitions) work?

1. I did try using the actual gutsy installer, but as with happened the last time I tried to shrink an XP partition, the installer disc does not give the option to do so. When I used the installer with Win 98 it did shrink the partition just fine, but with XP I have found--both with feisty and gutsy--that the installer livecd does not offer to shrink the partition. It wants to either delete the XP partition entirely, or you'll have to manually shrink it (which is complex and I am not familiar with it). Those are the only two options. --Which for me, basically means I have to use another means such as gparted.

2. I'm going to take a look at the hirens boot disc now. Thank you for the suggestion.

---

### Post by swarup on 2008-01-08
> **mikeyphi said:**
> Another thing to check - make sure your windows is fully Defraged.

Yes, thank you. It is already fully defraged. Actually, the disc was wiped clean and XP professional loaded fresh just before I purchased it. All I've loaded is MS Office. And even though there isn't much on the disc, I did defrag it before starting to attempt to shrink the partition.

---

### Post by Wiifreak on 2008-01-08
Or else:
Install Tune up Utilities (15 days trail).
Do al checks.

---

### Post by swarup on 2008-01-08
> **Wiifreak said:**
> Or else:
Install Tune up Utilities (15 days trail).
Do al checks.

Thank you for the suggestion. I've just located it on Google, and I'll download it and do all the checks, and see what it finds. Perhaps it will give some further insight into what is going on.

---

### Post by swarup on 2008-01-08
> **Wiifreak said:**
> Or else:
Install Tune up Utilities (15 days trail).
Do all checks.

Actually, I've just downloaded and installed it. I requested it to do its most thorough check, including a search for bad sectors. But all it actually seems to do, is manage the Windows utilities already installed for such purposes. That is when I requested Tune-up Utilities to start its thorough check, all it did was initiate the Windows CHKDSK. --Which I've already run. So unfortunately, this does not seem to be of much help. But thank you for your effort!  :) (If I've missed something about the Tune-up Utility and there is something more there than what I've seen, please let me know.)

---

