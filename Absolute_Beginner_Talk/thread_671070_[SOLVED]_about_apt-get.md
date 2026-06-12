---
title: "[SOLVED] about apt-get?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by lemonicetea on 2008-01-18
Hi, when I use "apt-get install", It always tells me to insert CD.I am wondering how can I set it to download from internet rather than from CD. Thanks a lot.

---

### Post by PmDematagoda on 2008-01-18
Open Software Sources in System>Administration>Software Sources and then disable the CD-ROM, after that your problem should be solved.

---

### Post by skymera on 2008-01-18
alternatively

```
 gksudo gedit /etc/apt/sources.list 
```

then just # out the cd rom

---

### Post by lemonicetea on 2008-01-18
Thanks a lot!!!

---

### Post by zipperback on 2008-01-18
> **lemonicetea said:**
> Thanks a lot!!!


Once you have removed the cd-rom from your repository list, you may want to also update

```

sudo apt-get update

```

This will reload the available packages from your available repositories.

- zipperback
:popcorn:

---

