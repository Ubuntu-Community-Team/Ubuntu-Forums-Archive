---
title: "Error with APT-GET. I don't get it."
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by JadedMaple on 2006-06-02
keith@beehands:~$ sudo apt-get install build-essential check install xlibs-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package install


What does that mean?

I am so confused.

---

### Post by meng on 2006-06-02
There's no package called install
I think the package you want is checkinstall (one word)

---

### Post by Dr. Nick on 2006-06-03
[quote=JadedMaple]keith@beehands:~$ sudo apt-get install build-essential check install xlibs-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package install


What does that mean?

I am so confused.[/quote]

yes it should be
sudo apt-get install build-essential[COLOR=Red] checkinstal[/COLOR]l xlibs-dev [COLOR=Black]

you cant have spaces in package names.
[/COLOR]

---

