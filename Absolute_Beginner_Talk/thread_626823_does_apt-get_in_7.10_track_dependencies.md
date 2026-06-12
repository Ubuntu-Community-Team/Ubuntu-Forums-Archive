---
title: "does apt-get in 7.10 track dependencies"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by BlocknBleed on 2007-11-29
I thought I read somewhere that Ubuntu modified the apt-get command in the later releases to deal with dependencies. Is this true or should I stick with aptitude?

---

### Post by philinux on 2007-11-29
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Tristam Green on 2007-11-29
if you're talking about apt-get uninstalling the dependent packages at the same time as a normal uninstall, it appears so.  sudo apt-get remove package seems to work as well as sudo aptitude remove package from terminal.

the only difference is i feel i have to autoremove old packages more with apt-get than i do with aptitude.

---

### Post by BlocknBleed on 2007-11-29
> **philinux said:**
> [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

thanks

---

