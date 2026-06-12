---
title: "[SOLVED] Browser Settings for Squid"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-12-23
I am finding that normal desktop users cannot access the squid proxy whereas administrator users logging in on the same machine have zero problem.  This seems to suggest that the ACL is working and the problem must therefore be at the client.

How do I fix this?  I thought there may be a global setting for the machine but I cannot figure out what this is ....

---

### Post by expatCM on 2007-12-24
This is now solved.  I found two problems - a small typo on the port number used and the need to update host ip of the server in the hosts file on the client.

---

