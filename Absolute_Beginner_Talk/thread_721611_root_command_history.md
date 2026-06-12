---
title: "root command history"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by bprof on 2008-03-11
Hello,

I have two users using the same server as root, is there a way to see the history of commands both used?

Thank you,

---

### Post by kellemes on 2008-03-11
Not sure if this is what you mean..

~/.bash_history shows the history of commands

---

### Post by Oldsoldier2003 on 2008-03-11
> **bprof said:**
> Hello,

I have two users using the same server as root, is there a way to see the history of commands both used?

Thank you,

if you mean they are sudoers with root permissions, you can look in /var/log/auth.log the commands they issue will be logged there...

---

### Post by justleen on 2008-03-11
and if you mean both users are actually root, then all you'd be able to tell from your logs is when person A and B logged on, but you cant tell any more (once both they are both logged in and typing commands) who issued which command.

---

### Post by bprof on 2008-03-11
Thank you everyone, specially kellems, thats exactly what I wanted.

---

