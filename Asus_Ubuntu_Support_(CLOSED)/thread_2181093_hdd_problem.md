---
title: "hdd problem"
date: 2013-10-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pay3 on 2013-10-16
My hdd total storage is 750 gb.
but when check my disk space in gpart it shows 700 gb.
How can i recover remaining 50 gb,

---

### Post by The Cog on 2013-10-16
My guess is that it's a difference between GB (Gigabyte : 1000000000 bytes) and GiB (Gibibyte : 1073741824 bytes).
Some software, particularly older software, reports sizes in GiB but uses the GB symbol.

700 GiB (751619276800 bytes) = 751 GB (751000000000 bytes) (roughly).

---

