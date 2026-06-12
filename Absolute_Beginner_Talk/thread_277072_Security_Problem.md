---
title: "Security Problem"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by dr_d on 2006-10-13
hi there..

when attempting to ssh into my new ubuntu server, i accidently typed my password when it was asking for my username.

now my password is saved in cleartext in /var/log/auth.log

it's not too much of an issue for me, as i'm the only one with access to that server... but it's far from ideal. just wondering.. how long until that log file gets deleted?

does it ever get deleted? if not what action can i take to remove that entry.

thanks in advance,
dr d

---

### Post by blendmaster on 2006-10-13
edit: Sorry! I read what you said wrong.

---

### Post by blendmaster on 2006-10-13
You could access it with sudo and delete that part.

---

### Post by dr_d on 2006-10-14
Oh good idea... can't belive i didn't think of that.

Cheers.

---

