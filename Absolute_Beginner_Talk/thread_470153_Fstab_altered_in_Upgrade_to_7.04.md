---
title: "Fstab altered in Upgrade to 7.04"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Cornbreadly on 2007-06-10
My fstab now lists my HDs as sda1 and sdb1 and so on.  I want to be able to have my 2nd HD mount in media and therefore the desktop with every boot up but under the file name that I selected for it, not the automatic one that the boot up process chooses. 

Why the change from hda1 to sdb1?  And what do i do?

---

### Post by steve.horsley on 2007-06-10
I noticed that Feisty called IDE drives sda/b not hda/b. But an update last wek changed that back again, so you had better do all your updates before trying to fix the rest.

---

### Post by steve.horsley on 2007-06-11
And an update last night changed them back from hda to sda again!!!

 I have to say, I have never known Ubuntu to be so unstable, with two updates in the space of a couple of weeks that prevent it from booting properly. How long this game is going to carry on?

---

### Post by mcduck on 2007-06-11
> **steve.horsley said:**
> And an update last night changed them back from hda to sda again!!!

 I have to say, I have never known Ubuntu to be so unstable, with two updates in the space of a couple of weeks that prevent it from booting properly. How long this game is going to carry on?

If you use UUID's instead of device names in /etc/fstab you should have no problems. ;)

Anyway, the original change was that kernel developers found out that SATA drivers handle PATA hard disks better than the actual PATA driver did. So they started using that SATA driver for all hard disks. And that caused their name to change. I suppose they now came up with some way to keep the correct names for PATA disks, or then they reverted back to PATA drivers..

---

### Post by steve.horsley on 2007-06-11
Thanks for the explanation, mcduck. Makes a lot of sense.

Yes I know using UUIDs, which the installer does by default, would mask the change. Maybe I'm just an inflexible control freak, or maybe it's because UUIDs break when you reformat partitions, but at the moment, I prefer using /dev/x notation. And maybe I should reconsider that preference. Which do I do more often - reformat or repartition? Reformat, without a doubt.

---

### Post by heu on 2007-12-20
well the same happened to me after applying some upgrades to 7.04 on december the 19th (just yesterday). I didnt really pay attention to the upgrades but they looked like some kernel upgrade. I have the following disk arrangements   hd0 - hda1  Master - ntfs with winblows xp,   hd1 - hdb1 - Slave with 3 partitions, 1 ntfs partition which i access (r-w) with ntfs-3g, one ext3 partiton with Kubuntu and the swap partition. The fstab was already configured using UUIDS and everything was working fine. After rebooting I get an error 22 (no such partition) from grub. I reboot on winblows and check out the menu.lst file and i realize that it had just been edited. There was a back up file and the date and time were those of the time at which the upgrade had been applied. The parameters looked alright though. The fstab file had not been altered and as i said UUIDs were bering used through the whole fstab. All it took to solve the problem was change the grub lines to boot linux from hd1,1 to hd0,1 but curiously the mapping i use to boot winblows didnt need to be touched? Everythings working fine (other than the hard disks are refered to as sda and sdb but it didnt affect me) now but the whole issue is kind of annoying since it seems a reoccurring issue. Does anybody know what caused it and whats the logic behind the changes, which seemed to affect grub more (and they are not reflecting the real jumpering of the hard disks)  than anything..at least on my system?

---

