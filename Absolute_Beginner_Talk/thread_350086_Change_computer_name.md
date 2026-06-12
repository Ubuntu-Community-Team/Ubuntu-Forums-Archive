---
title: "Change computer name?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-01-31
Hi,

How do I change my computer name please?

Thanks

---

### Post by linuchsan on 2007-01-31
in /etc/hostname

---

### Post by taurus on 2007-01-31
> **linuchsan said:**
> in /etc/hostname

And you better change it in /etc/hosts with the same name too or you will have a one dead machine, no sudo and no internet.

---

### Post by MrHorus on 2007-01-31
> **taurus said:**
> And you better change it in /etc/hosts with the same name too or you will have a one dead machine, no sudo and no internet.

Would the hostname command not do both of the above?

---

### Post by an.echte.trilingue on 2007-01-31
> **MrHorus said:**
> Would the hostname command not do both of the above?
No.
Neither of the methods mentioned here work.

EDIT: This is how it works:

```
sudo su
vi /etc/hostname
vi /etc/hosts
/etc/init.d/hostname.sh start
exit
```

I think you might be able to skip the /etc/hosts part, but I am not sure.

---

