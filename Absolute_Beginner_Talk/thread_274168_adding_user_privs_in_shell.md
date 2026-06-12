---
title: "adding user privs in shell"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by fnordportland on 2006-10-09
how do i add user privs to an exsisting user in a shell?

---

### Post by bswilson on 2006-10-09
> **fnordportland said:**
> how do i add user privs to an exsisting user in a shell?

The privileges you see in the Ubuntu graphical *Users and Groups* tool are managed by group membership.  You can add a user or remove a user from a group or set of groups with the **useradd/groupadd/usermod/groupmod** commands.  Check the man pages for the right syntax.

---

