---
title: "downgrade libc6"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by wayanwolvie on 2007-06-15
Hi everyone,

I have a problem here. I need to rollback/downgrade my libc to lower version (i'm using Ubuntu Dapper). But I don't know how to do it. I tried to uninstall it first and then install the lower version. But, It seems that synaptic will also uninstall a lot more other (60+ packages). 

Why I wan't to downgrade? actually this is the problem :

> The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20.4) but 2.3.6.ds1-13 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I tried to install Clucene from Debian repository, but it was failed because of the tzdata package cannot be installed. Then it creates error and I cannot update/install new packages (something blocks it, and message above appear). I want to solve this problem by install the libc6 from ubuntu.

Does anyone know how to solve this? because if not, I'm afraid I need to reinstall my ubuntu

---

### Post by mxc on 2007-07-17
We got the same issue. Any ideas on how to fix it?

---

### Post by peepingtom on 2007-07-19
*please delete

---

