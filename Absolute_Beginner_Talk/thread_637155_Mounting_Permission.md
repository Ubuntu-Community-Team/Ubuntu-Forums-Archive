---
title: "Mounting Permission"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by sooqing on 2007-12-10
When I am on Ubuntu LiveCD, how do I mount my ext2 drive, which has a distro installed, such that I can access the home directory of a user using GUI instead of via CLI?

I can do that if I first change my root password, then su to root, but I still cannot see it in GUI. Another way is to chown -R and change the ownership of all the files but I do not want to damage the ACL, since I still want to boot into it. A third way is gksu "file manager".

Surely there are more elegant ways of doing this at the mounting stage than the above solutions?

---

### Post by The Cog on 2007-12-10
gksu nautilus (or kdesu dolphin) is the method I use. I think getting a GUI as the userid of the user on the hard disk might be quite difficult.

---

