---
title: "Partitioning harddisk issue"
date: 2006-06-02
forum: Apple PPC Users
---

### Post by el3ktro on 2006-06-02
Hello,

I installed Mac OS X and Ubuntu on my iBook - everthing's fine so far. I partitioned the harddisk using the Mac OS installer. I basically just created one 4 GB partition für Mac OS X and installed it there. After that, I booted the Ubuntu LiveCD. I noticed that for some reason, the Mac OS X installer keeps ~130MB free before this 4GB partition, so I used this as swap. Behind the 4GB partition, I created the NewWorld boot partition (1MB), one 4GB partition for Ubuntu, and another 6GB or Ubuntu's /home. Then I installed Ubuntu - also no problem.

Now I want to take the remaining ~42GB of the harddisk to create one large VFAT or HFS partition to share data between Mac OS & Ubuntu - and now the problem starts. In Ubuntu, mac-fdisk says that hda7, the last, 42GB free space, does exist as an "Apple_free" partition. But the Mac OS X disk utility doesn't see this partition at all. I tried formatting this partition with Ubuntu's disk manager - I can choose this partition, "activate" it, format it with FAT, and I can actually mount it - but still Mac OS won't see it. What am I doing wrong here?

Tom

---

