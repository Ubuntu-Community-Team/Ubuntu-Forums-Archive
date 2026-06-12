---
title: "install xmgrace- repositories"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by marta_santander on 2007-09-23
Hi!
I am new in Ubuntu 7.04  and I am trying to install xmgrace using "sudo apt-get install grace" in a terminal but it doesn't go. This message appears in the terminal:

~$ sudo apt-get install grace
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grace is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grace has no installation candidate

I have checked the repositories in system-->administration-->Synaptic package manager-->settings-->repositories and I have all the repositories marked as on (main,universe,restricted and multiverse).
Anybody could say to me how is happening and how to install xmgrace? 
Thank you.

---

### Post by agurk on 2007-09-23
Hmm, have you run 'sudo apt-get update' before trying to install grace?

---

