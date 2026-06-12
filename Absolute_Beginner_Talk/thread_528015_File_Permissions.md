---
title: "File Permissions"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by jflowers on 2007-08-17
I am using my new linux system strictly as a desktop operation, and not as a server.  For security reasons, I am considering removing all permissions (no read, write, or execute) to the "others" group.  Could this create a problem with my system?

Thanks

---

### Post by aysiu on 2007-08-17
Yes, it could create a problem.

The proper operating of your system is based off permissions. If you don't know what you're doing and just change permissions *en masse*, you will likely render your system unusable.

---

### Post by kwilliam on 2007-08-23
Aysiu, could you give some more details?  I am also considering the same thing, but just for files in my home directory.  I'm thinking of creating a "guest" account that I could use to let others try Ubuntu, but I don't want user "guest" to be able to read any of the files in my home directory.  Specifically, most of my home dir files have r-x settings for "other", and I'm wondering if I can recursively change them all (including hidden files) to --- for "other".

---

