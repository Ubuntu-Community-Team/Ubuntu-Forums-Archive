---
title: "how to remove plain text passwords?"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by tux21 on 2006-07-19
how do i  remove plain text passwords from file /etc/ppp/chap-secrets? i don't want to reveal my login .

---

### Post by mlind on 2006-07-19
> **tux21 said:**
> how do i  remove plain text passwords from file /etc/ppp/chap-secrets? i don't want to reveal my login .

AFAIK /etc/ppp/chap-secrets does not support encrypted passwords. You should probably look in pap-secrets and flag called *papcrypt*.

---

