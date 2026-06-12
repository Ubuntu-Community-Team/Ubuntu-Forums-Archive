---
title: "System Restore"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by djen9999 on 2007-02-18
I'm pretty sure I know the answer but I want to get a definitive reply before I go anywhere.  I created a dual boot system on a single drive yesterday.  Things got totally messed up.  First I wasn't able to get past the sign in page now I get a complete failure warning.  I was probably messing where I shouldn't be messing.

Can I use my XP's system restore to go back to a time yesterday before I did the partitioning and installation?  My gut feeling is no.

If not, how to I get things back to a reasonable point where I can start all over again?

---

### Post by linux_kid on 2007-02-18
No big deal, just pop in the ubuntu cd and reinstall.  you don't even need to partition agian, your current partitions should be fine.

P.S. You can NEVER be messing where you shouldn't be messing in Linux, because you should be messing everywhere :) :)

---

### Post by Poman on 2007-02-18
> **djen9999 said:**
> I'm pretty sure I know the answer but I want to get a definitive reply before I go anywhere.  I created a dual boot system on a single drive yesterday.  Things got totally messed up.  First I wasn't able to get past the sign in page now I get a complete failure warning.  I was probably messing where I shouldn't be messing.

Can I use my XP's system restore to go back to a time yesterday before I did the partitioning and installation?  My gut feeling is no.

If not, how to I get things back to a reasonable point where I can start all over again?

Hi, I found that it helped to create a new admin user, move over any files while logged in as root, and then as the new admin you can delete the old user.  I don't know the specifics of your problem, but this is how I messed up and restored my settings. From now on I'm not messing with it unless I know what the consequences will be. I would not try XP's system restore, as it won't have any effect on the Linux system.

---

