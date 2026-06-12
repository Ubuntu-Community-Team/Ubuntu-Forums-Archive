---
title: "automatix"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Bigadada_saba on 2007-07-07
i upgraded to 7.04 from6.10
then i reinstalled automatix  but the 6.10 version keepsinstaling insted of the 7.04 what do i do to install the 7.04 version

---

### Post by Cypher on 2007-07-07
Check that you have the following line in your /etc/apt/sources.list file
```

deb http://www.getautomatix.com/apt feisty main

```
You probably have "Edgy" instead of "Feisty"..

---

