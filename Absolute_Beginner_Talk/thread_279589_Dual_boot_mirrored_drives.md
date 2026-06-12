---
title: "Dual boot mirrored drives"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by baronne on 2006-10-18
Hi,
I nearly gave myself a heart attack this morning, I thought I'll just setup my machine for a dual booting Ubuntu / XP setup. My machine is running a mirrored array (SATA), so I booted up the Live CD and went for the install. I tried to resize the partition which all looked ok... but then it went horribly wrong. It really didn't give me the partitions I expected. I didn't recognize the mirror, it seemed to be just the two separate drives... I thought ... oh no..
rebooted. bang. no OS. I couldn't boot into XP.
Fortunately I did an XP repair which thankfully worked.. so I'm back. But now I want to know how or if it is possible to get a dual boot thing going on with a mirrored drive? :-k 
cheers
Baronne

---

### Post by randiroo76073 on 2006-10-18
Baronne, I'm not sure about mirroring, but I think that you might have to disconnect 1 then setup, then reconnect to mirror???  Maybe someone that knows more will post shortly.  Luck to ya!
Randy

---

### Post by CatKiller on 2006-10-18
[The Ubuntu release notes]("http://www.ubuntu.com/download/releasenotes/606") says you must disable your array before attempting to install.

> Known Issues

    *

      If you are installing from the Desktop CD on a system that already has one or more RAID arrays or LVM volume groups set up, you must disable the arrays (sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan) and volume groups (sudo vgchange -a n) before starting the installer.


---

