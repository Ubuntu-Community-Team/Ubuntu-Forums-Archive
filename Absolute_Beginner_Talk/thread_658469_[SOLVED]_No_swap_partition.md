---
title: "[SOLVED] No swap partition"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by gary0 on 2008-01-04
I have just noticed tonight that I have no swap partition. I have 2 drives - 120 gig system disk and 250 gig home disk. I obviously omitted to set up the swap during installation. Is this a problem? The pc runs fine by the way. If it could cause problems, how do I go about creating a swap partition, and which drive would be the best place to put it?

Gary.

---

### Post by njparton on 2008-01-04
Depends on how much ram you have.

If you have say 2 gig and don't do anything intensive I doubt a swap partition would ever be used.

---

### Post by spydon on 2008-01-04
I have never seen a linux system without a swap but if you have much ram I don't think there will be so much difference. If you want to have a swap partition id say that you shrink the system partition and make a swap.

---

### Post by gary0 on 2008-01-04
I do have 2 gig of ram. No worries then?

Gary.

---

### Post by njparton on 2008-01-04
Yep, should be really easy via gparted and then add an appropriate entry to fstab.

---

### Post by PeterJS on 2008-01-04
If you have enough RAM that you'd never need to use swap then you don't  *need* swap. It's never a bad idea to have some just in case if you plan on doing anything over the top. Here's a guide to adding swap space after the install with out changing your partitions around.

---

### Post by gary0 on 2008-01-04
Thanks guys.

Gary.

---

