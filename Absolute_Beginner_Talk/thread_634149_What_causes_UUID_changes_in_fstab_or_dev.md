---
title: "What causes UUID changes in fstab or /dev?"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by bhold on 2007-12-07
Twice now I have had unexpected changes to the UUID= values in /etc/fstab or under the /dev directoryb. First time I noticed it was on boot a while back - got an error message about a non-existant UUID value. When the system came up, sure enough, fstab was out of sync with the uuid entries under /dev. Second time (just noticed it last night) was that my swap partition used to be associated with a UUID, but now that has been removed...
blkid command shows this entry for swap with no UUID...
/dev/sda3: TYPE="swap"
/etc/fstab has this entry for swap...
UUID=a8282f99-3008-4359-b551-07fa2bc9f41d none            swap    sw 0 0

I fixed the problem by removing all the UUID= entries from fstab, replacing with the /dev path information instead. I don't need the UUID stuff because I'm  not removing / replacing disk media on my desktop system.

So this is a question of just trying to understand how this works - what operations can cause changes to UUID - either entries under /dev, or in fstab?

I run Ubuntu 7.10 as my primary distribution with one or two other linux distributions installed in separate partitions. So occasionally I am doing some re-partitioning using Gparted live cd. Maybe that has something to do with it but I have never seen any UUID information displayed in Gparted so not sure about that.

---

### Post by lamalex on 2007-12-07
Yeah, the partitioning is what is causing the changes of UUID, the UUID comes from some filesystem information, so when you change the partitioning, the UUID changes. gparted doesn't display UUID info, I think they're currently debating this though.

---

### Post by bhold on 2007-12-08
Thanks lamalex I suspected maybe the gparted operations had something to do with the uuid changes.

Regarding system software that manipulates /etc/fstab or manipulates UUID subdirectory names under /dev/...
I don't think the uuid syntax makes much sense in fstab on a desktop system, isn't the purpose of this to facilitate removing or adding a large number of disk devices? Maybe good for server systems, but on the desktop why implement a feature that causes confusion, requires occasional repair, and adds little or no value? 

 My 2 cents worth.

---

### Post by louieb on 2007-12-08
I've had the uuid change by formating an existing partition.  In this case I was just clearing out an existing ext3 partition. On reboot had to fix the uuid in /etc/fstab.  
> but on the desktop why implement a feature that causes confusion, requires occasional repair, and adds little or no value? 
:KSNicely said.

---

