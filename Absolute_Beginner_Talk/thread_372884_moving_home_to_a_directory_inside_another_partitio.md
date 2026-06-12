---
title: "moving /home to a directory inside another partition"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Shukapi on 2007-02-28
Hi.

I planned my partitions such that I would have a partition (sda4) as /my. I want this partition to contain my home directory AND some other directories.

So I want the path to home to be /my/home.

However I didn't really consider how I would do this. I read the posts about moving /home to another partition, but that simply uses mount (fstab) to link /home to the entire partition.

Is this possible?
Do I need to make a hardlink or softlink as /home that points to /my/home?
Will this cause any problems?

Thanks for your help.

---

### Post by mac.ryan on 2007-02-28
> **Shukapi said:**
> Do I need to make a hardlink or softlink as /home that points to /my/home? Will this cause any problems?

I did this on a friend' computer a couple of weeks ago and not having heard from her yet, I assume it works ok. You cannot do an hard link between different partitions, so the only chance I found was a soft one (I am not a linux guru, though...).

---

