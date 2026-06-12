---
title: "edgy &quot;alternate&quot; cd for a computer with 128 Mb RAM?"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-10-20
Is there or is ther going to be a CD for installing Edgy similar to the Dapper alternate install CD that could be used on computers with less memory? I have been able to upgrade my system to Edgy with this computer, but I think I will do a fresh install.

---

### Post by underdog512 on 2006-10-20
> **1002285 said:**
> Is there or is ther going to be a CD for installing Edgy similar to the Dapper alternate install CD that could be used on computers with less memory? I have been able to upgrade my system to Edgy with this computer, but I think I will do a fresh install.

Why exactly do you want to do a fresh install?

---

### Post by 1002285 on 2006-10-20
> **underdog512 said:**
> Why exactly do you want to do a fresh install?
2 reasons.
1) I have partitions like this:
/dev/hda1   *           1         608     4883728+   7  HPFS/NTFS
/dev/hda2             609        3654    24466995    5  Extended
/dev/hda5            2561        3654     8787555    b  W95 FAT32
/dev/hda6             609        1581     7815559+  83  Linux
/dev/hda7   *        1582        2514     7494291   83  Linux
/dev/hda8            2515        2559      361431   82  Linux swap / Solaris

The problem is I want to add the hda5 - that is currently in FAT32 - to my home partition and have one bigger home partition. I have not found a way to format it over because linux partitions - both / and /home have bigger numbers - hda6 and hda7 that hda5.
Copying everything important to another computer and installing Ubuntu again seems a possible solution.

2) Wifi settings don't work after upgrade to edgy. It works if I can spell out exactly the ESSID of the access point, but it does not let me choose from available access points. I think I need to either install dapper again or try a fresh install of edgy, but until that time I am forced to use Windows. Dist-upgrade of Edgy today did not solve this problem.

Do you think there are better solutions for me?

---

### Post by PriceChild on 2006-10-20
Of course there will be an alternate install.

Fresh installs are sometimes good to get rid of old errors. Upgrades don't always go perfectly.

---

