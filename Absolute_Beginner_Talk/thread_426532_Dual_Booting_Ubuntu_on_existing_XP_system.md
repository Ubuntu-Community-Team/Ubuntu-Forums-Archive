---
title: "Dual Booting Ubuntu on existing XP system"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by WanderingKnight on 2007-04-28
Hello! I've decided to set up an Ubuntu system in my PC, in the hopes of completely switching out from Windows in the future. But as of now, I'd rather have the XP system available. This is the least of the problems, since I know more or less my way around partitions. The deal is the following: What do I do with all my data already stored in NTFS format?

The distribution of my drives is as follows:

Physical Drive 1 (This'll is the drive most likely to get XP & Ubuntu)

80 GB Partitioned in NTFS

This drive is the least of the problems, since none of the data is vital, and I have actually already backupped the useful data into the other drive, which is as follows:

Physical Drive 2

20 GB NTFS <--- Windows XP resides here
90 GB NTFS <--- Precious data resides here (more or less 60 GB, the rest is free but still in the same NTFS partition)

My idea is to format the first physical drive with a 10 GB NTFS partition for XP, and the rest for Ubuntu. Now, doing that is relatively easy even for a Linux newbie like me, but the problem is, what do I do with the 60 GB worth of priceless data written in NTFS format on the 2nd drive? I know I can read it from Ubuntu, but can't write on it.

I've thought of a workaround, and that is, to transfer, using Windows, all the data from the drive to a FAT32 partition on the first drive, but then I'd be stuck with a FAT32 partition :(

Any solution you can think of? (Other than backupping all my data on CD/DVD).

---

### Post by viciouslime on 2007-04-28
You could install the xp ext driver. If you're thinking of using ubuntu as your main OS then I can highly recommend this method.

This way you will be able to read and write to your ubuntu partitions from XP should you find you really have to boot it, and ubuntu is all set and ready for you to just wipe out that xp install and go full-on ubuntu :D

To get the xp driver see this website: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by bulldog on 2007-04-28
Your 80GB drive,
10GB partition NTFS windows
10GB partition ext3 /  [root]
60GB partition ext3 /data or /home whatever you prefer.

Install this driver in windows and you'll be able to read and write from windows and ubuntu to this /data partition.

[http://www.fs-driver.org/](http://www.fs-driver.org/)


EDIT;
Two souls,same thoughts LOL

---

### Post by orb9220 on 2007-04-28
> what do I do with the 60 GB worth of priceless data written in NTFS format on the 2nd drive? I know I can read it from Ubuntu, but can't write on it.

Yes fiesty has the ability to enable read and write on ntfs partitions.

> I've thought of a workaround, and that is, to transfer, using Windows, all the data from the drive to a FAT32 partition on the first drive, but then I'd be stuck with a FAT32 partition

Yes but fat32 is fine and stable which is what mine is on. The only limitation is you cannot have a single file larger than 4gb and you cannot use linux backup commands like rsync to save to because fat32 does not support the permissions flags of ext3 file systems.

Another suggestions which I use is to also create a seprate /Home partition so when I do a clean install from edgy to feisty I only have to format root / and swap on the new distro and I can leave my /home intact where I have my programs,settings,etc.. untouched.

And using [http://www.fs-driver.org/](http://www.fs-driver.org/) driver also let's me mount ext3 partitions in windows where I can read and write data to my linux partitions.

---

### Post by WanderingKnight on 2007-04-28
OK, so I gather all I have to do is install the ext driver on Windows, and pour all my data on the first drive (formatted with ext)

*shrugs at the gruesome task of copying 60 GB*

PS: What's this about feisty supporting NTFS writing?

---

### Post by orb9220 on 2007-04-28
No you can also just install ubuntu on first drive and enable ntfsg support and use the data partition as normal.

Different ways to go about it you just have to be clear on what you want. Do you want not to have to do anything and leave it alone? Do you want to move it? Do you want win and ubuntu to access it?

---

### Post by WanderingKnight on 2007-04-28
I'd like my Ubuntu system to be able to fully access the NTFS partition, with both read and write capabilities. Are there any limitations on NTFS support using feisty?

---

### Post by orb9220 on 2007-04-28
If you enable ntfsg support then you will be able to read and write to partition.
If you install [http://www.fs-driver.org/](http://www.fs-driver.org/)  on your xp then you will be able to also access your linux partitions from xp.

---

