---
title: "[SOLVED] Got a problem"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by jfd on 2007-11-30
I tried to install something in the terminal and got this:

*E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.*

So I ran it, and I got this:

*dpkg: requested operation requires superuser privilege*

So in the terminal i typed *su*, to become superuser, and typed in my password and got this:

[I]su: Authentication failure
Sorry.[/I]

But i'm the first ever user that was created on the install of ubuntu.

Can anybody help?

---

### Post by Duck2006 on 2007-11-30
Try

> sudo dpkg --configure -a.

---

### Post by thelatinist on 2007-11-30
The root account is locked in ubuntu.  Use sudo to run the command:

```
sudo dpkg --configure -a
```

This will run the command as root from within your account.

---

### Post by jfd on 2007-11-30
Yeah I used that and it fixed the problem, thanks :)

---

### Post by thelatinist on 2007-11-30
> **jfd said:**
> Yeah I used that and it fixed the problem, thanks :)

Great!  Now you should edit your first post to add [SOLVED] at the beginning of the title.

---

### Post by jfd on 2007-11-30
Done ;)

---

