---
title: "run scrip when starting a program"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by dragonflyFZX on 2006-12-19
hi,

i need to make a vpn connection before i can use my email.  How do i run a script when i click the evolution icon?

D

---

### Post by bodhi.zazen on 2006-12-19
> **dragonflyFZX said:**
> hi,

i need to make a vpn connection before i can use my email.  How do i run a script when i click the evolution icon?

D

write the bash script, lets call it email

At the end of the script add:

exec /path/to/evolution

on the evolution icon change the command line to 

```
bash /path/to/email
```

---

