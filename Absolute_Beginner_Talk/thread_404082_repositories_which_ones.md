---
title: "repositories which ones"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2007-04-07
Which repositories should I absolutly have which aren't included?

---

### Post by ardchoille42 on 2007-04-07
> **jbumgar said:**
> Which repositories should I absolutly have which aren't included?

I use Ubuntu 6.06.1 LTS (Dapper Drake) because it has proven to be the most rock-solid anf problem-free distro I have ever used. Here is my sources.list file.

```

# This is my Ubuntu 6.06.1 LTS sources.list that is used by the package managers.

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
# deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

```

As you can see, this isn't much different from the default sources.list file that is intalled with the system. I have never had any problems with this list and it offeres most of the stuff in the repos.

---

### Post by LaurelLynn on 2007-04-07
Dear jbumgar,

It depends entirely on what you want to get.  For safety sake it is probably better to stick with the default repositories, such as those listed by ardchoille42,  for anything that is there.

If something you want isn´t listed you can broaden your search, but the further afield you go the riskier it becomes for your systems stablity, so backup before doing anything too unusual  (old time wisdom: Back it up or kiss it goodbye!)

Usually I try to go straight to the project home page to see if it has Ubuntu specific instructions, often they will list a repository (more often they will offer you a debian package file).

Laurel Lynn

---

### Post by ardchoille42 on 2007-04-08
> **LaurelLynn said:**
> If something you want isn´t listed you can broaden your search, but the further afield you go the riskier it becomes for your systems stablity, so backup before doing anything too unusual  (old time wisdom: Back it up or kiss it goodbye!)

Now that is some of the best advice I have heard with regard to Ubuntu repos.

---

### Post by LaurelLynn on 2007-04-08
Oh stop, your making me blush.

---

### Post by jbumgar on 2007-04-08
Thanks for your advice.

---

