---
title: "I can't log on to samba via windows"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by G_force on 2007-01-04
Hi

When i double click on ubuntu samba located in the workgroup it prompts me for a username and password

when i enter my username and password the prompt flicks and highlight the password

---

### Post by enopepsoo on 2007-01-04
You may need to use Machine\User as the username, instead of just the username.;)

---

### Post by G_force on 2007-01-04
it has the machinename/username and asks for my password yet it is still incorrect

---

### Post by Zzl1xndd on 2007-01-04
im having the same problem have yet to find a soultion. tried more than a few things.

---

### Post by G_force on 2007-01-04
yeah me too
annoying or what
so close, yet so far

---

### Post by pebo on 2007-01-04
Are you using smbpasswd for authentication?

---

### Post by G_force on 2007-01-04
i dont know what your talking bout mate could u elaborate

---

### Post by pebo on 2007-01-05
On the server you add a samba password for each user:
```
sudo smbpasswd -a [username]
```
then you will be prompted to input a password. 
On the client machine you use this samba password, not your user password.
hth

---

### Post by G_force on 2007-01-05
cheers mate your a legend

---

### Post by Zzl1xndd on 2007-01-05
> **G_force said:**
> cheers mate your a legend

I take it that it worked i cant test it right now as my roommates are sleeping but heres hoping,

---

