---
title: "Update Manager"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2007-06-15
The update manager seems to crash every time I try to install any updates.  If I have entered my root password into another application before running the update manager, the update manager will happily ask for my root password and install the updates.

If the update manager is the first administrative application that I run, it crashes when trying to bring up the dialogue box for my root password.

What is the problem?

---

### Post by diatribe on 2007-06-15
just go to a terminal and type:

sudo apt-get update
sudo apt-get upgrade

and then it will upgrade for you

---

