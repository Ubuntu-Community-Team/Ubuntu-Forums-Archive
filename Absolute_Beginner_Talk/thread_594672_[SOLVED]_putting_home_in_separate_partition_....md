---
title: "[SOLVED] putting /home in separate partition ..."
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-28
After reading the advice to put /home in a separate partition, I can understand that wisdom.

Well, I did create me a partition for /home -- /dev/sdb4

I booted the live CD and copied my /home data to the new partition using:  cp -a * /dev/sdb4

Copied data looked good.

Then I put the following entry at the bottome of  /etc/fstab:

#MOUNT MY HOME DIRECTORY IN PARTITION:  /dev/sdb4
#------------------------------------------------
/dev/sdb4       /home  ext3  nodev,nosuid 0 2



But, when I reboot, /home does not get mounted.  To get in Gutsy, I had to go to terminal mod and mount the partition, then alt+F7 to get the Gnome login -- then I could successfully log in.

Why is my /home not getting my new partition mounted on it?

Thanks

Carl

---

### Post by philinux on 2007-10-28
hi moser, can you post your full fstab please.

---

### Post by eldepeche on 2007-10-28
Is the /home directory on your root partition empty? You can't mount a drive on a nonempty directory.

---

### Post by cwmoser on 2007-10-28
Thanks for the help.   Eldepeche recommendation was the problem - I had an empty directory in the mount directory.  Thanks

There are so many little things that can go wrong and I appreciate all the help you guys are giving.
This forum is what makes Ubuntu great and the reason this old Windows user is able to convert to Linux.  Thanks again.

Carl


> **eldepeche said:**
> Is the /home directory on your root partition empty? You can't mount a drive on a nonempty directory.

---

