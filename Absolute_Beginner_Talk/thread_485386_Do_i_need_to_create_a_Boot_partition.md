---
title: "Do i need to create a /Boot partition?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Delirious on 2007-06-26
I just did a manual partition during my Ubuntu install and created and assigned a partition for / , /var, /temp, and /home. 

After the install the machine boots straight into vista ultimate without even showing Grub. 

Anyway thats not my question (i think ive gathered alot of info to fix that on my own) my question is should i have created a /boot partition as well since i went the manual route? I've googled and searched here and couldnt find anything really that told me what /boot is for and if i need to create it when doing manual partitioning.

---

### Post by Teh Dust on 2007-06-26
/boot is where grub is stored.

When I partition a drive I make 3 separate partitions.

A /boot partition which I set as ext3 because it seems that ext3 is required

A / partition that is XFS and handles all other files

And of course, a SWAP partition.

but as long as you have a / partition then you do not need to wory about anything missed such as /boot

Hope this helped you out.

---

### Post by Delirious on 2007-06-27
> **Teh Dust said:**
> /boot is where grub is stored.

When I partition a drive I make 3 separate partitions.

A /boot partition which I set as ext3 because it seems that ext3 is required

A / partition that is XFS and handles all other files

And of course, a SWAP partition.

but as long as you have a / partition then you do not need to wory about anything missed such as /boot

Hope this helped you out.

Yup that helps thansks :)  Just wasn't sure if /boot is included in the / partition. why XFS and not ext3 for / and not ext3?

---

