---
title: "How do I setup partitions on my G4?"
date: 2007-01-02
forum: Apple PPC Users
---

### Post by Lend27 on 2007-01-02
I want to install Ubuntu on my Ibook G4.
I have a 40 gig drive with 1 OSX partition. 6 gig is unused.
When I booot from the Ubuntu 6.10 CD, It won't install on freespace for obvious reasons. (There is none).  Using manual partitioning I can resize the OSX partition to leave 6 gig freespace. I want to make sure I do it right. Do I have to create 3 partitions out of that freespace?  1 for swap, one for root, one for boot?

Any help is appreciated.


Thanks
Len

---

### Post by linear on 2007-01-02
> **Lend27 said:**
> Do I have to create 3 partitions out of that freespace?  1 for swap, one for root, one for boot?

No, it's easiest to leave it as one big chunk and let the installer create the partitions automatically.

---

### Post by wannabecanuck on 2007-01-08
I'm running into the same problem.  I allocated 4 GB for my ubuntu partition but the following step in the installer was not clear as to what to do.  I abandoned the install to read up on what the appropriate action is.

I went back into the install process and now the 4 GB partition appears to be inaccessible.

---

### Post by juart on 2007-01-08
The following worked for me.

After booting from the CD you choose as required:
language
location
keyboard
detect hardware (automatic)
scanning CDrom (automatic
loading installer components (automatic)
detecting network (automatic)
configuring network (automatic)
enter hostname (you enter a name here) 
detecting disks and hardware (automatic)
start partitioner (automatic)

partition disks screen - select manually edit partition table then scroll to the partition you wish to use which I believe in your case is the 4 gig partition then hit return (be careful to select the correct partition here). Then select delete the partition. This should now show as FREE SPACE.
Select the FREE SPACE and hit return then select automatically partition free space. The partitioner will do the rest and create the appropriate 3 partitions for boot, swap, and /.

You should then select finish partitioning and write changes to disk. Installion should then procede to completion. Let us know if this works.

Good Luck,
juart

---

