---
title: "Can not resizepartition with Gparted"
date: 2012-01-15
forum: Any Other OS
---

### Post by deepakdeshp on 2012-01-15
I am using Mint12 and df -k shows 9 percent  usage. But when I try to resize it, it is greyed out even though my boot partition isnt mint.

---

### Post by nothingspecial on 2012-01-15
Moved to Other OS/Distro Talk.

---

### Post by drs305 on 2012-01-15
Depending on where the partition is on the disk, other partitions may need to be unmounted as well. Generally I find it easiest to do partitioning from a LiveCD, but even then you will have to unmount the swap partition before accomplishing the resizing operation(s).

And don't forget to backup important data before accomplishing any disk partitioning.

---

### Post by Double.J on 2012-01-15
> **drs305 said:**
> Depending on where the partition is on the disk, other partitions may need to be unmounted as well. Generally I find it easiest to do partitioning from a LiveCD, but even then you will have to unmount the swap partition before accomplishing the resizing operation(s).

**And don't forget to backup important data before accomplishing any disk partitioning**.

+1

Usually greyed out means that the partition is currently mounted, and you right click > unmount to get access to it; this can often happen if you've opened the filesystem in the file manager to see what's on it? As drs305 says, you may also need to swap off, again - right click and swapoff. 

I also advise using a live CD - it gives you full access to the drive. Just remember the golden rule - whenever you do any partitioning - back up everything on that device - it's really not worth the hassle of not! :)

---

### Post by deepakdeshp on 2012-02-16
> **gnu/mirow said:**
> +1


I also advise using a live CD - it gives you full access to the drive. Just remember the golden rule - whenever you do any partitioning - back up everything on that device - it's really not worth the hassle of not! :)


Thats a very sound advise about backing up. And thank you for the other details too.

---

