---
title: "removing completely ubuntu"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by jnw222 on 2008-04-20
how do you completely remove ubuntu and all related programs and restore xp without a reintsall cd

---

### Post by will1911a1 on 2008-04-20
> **jnw222 said:**
> how do you completely remove ubuntu and all related programs and restore xp without a reintsall cd

It's gonna be tough to reinstall XP if you don't have a disc.

---

### Post by sayakb on 2008-04-20
You might need to remove Grub and for that, you need a XP setup CD. First, simply boot in the XP Setup disk and enter recovery mode by pressing R. Then do:
```
fixmbr
fixboot
```
Now you would boot in straight to XP (in case you already have it installed). Then right click on My Computer and click Manage. Click Disk Management and delete the Ubuntu partition from there.

---

### Post by the8thstar on 2008-04-20
If your XP partition is still accessible (is it?), log into it. Then you can run fixmbr and fixboot from a regular command prompt.

---

### Post by jnw222 on 2008-04-20
xp works so just launch 
fixmbr
fixboot 

from command line and 
go to disk managment then delete ubuntu partition

---

### Post by sayakb on 2008-04-20
> **the8thstar said:**
> If your XP partition is still accessible (is it?), log into it. Then you can run fixmbr and fixboot from a regular command prompt.

Can he? I suspect :confused:

---

### Post by the8thstar on 2008-04-20
> **jnw222 said:**
> xp works so just launch 
fixmbr
fixboot 

from command line and 
go to disk managment then delete ubuntu partition

Exactly. That's the easiest way buddy.

---

### Post by sayakb on 2008-04-20
Wow.. I thought that one can fixmbr from the CD only. Thanks for the info.. :)

---

