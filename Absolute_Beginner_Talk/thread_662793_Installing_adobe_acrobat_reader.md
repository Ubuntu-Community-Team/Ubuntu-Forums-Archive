---
title: "Installing adobe acrobat reader"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by EnergySamus on 2008-01-09
Hello! I am installing Adobe Acrobat Reader through the terminal. I am at a part where the installation tells me to enter a installation directory. What is the directory?
I am sort of new at the terminal!:lolflag:

EnergySamus

---

### Post by philinux on 2008-01-09
Its in synaptic

acroread

just mark it for installation

System>Admin>Synaptic

---

### Post by santiagoward2000 on 2008-01-09
> **philinux said:**
> Its in synaptic

acroread

just mark it for installation

System>Admin>Synaptic

Not exactly... You'll need to add the [Medibuntu]("http://www.medibuntu.org") repository to find it in Synaptic.

---

### Post by EnergySamus on 2008-01-09
Thanks! But it isn't in there!!!

---

### Post by philinux on 2008-01-09
> **santiagoward2000 said:**
> Not exactly... You'll need to add the [Medibuntu]("http://www.medibuntu.org") repository to find it in Synaptic.

Good pickup there.

---

### Post by Niniel on 2008-01-09
Why install Acrobat? There are some nice open source readers around. :)

---

### Post by santiagoward2000 on 2008-01-09
You'll need to add the Medibuntu repository. Just open a terminal and do:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
This is for Gusty.
Cheers!

---

