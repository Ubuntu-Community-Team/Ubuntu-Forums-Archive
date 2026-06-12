---
title: "Can you automate sudo commands?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Davidknight24 on 2007-04-29
Hi, I'm learning the ropes of the bash shell, still Day 1, please be gentle ;)

Anyway, I'm trying to run a shutdown command in the background after a short wait using the sleep command, eg:

```
(sleep 10 ; sudo shutdown now) &
```

Good so far? Problem, after 10 seconds, it asks for the password. How do I get around this?

---

### Post by Pobega on 2007-04-29
Edit the /etc/sudoers file and add a line like (I'm working from memory, so I may be wrong)

YOURACCOUNT  ALL=(ALL)NOPASSWD: /sbin/shutdown

And change that command to:

(sleep 10 ; sudo /sbin/shutdown now) &

---

### Post by Davidknight24 on 2007-04-29
> **Pobega said:**
> (sleep 10 ; sudo /sbin/shutdown now) &

That works cheers, but why the /sbin before the shutdown command?:confused:

---

