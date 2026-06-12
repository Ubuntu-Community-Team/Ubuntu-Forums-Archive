---
title: "Dual boot partition size - help please"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by armitage shanks on 2008-02-16
Hi, I have a 60 gig tosh a120 laptop which I am wanting to dual boot. I have done a clean XP install and want to know if anyone has any suggestions on size of partitions. I use the machine with windows for work predominantly but wish to use Ubuntu 7.10 to evaluate for future use at work in place of XP. 

It would be good to be able to have access to files from both OS (I think that 7.10 can read and write to NTFS.

Anyway any advice on partition size would be welcome.
Thanks in advance.

---

### Post by LaRoza on 2008-02-16
Personally, I give 15 GB to Windows and Ubuntu, create a large NTFS partition for them to share data, and a 512 MB swap partition.

You can shrink the Windows partition (after defragging and backing up) and create the new ones with GParted.

---

### Post by armitage shanks on 2008-02-16
Thanks so shrink windows to 15 gb create an ext of 15 gb and then swap of 512mb the rest as NTFS. Have I got that right please?

---

### Post by kagashe on 2008-02-16
> **armitage shanks said:**
> Thanks so shrink windows to 15 gb create an ext of 15 gb and then swap of 512mb the rest as NTFS. Have I got that right please?Yes, that is what LaRoza means.

kagashe

---

### Post by LaRoza on 2008-02-16
> **armitage shanks said:**
> Thanks so shrink windows to 15 gb create an ext of 15 gb and then swap of 512mb the rest as NTFS. Have I got that right please?

It doesn't have to be 15 GB, it can be bigger. I just use 15 each because that is big enough, but small enough not to waste space.

The Linux partition should be in EXT3 when you format it. You don't have to format it when you make it, you can do that during the install.

---

