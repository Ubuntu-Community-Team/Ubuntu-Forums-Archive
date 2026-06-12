---
title: "No permissions to certain files on ftp for certain users"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by bartkl on 2007-07-07
I'm using the ftp server vsftpd now and everything is working fine.
It's configured for anonymous usage. The /etc/passwd file contains the following line:

ftp: x:110:65534::/mnt/disk/Music:/bin/false
*(what does /bin/false mean?)*

this one's the user 'ftp' which is for anonymous access. 

I have two file extensions I would wish not to be visible to ftp users , so no permissions at all (000).
How can I chmod it that way so only the user 'ftp' has those rights?

Thanks in advance.

---

### Post by bartkl on 2007-07-07
No one?

---

