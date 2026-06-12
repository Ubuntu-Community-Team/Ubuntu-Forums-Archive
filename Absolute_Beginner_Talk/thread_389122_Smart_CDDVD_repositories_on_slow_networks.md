---
title: "Smart CD/DVD repositories on slow networks"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by dluciv on 2007-03-20
I have DVD with a couple of packages and very slow (modem) network connection. Although I have enabled universe and multiverse repositories and keep available package lists up to date.

When I choose to install something, it often depends on some new packages and it tries to load almost everything from internet repositories. In the most cases I will be satisfied with previous version on my CD.

Is there any tool (I have missed some existing functionality posibly) that provides list of possible complete solutions when requiring packages to install? If it does exist, I can choose between out-of-date package versions and high netwrk traffic.

Examples:
1.
I have
app1-ver1 depending on lib1-ver1 on CD
and
app1-ver2 depending on lib1-ver2 on net
so it should show me alternatives when installing app1.

2.
I have
app1 on net, depending on lib1-ver1.*.
and
lib1-ver1.1 on CD and lib1-ver1.2 on net.
it also should ask me if I am satisfied with lib1-ver1.1 from my CD or I prefer to download lib1-ver1.2.

---

### Post by zvacet on 2007-03-21
In synaptic>package>mark version you want>lock version

---

