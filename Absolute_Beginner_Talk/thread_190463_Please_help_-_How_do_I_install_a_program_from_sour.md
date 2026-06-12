---
title: "Please help - How do I install a program from source like &quot;xitami&quot;???"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by luckylucky on 2006-06-06
Hi there,

I would really like to get xitami working within Ubuntu but it's not one of those programs that can easily get installed by Ubuntu's beautiful install feature.

There is source code for install for linux systems at [www.xitami.com](www.xitami.com) which I've downloaded but for the life of me I can't figure out what to do with it.

Caan anyone please give me a pointer to how to learn (for beginer) to install programs from source?  Thank you very much!

Very Lucky

---

### Post by mostwanted on 2006-06-06
Take a look at [http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing) - it walks you through the different methods of installing.

The configure or make step will probably complain that there are missing dependencies. They will probably be in APT so open up Synaptic and look for them. If you find it, make sure to also install the -dev version of it.

---

