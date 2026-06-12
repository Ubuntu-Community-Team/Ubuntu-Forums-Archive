---
title: "am I admin?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-05-08
Plain question: how do I know if I am loggin as the administrator through the terminal command prompt? Thxs CMMM

---

### Post by MRiGnS on 2007-05-08
> **krisfrajer said:**
> Plain question: how do I know if I am loggin as the administrator through the terminal command prompt? Thxs CMMM

<user>@<machine name>:~$

if user = root you are the man!

---

### Post by Bachstelze on 2007-05-08
If you're logged in as a regular user, the prompt ends with a dollar sign :

```
mfb@ana ~ $
```

If you're logged in as root, it ends with a hash :

```
mfb@ana ~ $ sudo -i
ana ~ #
```

---

