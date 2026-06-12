---
title: "location of c header files that match the running kernel?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by vinther on 2006-07-12
thanks

Erik

---

### Post by fluffington on 2006-07-12
/usr/src/linux-headers-`uname -r`/include/linux

Edit: if you don't have it, you need to apt-get install linux-headers-`uname -r`

---

