---
title: "users and groups"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by plewisfdx on 2006-11-27
In System -> Administration -> Users and Groups I added myself to another users group.  The "group settings -> properties" shows a check mark by my name for that group.

At a terminal, when I type:

$ groups

it doesn't list this group as one I am a member of.  Also, when I try to write into a folder that a group member should be able to write to, it has permission errors.

Why does the "Users and groups" say I am a member, if in fact I am not?

thanks,

phil

---

### Post by Bachstelze on 2006-11-27
please paste the contents of /etc/group

---

### Post by plewisfdx on 2006-11-27
Here's the relevant line:

npc:x:1001:phil,npc

This shows phil as a member of npc, but still the same problem.

---

### Post by Arndt on 2006-11-27
> **plewisfdx said:**
> In System -> Administration -> Users and Groups I added myself to another users group.  The "group settings -> properties" shows a check mark by my name for that group.

At a terminal, when I type:

$ groups

it doesn't list this group as one I am a member of.  Also, when I try to write into a folder that a group member should be able to write to, it has permission errors.

Why does the "Users and groups" say I am a member, if in fact I am not?

thanks,

phil

Existing processes are not changed when you change the /etc/group file. You need to log in again, or use "su - yourusername".

---

