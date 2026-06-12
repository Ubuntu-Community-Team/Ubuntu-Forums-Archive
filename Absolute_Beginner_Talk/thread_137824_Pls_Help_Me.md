---
title: "Pls Help Me"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by vinchuca on 2006-02-28
Hello, i'm from Uruguay, and i'm realy realy newbe, in Linux and Ubuntu. i'm using the version 5.04 dual boot whit Win xp sp2. My problem is to connect the modem (a winmodem obviusly), the modem are a Sis Ac'97, and i have read a lot of forums, and wiki pages, but my problem are i don't know where are my kernel sources.... i search for the directorie a lot but i dont found them

if any one have some help..... 

thnks a lot


I love this comunity

---

### Post by taurus on 2006-02-28
If you have one install, it should be in /usr/src...  

```

ls -la /usr/src

```

However, I doubt if you have a copy of kernel source so you need to install it by using either synaptic or apt-get.  So, fire up synaptic and click on the Search (upper right corner).  At the field, type in kernel and put a check mark in front of the version that you have running right now.  If you're not sure what version you have, this command will tell you

```

uname -a

```

---

