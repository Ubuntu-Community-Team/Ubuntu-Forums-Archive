---
title: "Friend having a problem installing Ubuntu. Help please X]"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Zaosyn on 2007-04-27
I talked my friend into getting Ubuntu, but he's ran into problems.


Firstly; He has two hard drives, one 120 gigs, the other 80 gigs:

Here's a bit of our conversation:

> (04:00:12 AM) dustinnnnn: let me finish insalling
(04:00:15 AM) dustinnnnn: can i install while talking
(04:00:16 AM) Tyler: kk
(04:00:24 AM) Tyler: pretty sure :-?
(04:00:28 AM) Tyler: yeah
(04:00:30 AM) Tyler: I believe so
(04:01:07 AM) dustinnnnn: wtf
(04:01:11 AM) dustinnnnn: i highlight the one i want
(04:01:12 AM) dustinnnnn: and it says
(04:01:24 AM) dustinnnnn: no root file system is defined?
(04:01:30 AM) Tyler: on the side
(04:01:33 AM) Tyler: does it give options likke
(04:01:36 AM) Tyler: "/"
(04:01:46 AM) dustinnnnn: says
(04:01:58 AM) dustinnnnn: /dev/sda5   ext3   /mediasda5 
(04:02:12 AM) Tyler: Is there 2 boxes
(04:02:21 AM) Tyler: If I remember
(04:02:21 AM) dustinnnnn: my 120 gb
(04:02:23 AM) dustinnnnn: and my 80gb
(04:02:24 AM) Tyler: you check the partition one
(04:02:34 AM) Tyler: YOur 30 gig one ain't on there :-s
(04:02:36 AM) Tyler: It might mean
(04:02:38 AM) Tyler: which hard drive
(04:02:40 AM) Tyler: you want it to dual boot on
(04:02:58 AM) dustinnnnn: i choose first one in list
(04:03:03 AM) dustinnnnn: no root file system is defined still
(04:03:15 AM) Tyler: Can you take an SS :-?
(04:03:22 AM) dustinnnnn: i unno

If you can draw something from our conversation, can you please help?

---

### Post by seshomaru samma on 2007-04-27
ask your friend to boot from the live cd and paste the output o the coammnd :
```
sudo fdisk -l
```

---

### Post by petersjm on 2007-04-27
If your friend is manually partitioning, he needs to select the / (and /home if he's got a separate partition for that) in the installer. I used QTParted for Kubuntu, so not sure about GParted in Ubuntu, but QTParted gave me dropdown options for / and /home. Select them against the partition or drive you want, and that should do the trick. I'd imagine GParted in Ubuntu will be roughly similar?

---

