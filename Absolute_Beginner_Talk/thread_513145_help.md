---
title: "help"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by rasesh_raz on 2007-07-30
i am not able to give apt-get command its giving the following error [root@ashwin ~]# apt-get install linux-tree
bash: apt-get: command not found

---

### Post by Vague on 2007-07-30
> **rasesh_raz said:**
> i am not able to give apt-get command its giving the following error [root@ashwin ~]# apt-get install linux-tree
bash: apt-get: command not found

I responded to your other post, as well, but I'll respond in basically the same way here.  The fact that you have a root console up suggests to me that you probably aren't using Ubuntu.  What distro are you using?

---

### Post by rasesh_raz on 2007-07-30
m using fedora 6.0

---

### Post by hammad1337 on 2007-07-30
try > yum install linux-tree

---

### Post by Vague on 2007-07-30
> **rasesh_raz said:**
> m using fedora 6.0

Yeah, that's your problem.  Fedora doesn't include apt.  By default it uses RPM for package management.  You can get apt working in Fedora, but I'm not really sure on the details.  Just as a suggestion, you'll probably find better support for Fedora at a forum specifically geared toward it, as you'll find a lot more Fedora users there.

(Edit: Oh yeah, forgot about yum.  Heh, shows what I know.)

---

### Post by rasesh_raz on 2007-07-30
thanks a lot man actually i am trying to recompile my kernel i dont have net facility at home and was just trying it  in college lab on fedora will do the apt thing at my place later will need your help later for sure

---

