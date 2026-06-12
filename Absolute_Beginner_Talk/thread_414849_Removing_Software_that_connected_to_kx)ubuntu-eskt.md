---
title: "Removing Software that connected to /k/x)ubuntu-esktop"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by diskotek on 2007-04-20
when i wish to remove a program/software that comes with default by synaptic; i saw that it will remove ubuntu-desktop as well.

for example: i'm trying to remove f-spot through synaptic it says that "do you also want to remove additional packages (straight translation). and well, i'm afraid to delete f-spot than... and i'm afraid that i'm a n00b :(

what should i do, it will really remove ubuntu-desktop?

---

### Post by Bachstelze on 2007-04-20
Removing *ubuntu-desktop* is harmless but remember to reinstall it when/if you upgrade to the newer Ubuntu.

---

### Post by Ownerizer on 2007-04-20
ubuntu-desktop is basically a metapackage that depends on everything else installed by default on your system, although it doesn't really "do" anything. it's fine if apt-get remove it when you are uninstalling something.

---

### Post by goldaryn on 2007-04-20
Short answer: you can do it.

If you remove a package that ubuntu-desktop depends on (e.g. evolution), it will remove evolution (and dependants) and the ubuntu-desktop 'wrapper' package, but not all the various packages that ubuntu-desktop depends on.

I think if you somehow managed to do this (NOT a good idea) , it would warn you i.e. Warning, the following packages will be removed .... then list loads of packages.

I think the reason ubuntu-desktop exists is to provide an easy way to install 'desktop ubuntu' i.e. sudo apt-get install ubuntu-desktop will install everything you need.

Hope this helps.

g.

---

### Post by diskotek on 2007-04-20
thank you very much for your suggestions/answers **hymntolife** & **ownerizer & goldaryn**.

---

