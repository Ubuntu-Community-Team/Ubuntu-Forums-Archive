---
title: "ext3 with universal permissions?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Zalbor on 2007-05-07
I want to ask if something I have in mind is possible...

I'd like to have an ext3 partition (or just a directory in an ext3 partition), in which every file will have the same permissions. But not have to manually change the permissions for each new file or directory I put there; I'd like to make it so that every file placed there will automatically have its owner and/or permissions changed.
Can this be done?

---

### Post by Cypher on 2007-05-07
You can set the permissions on a given partition/directory by using [umask]("http://en.wikipedia.org/wiki/Umask"). As far as owner goes, that is usually by default attached to the person creating the file.

---

### Post by Zalbor on 2007-05-07
So if I make an ext3 partition, and mount it with "umask=000" every file in it will be accessible to everyone?

---

### Post by Cypher on 2007-05-07
Righto, you can set that up in your /etc/fstab file. Though, normally you'd want to use 022 which would result in a "755" which is owner:everything, group:read/execute and world:read/execute..

---

### Post by Zalbor on 2007-05-07
Thanks!
I think I'll use something like 002 then, because the whole reason for this is that I want the partition completely accessible by every user, or at least by everyone in a group.

---

