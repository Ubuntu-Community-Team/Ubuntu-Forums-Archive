---
title: "Guichan won't delete"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by .enigmatik on 2007-03-21
I installed guichan and later I ran ./configure, make, and sudo make uninstall in a terminal and then after it was done I sent it to the trash and tried to delete it. And I got a message saying it couldn't delete. Please help.

---

### Post by Muzik83 on 2007-03-23
If the error you received when you tried to empty the trash was something to the effect of "Permission denied" you can try

sudo rm -ri ~/.Trash/*

-sean

---

