---
title: "Installation / User Problem"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-08-18
When I try to run a program or install a program using the terminal, I get the following error:

[i]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/i]

What is the problem here, and how can I change to root?  It is by default alex@ubuntu (my username).

Thanks for your help.

---

### Post by xmastree on 2005-08-18
Root account is disabled by default.
You have two options.
Either:
 use Applications > System Tools > Root Terminal, (you will be asked the password, use the same one as you use for regular login)

Or:
type 'sudo' before any command. Again, you will be asked for the password.

---

### Post by amcavoy on 2005-08-18
Great.  Thank you.

---

