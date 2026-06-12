---
title: "[SOLVED] Installing a new OS"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-12
I've managed to partition my HDD into two parts

hda 1 = /
hda 2 = HOME

In the future if I wish to ditch Feisty Fawn and change to another version of Ubuntu, will I need to reconfigure all my hardware again ie wireless connection ??

Or will the necessary files have been stored in my HOME folder already, allowing me simply to install the new OS to hda 1.

---

### Post by eggdeng on 2007-09-12
You will have to install drivers again. Even a kernel update often breaks graphics drivers among other things, so be careful never to update the kernel unless you have a very good reason. This means you have to be careful about updating any package with the word linux in the name. The home folder is basically for files which belong specifically to individual users.

---

### Post by chrome307 on 2007-09-12
OK thanks :)

---

