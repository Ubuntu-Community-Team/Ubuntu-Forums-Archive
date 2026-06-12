---
title: "how do you install .rpm files [Resolved]"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by ndworecki on 2007-01-21
Hi im wondering how to install a .rpm file.


Thanx,
            Nathaniel

---

### Post by taurus on 2007-01-21
You  use alien to convert it to .deb and install it with dpkg.

```
sudo aptitude update
sudo aptitude install alien
alien **filename**.rpm
sudo dpkg -i **filename**.deb
```

---

### Post by MasterOfDisaster on 2007-01-21
Type in the terminal 'sudo apt-get install alien'.

Then type 'alien -d whateverfile.rpm'

This should create a .deb file, which you can double click on to install.

Pff. Beat me to it.

---

### Post by ndworecki on 2007-01-21
LOL same time responses with same information

Thank you a lot i really appreciate this.

---

