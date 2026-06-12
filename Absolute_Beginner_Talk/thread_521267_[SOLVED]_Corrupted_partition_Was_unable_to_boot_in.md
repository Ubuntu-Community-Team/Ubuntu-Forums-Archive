---
title: "[SOLVED] Corrupted partition? Was unable to boot into livecd. Any alternate solutions"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-08-09
Long story short: I used the ext3 driver from fs-driver.org and I have just discovered that (at least) one of the partitions is corrupt. 

I've attempted to boot using the Feisty livecd so I can do an e2fsck but now the livecd won't load!

Any alternate solutions I can try to repair the partition? Would "sudo tune" do the job?

Edit: Hmmm it turns out that running "sudo e2fsck -fy /dev/sd#" worked. However, take note that it should ONLY be run while the partitions are not mounted. Otherwise, you risk damaging your data!

---

