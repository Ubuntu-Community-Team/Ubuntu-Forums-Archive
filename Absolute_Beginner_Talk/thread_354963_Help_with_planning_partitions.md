---
title: "Help with planning partitions"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by gojetsgo on 2007-02-06
Hi, I'm a total newbie with regard to ubuntu.  My only experience with Linux is playing around with Knoppix and Ubuntu live CDs, but I'm ready to make the first jump.

I've read a lot of posts and guides about setting up a dual boot system, but I'm a bit paranoid about actually setting it up.  I have a laptop with a 55 GB hard drive and 512 megs of RAM.  Here's how I think it should go:

Windows - 18 GB - NTFS
Shared data - 25 GB - FAT32
Home - 1 GB - EXT3
Root (Ubuntu) - 10 GB - EXT3
Swap - 1 GB - EXT3 (?)

Does this seem like a reasonable distribution of space between the partitions? 

Also, how does the Ubuntu installation know how to deal with each partition (ie. how does it know that settings etc will go in the "Home" partition)?

Thank you in advance for your help!

---

### Post by meng on 2007-02-06
It's quite reasonable, but consider trimming your Root (Ubuntu) to 6-8 GB and giving the balance to /home. Swap partitions have their own format, you don't need to specify one once you've designated a partition as the swap.

---

### Post by ^rooker on 2007-02-06
I'm not sure why you want your /home to be in a separate partition? If you're afraid of users filling up your system space, I'd suggest using quota.

I guess what you mean by "settings going to the 'home' partition", is anwered by:
- System settings are usually in /etc
- Personal (=per user) settings/preferences are stored in each user's home directory.
(which is set in /etc/passwd)

I guess that the other chosen partition sizes are quite reasonable.

---

### Post by meng on 2007-02-06
I'm a big fan of a separate /home, it's great for reinstalls/upgrades.

---

### Post by gojetsgo on 2007-02-06
> **meng said:**
> I'm a big fan of a separate /home, it's great for reinstalls/upgrades.

Yes, that's what I read in a couple guides - it sounds like a good idea.  So do I specify that the /home partition is for settings after Ubuntu is installed or before?

Thanks again for the help.

---

### Post by meng on 2007-02-06
You can do either, but I recommend you do it during the installation.

---

