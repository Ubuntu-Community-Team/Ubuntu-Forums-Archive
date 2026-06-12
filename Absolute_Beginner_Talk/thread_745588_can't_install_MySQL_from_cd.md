---
title: "can't install MySQL from cd"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by go_lanche on 2008-04-04
Hey all, I am attempting to install MySQL, Apache and PHP from the cd that came with my new Teach Yourself Apache, MySQL and PHP book from SAMS. When I try to install I get this message and can not get around it.

ck@rig:/usr/local$ gunzip < /mnt/MySQL/Linux/tarballs/source/mysql-5.0.20.tar.gz | tar xf -
bash: /mnt/MySQL/Linux/tarballs/source/mysql-5.0.20.tar.gz: No such file or directory
ck@rig:/usr/local$ 

I would appreciate any help on this topic, I am very new so please feel free to point out anything minor that I may have missed. Thanks for the help.

---

### Post by annda on 2008-04-04
you can install all the packages from the repositories, it is much easier

System>Administration>Synaptic
Edit>Mark packages by task> LAMP server>OK

---

