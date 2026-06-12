---
title: "Merging partitions"
date: 2006-12-05
forum: Apple PPC Users
---

### Post by galvatron1983 on 2006-12-05
Ive managed to get hold of an old Powerbook G3 that Ive successfully installed Ubuntu on and Im planning on using that as my primary Linux machine from now on. 

Ive deleted Ubuntu from its partition on my macs hard drive along with the swap partition and the yaboot partition. All I have now is my original OS X partition which was shrunk to 83GB to allow space for linux, and thats now become 20GB of unallocated free space. Ive initially tried to reverse the technique I used to create the Linux partition in Parted on the Live CD to give OS X the free space back, but parted wont display the free space from the print command, just the partitions that contain data.

Is there a way I can merge the free space with the OS X partition and get all of my free space back in OS X???

---

### Post by stream303 on 2006-12-05
A quick way would be to use iPartition for the Mac.  It's a very handy utility and you can practice with the demo - it won't actually write any partitions until purchase.

I used iPartition initially when I wanted to dual-boot my Mac and shrank the original.  Expanding it back shouldn't be too hard.

---

