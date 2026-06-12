---
title: "(How do I?)Mount/Access other partitions"
date: 2008-06-14
forum: Apple Hardware Users
---

### Post by WillJeffery on 2008-06-14
I'm trying to access my iTunes library from OS X so I can play all my songs through Amarok. I am able to locate my OS X partition and navigate to my music folder, but I do not have permission to open the Music folder. Halp pls?


Thanks in advance!

---

### Post by cyberdork33 on 2008-06-14
> **WillJeffery said:**
> I'm trying to access my iTunes library from OS X so I can play all my songs through Amarok. I am able to locate my OS X partition and navigate to my music folder, but I do not have permission to open the Music folder. Halp pls?
Ubuntu respects the file permissions set in OSX. Those files do not belong to your Ubuntu user.

You can set the permissions to allow access to all users, or use the Ubuntu root user to copy files from the OS X partition and chown them to your Ubuntu user.

---

