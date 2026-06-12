---
title: "vista and ubuntu dual booting"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by biggjb2010 on 2007-04-16
i've been looking around at all the other threads for this but seeing as i am pretty new i do not know what to type in the terminal for a command...i downloaded that file and have extracted everything i just need to know wat the command is.

"If you find your Vista's not happy after repartitioning using Ubuntu repartitioner, run don't walk over to [www.linux-ntfs.org](www.linux-ntfs.org) & grab a cvs snapshot of their ntfs tools, specifically ntfsfix. I executed "ntfsfix /dev/sda2" which took very few seconds then rebooted & selected Vista. Vista did a little complaining then bashed away at the disk for a little while, & finally booted & ran. I immediately rebooted Ubuntu to make sure it is still ok, & it is!

After downloading the cvs snapshot, simply
tar jxvf ntfsprogs_[date]_.tar.bz2
./configure
make
sudo make install
& run ntfsfix [vista partition device name]."

i just bought this gateway comptuer that has 320 gb hd, dual core 1.8 ghz, 1 gb of ram and do not want to lose the data from vista. ive read that if you run chkdsk on the recovery cd it will help but i cant manage to get the command prompt from the cd to come up either.

---

### Post by NESFreak on 2007-04-16
could you be a bit more clear on what exactly you are trying to accomplish?

NESFreak

---

### Post by dstew on 2007-04-16
To get to the recovery console command prompt, use the Windows CD-ROM to start your computer. At the "Welcome to Setup" screen, press F10 or press 'R" to repair.

---

