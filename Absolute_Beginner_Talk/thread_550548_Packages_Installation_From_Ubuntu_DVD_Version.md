---
title: "Packages Installation From Ubuntu DVD Version"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by 1normalguy on 2007-09-14
How do I install the remaining packages available on ubuntu dvd which are not installed by default. For example, I tried to install kde which is available on ubuntu dvd, but there are too many packages and I have no idea how to install them. I find 5 folders related to kde on dvd ( kdebase, kdebindings, kdelibs, kdepims, kdesdk ). When I try to run a single package it automatically starts downloading dependencies form internet which are available on dvd:(.

---

### Post by mikewhatever on 2007-09-14
Assuming you have Feisty Fawn, go to System>Administration>Software Sources and add the DVD to the sources. (Don't forget to put the DVD into the tray.) Then update with 'sudo apt-get update' and install whatever you want.

---

### Post by 1normalguy on 2007-09-14
I don't see anything new added to the third-party software list when I click on Add CD ROM.

---

