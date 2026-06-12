---
title: "[SOLVED] Partition problems when installing ubuntu: Unusable space"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by gs110 on 2007-10-31
I'm trying to install Ubuntu 7.10 off of the live cd, using a dual boot with windows. When I get to the part where you partition the drive, I try to partition space I recently free from my windows partition. After I create one partition (either swap or my main partition) , all of the left over space that I was going to use for my swap or the main partition (whichever I didn't do first), is labeled as unusable. Any idea about why this happens? Thanks.

---

### Post by Inxsible on 2007-10-31
> **gs110 said:**
> I'm trying to install Ubuntu 7.10 off of the live cd, using a dual boot with windows. When I get to the part where you partition the drive, I try to partition space I recently free from my windows partition. After I create one partition (either swap or my main partition) , all of the left over space that I was going to use for my swap or the main partition (whichever I didn't do first), is labeled as unusable. Any idea about why this happens? Thanks.
Are you trying to dual boot ?

What other partitions (most likely windows) do you have ?

Remember, you can have at max 4 primary partitions. You can create Logical partitions and install Ubuntu in them. Unlike Windows, Ubuntu can be installed in extended/logical partitions.

---

### Post by gs110 on 2007-10-31
Yes, I used a logical partition for it and the extra space is usable, thanks.

---

