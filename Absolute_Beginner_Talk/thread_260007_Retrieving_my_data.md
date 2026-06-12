---
title: "Retrieving my data"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2006-09-18
I see lots of threads that say that its a good idea to have at least the /home folder on a seperate partition in case you mess up your system. 

Well I had the following partitions on a safe drive:
/
/home
/var
/usr

I messed up my system and now I want to retrieve my data from a safe backup disk where the above partitions sit. I reinstalled my installation, but now how do i get my original files back? A simple copy don't do it. For example: I have four users in /home, but copying their folders to the new home, won't give me a logon for them.

Any help getting my old partition info to override the new ones?

---

### Post by MrHorus on 2006-09-18
> **GrootBrak said:**
> I have four users in /home, but copying their folders to the new home, won't give me a logon for them.

Any help getting my old partition info to override the new ones?

Add the user accounts with the same naem so the OS sets up /home dirs for them and they have logon shells.

THEN copy the data over :)

---

### Post by GrootBrak on 2006-09-18
Will try it.

But how do I get all my data back from all the other partitions (mount points?) I prefer to do it in one go. Later on I need to buy a bigger hard disk, because my install hangs as soon as I add the second disk, I can only add it after a sucessfull install.

---

