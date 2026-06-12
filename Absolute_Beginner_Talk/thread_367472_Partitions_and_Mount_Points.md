---
title: "Partitions and Mount Points"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Ewok85 on 2007-02-22
I only used half of my HDD when I installed Ubuntu and want to use the other half.

I've got the partition setup, and can mount it using the mount command, but what do I do to make it stick after a boot?

And I have files in my /var/ folder, but I want to use my second partition.
Am I right in thinking that if I mount partition2 at /var2/ and copy the files from /var/ to /var2/, then mount partition2 at /var/ it will retain the files but be on the larger partition?

---

### Post by Archmage on 2007-02-22
To have the partition mounted after a reboot you need to put them in the file /etc/fstab.

You are right about moving the /var partion, but I would suggest that you boot from a live-cd and do the moving, because files will be modife on the /var-partion while the linux-system is runing.

---

### Post by Ewok85 on 2007-02-22
What if I set the mount point in the fstab, then reboot? that way its automatically overwritten :) 

Would that be OK?

---

