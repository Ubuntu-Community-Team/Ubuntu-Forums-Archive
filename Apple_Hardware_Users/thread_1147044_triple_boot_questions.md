---
title: "triple boot questions"
date: 2009-05-03
forum: Apple Hardware Users
---

### Post by Hume's doona on 2009-05-03
i have an existing dual boot with os x leopard and ubuntu ultimate edition.

at the moment, the UE partition is 80 gig. i want to resize this to be around 125gig and be occupied by jaunty jackalope, and add a windows partition of about 20-30 gig, leaving my os  partition in tact and about 100gig

do i just resize using bootcamp, making the os x partition 100gig, then install jaunty with manual partitioning [wiping UE], then install windows in the free space?

partitions would be:
1: refit
2: os x
3: jaunty
4: vista

can the fifth partition be a swap for ubuntu? and can i have separate home and root partitions but have it still bootable?

[i don't have many important files, but will copy what i have to dvd], i also have os x backed up with time machine

thanks

---

### Post by cyberdork33 on 2009-05-03
> **Hume's doona said:**
> i have an existing dual boot with os x leopard and ubuntu ultimate edition.

at the moment, the UE partition is 80 gig. i want to resize this to be around 125gig and be occupied by jaunty jackalope, and add a windows partition of about 20-30 gig, leaving my os  partition in tact and about 100gig

do i just resize using bootcamp, making the os x partition 100gig, then install jaunty with manual partitioning [wiping UE], then install windows in the free space?

partitions would be:
1: refit
2: os x
3: jaunty
4: vista

can the fifth partition be a swap for ubuntu? and can i have separate home and root partitions but have it still bootable?

[i don't have many important files, but will copy what i have to dvd], i also have os x backed up with time machine

thanks

sounds about right. yes you can have swap, home etc. You just have to make the partition that you actually boot to one of the first 4... ie if you make a separate /boot partition, it will need to be in the first 4 and your root ( / ) partition does not.

See details here
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

