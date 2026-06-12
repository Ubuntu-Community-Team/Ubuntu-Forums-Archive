---
title: "I have a friend interested"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-03-13
I've got a friend who is downloading the live disk right now and reading a few "Is ubuntu right for you guides" and I've seen the following posted but haven't looked into it myself but if you set up a dual boot, can you retrieve media from your windows partition while linux is running?

---

### Post by jbayone on 2007-03-13
Yes, as long as the drive is mounted, which it should be available once ubuntu is installed.  Writing to an NTFS partition is still all wonky, but there are ways around it.

---

### Post by euler_fan on 2007-03-13
I have heard of it being done, and of it also being VERY touchy (windows does not like it much at all).

The best thing is to back-up any files you might want to keep, completely re-install from scratch, and then make a fat32 partition to move files back and forth between linux and windows. This is the safest way to do it, so far as I know.

I usually just put files I want to move on my flash drive, which amounts to the same thing.

If they want to do this, I would also look at guides to partitioning hard drives in order to make sure it is all done to spec, as it will probably require manual partioning.

Hope that helps

---

### Post by nalmeth on 2007-03-13
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

This will be read only, but you will have access to the files.
If you (or your friend) wants to take the risk with NTFS write capability, look into ntfs-3g

Remember to tell your friend to defrag Windows +1 times before shrinking Windows and installing Ubuntu.

Backing up data is ALWAYS a smart idea, whether you're installing a new OS or not.

---

### Post by siciliancasanova on 2007-03-13
Thanks for the quick replies everybody!

---

