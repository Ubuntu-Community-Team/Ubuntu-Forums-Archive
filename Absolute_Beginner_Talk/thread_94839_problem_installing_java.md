---
title: "problem installing java"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-11-25
Hi i just installed java using the method indicated on the ubuntu 5.10 starter guide that is located in system>help

when I enter the command:
dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb

I get the following message:

dpkg: requested operation requires superuser privilege

What should I do?  I thought that I was a superuser since I installed ubuntu on my laptop.

---

### Post by Xian on 2005-11-25
Use 'sudo' in front of that command:

$ sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb

---

