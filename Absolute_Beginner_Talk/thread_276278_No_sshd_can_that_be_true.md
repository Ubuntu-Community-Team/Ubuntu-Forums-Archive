---
title: "No sshd can that be true?"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by redbull_monsta on 2006-10-12
erm having installed ubuntu 6.06 on both my desktop PC's im surprised to find no ssh daemon running... and i cant apt-get or apt-cache search it either.... finds nothing apart from open ssh client

Help!!!  where is sshd

---

### Post by Iarwain ben-adar on 2006-10-12
Hi,
try this
```
sudo aptitude install openssh-server
```

That should do the trick :D


Iarwain

---

### Post by taurus on 2006-10-12
It's opensshd...  And if you are not sure the exact name of a package, fire up synaptic and use the Search function.  If you type in "sshd" in the Search field, it will display all the packages related to sshd.

---

### Post by redbull_monsta on 2006-10-12
Ahhhhh thats better :KS 

Thank you, i knew it must be user error :-D

---

### Post by redbull_monsta on 2006-10-12
> It's opensshd... And if you are not sure the exact name of a package, fire up synaptic and use the Search function. If you type in "sshd" in the Search field, it will display all the packages related to sshd.

I trid that and got nothing... i even added universe and backport back to my sources, hence the confussion

All fixed now - cheers

Oh and it has to be said this forum rox tbh!

---

