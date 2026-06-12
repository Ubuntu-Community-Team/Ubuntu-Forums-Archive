---
title: "Setting up Folder Structure?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by CYD on 2006-07-10
I have 3 hard drives...installed.
ubuntu is installed on one drive and it is mounted at / and has the swap etc...

I added the 2 other hard drives after installing ubuntu 6.06.

I read a thread somewhere around here and used gparted to repartition the 2 new hard drives.  Now about getting them into fstab...where *should* I mount them?

When I mounted an NTFS windows drive temporarily in the past, I read to put it under /media/windows

Some other n00b just mounted it off root "/80gb" based off the size of his hard drive.

What is the classical folder structure for a system with multiple hard drives as in where are they typically mounted?

I see an empty folder called "/mnt" perhaps in there?

I am sure from a functional standpoint, the drives could probably be mounted anywhere..I think I understand that, but I want to follow the norm and see if there were any standards or what might designate where to mount the drives.

Thanks,

~CYD

---

### Post by nalmeth on 2006-07-10
I'd recommend throwing them in /media

---

### Post by scxtt on 2006-07-10
you can mount them anywhere you want (but not somewhere off the / F/S that already exists - /var, /home, etc.) -- ubuntu (or debian) likes to use the /media structure for non-root F/S, i'd stick w/ that as it'll give you nice usage of your "places" menu ...

---

### Post by mcduck on 2006-07-11
I believe the 'traditional' way would be to mount removable drives in /media (automounting handles that for you) and others in /mnt. This is how I always do it.

I think that drives mounted in /media will show in Places-menu, whereas those in /mnt will not.

---

