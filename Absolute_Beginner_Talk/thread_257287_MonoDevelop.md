---
title: "MonoDevelop"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-09-14
Anyone know **ALL** the req's to install? I am getting loads of errors when installing.

---

### Post by skymt on 2006-09-14
It should be a simple apt install. What errors do you get?

---

### Post by Ben Sprinkle on 2006-09-14
Alot, it is not in the repositories. I am installing from the source tarball.

I keep getting "must install..." programs, I am at school now and keep installing the required program andd installing. Then try compile again and it requires another program. So I need like a full list.

---

### Post by monktbd on 2006-09-14
> **Goat Spirit said:**
> Alot, it is not in the repositories. I am installing from the source tarball.


it is in the repositories but right now i dont know in which.
enable universe and multiverse and you should be fine.

i got it from the repos :).

edit: just checked and it is in universe.
to get more repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Ben Sprinkle on 2006-09-14
Meh, I forgot to enable them as I just reinstalled ubuntu. Is the MonoDevelop there the latest version? 0.12 I believe.

---

### Post by monktbd on 2006-09-14
0.11 svn version i see in the repo i checked.
[http://at.archive.ubuntu.com/ubuntu/pool/universe/m/monodevelop/](http://at.archive.ubuntu.com/ubuntu/pool/universe/m/monodevelop/)

edit: sorry at work on windows, cant check properly right now what i have installed.

---

### Post by Ben Sprinkle on 2006-09-14
Meh, 0.11 is fine I reckon, it should install all req's then I'll just install from 0.12 source. ;)

---

### Post by bruce89 on 2006-09-14
Actually 0.10 is the latest on Dapper, 0.11 in Edgy.

---

### Post by Ben Sprinkle on 2006-09-14
Ubuntu is great and all, but in thier repo's a **TON** of apps are outdated.

---

### Post by skymt on 2006-09-14
> **Goat Spirit said:**
> Ubuntu is great and all, but in thier repo's a **TON** of apps are outdated.

You can always move to Edgy.

---

### Post by David Corrales on 2006-09-14
> **Goat Spirit said:**
> Ubuntu is great and all, but in thier repo's a **TON** of apps are outdated.

They need to freeze the tree before releases so they can make it all work together. Also, that's what backports are for :)
You can still download the source and if the library headers in your computer allow it, compile it and create a .deb (checkinstall) to upgrade your software. I've done that for banshee, f-spot and totem.

---

