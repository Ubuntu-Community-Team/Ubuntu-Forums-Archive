---
title: "[SOLVED] Administration"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by kingdogbert on 2007-10-21
So when I installed Ubuntu, the first thing I did was remove admin privileges for my normal account (for security, of course). But now I can't figure out how to admin the computer. I can 'su' from a terminal, but I don't know the programs to run, so that's not helping. What's the trick? Thanks in advance

---

### Post by Pumalite on 2007-10-21
Ubuntu does not grant you administrative privileges, except temporarily through the 'sudo' command in Terminal

---

### Post by jd65pl on 2007-10-21
What admin tasks are you trying to perform?

---

### Post by aysiu on 2007-10-21
You want those *admin* privileges back. Here are instructions for getting them back:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

When you have *admin* privileges, you operate as a regular user almost all the time. It's only when you try to accomplish an administrative task that you'll be asked for a password in order to temporarily escalate your user privileges.

---

### Post by kingdogbert on 2007-10-21
I figured it out for myself :)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thanks for the replies

---

### Post by bodhi.zazen on 2007-10-21
> **aysiu said:**
> You want those *admin* privileges back. Here are instructions for getting them back:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

When you have *admin* privileges, you operate as a regular user almost all the time. It's only when you try to accomplish an administrative task that you'll be asked for a password in order to temporarily escalate your user privileges.

One step ahead of me today aysiu is ...

---

