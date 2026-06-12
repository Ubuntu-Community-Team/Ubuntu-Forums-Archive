---
title: "Samba Umask"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by gniltaws on 2008-02-14
Is there a way to set different umasks for different users in samba?

I am administering a file server at a college.  A professor wants read/write access to his students files.  I see how to change it for all of the users, but I only want to enable group read/write for selected users.  Is this possible?  Thanks in advance.

---

### Post by spiderbatdad on 2008-02-14
looks like this can be accomplished easily in the profiles portion of smb.conf  Use  the section above profiles to create a net logon service as well. guests will not have rw access. group profiles can be set to rw permissions.

---

