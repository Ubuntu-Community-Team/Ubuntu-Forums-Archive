---
title: "[SOLVED] What's my root password?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by sixsidepentagon on 2007-09-17
So I tried to login as su in the terminal, it asked for my password, so I typed in the password I use for all things linux, and it tells me:
me@ubuntu:~$ su
Password: 
su: Authentication failure
Sorry.

Is there a separate root password, or what?

---

### Post by bodhi.zazen on 2007-09-17
[uwiki]RootSudo[/uwiki]

Ubuntu uses sudo

You can set a root password (sudo passwd) or sudo -i

---

### Post by sixsidepentagon on 2007-09-17
Oh, thanks!

---

