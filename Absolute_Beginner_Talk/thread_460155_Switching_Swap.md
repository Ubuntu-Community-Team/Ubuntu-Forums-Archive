---
title: "Switching Swap"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Shmook on 2007-05-31
I've got 4 primary partitions on one HD but now want to install another distribution, so I'm thinking about deleting the swap partition, creating an extended partition and recreating a swap logical part as well as parts for the other OS.

Will I have to change any settings so Ubuntu will use this new swap partition or will it magically know?

Thanks

---

### Post by louieb on 2007-05-31
Your going to have to change your /etc/fstab file to let Ubuntu know what the new swap partition is.

---

