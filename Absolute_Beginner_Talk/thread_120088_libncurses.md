---
title: "libncurses"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by mitchx3 on 2006-01-20
so im trying to install kismet and get this when i run 

configure: WARNING: Unable to find libncurses
checking for initscr in -lcurses... no
configure: error: Unable to find libncurses or libcurses

So my question is how/where do I get libncurses?

---

### Post by chlorinekid on 2008-03-17
anyone have any idea on this? i've run into the same problem...

---

### Post by chlorinekid on 2008-03-17
sorted it...

```
sudo apt-get install libncurses5-dev

```

---

### Post by bruce89 on 2008-03-17
*kismet* is available from the repository by the way.

---

### Post by cmnorton on 2008-04-10
I'm struggling to introduce Ubuntu as an alternate server environment versus Red Hat EL, and we use Informix Forms, which relies on libncurses. I love Ubuntu, for desktop or server, and it's these little items that make it difficult to set up. But having answers like this more than counter-balances the problems.

We have an old Informix forms application that needs libncurses, and for some reason it did not get installed on one of my systems. It is installed now.

---

