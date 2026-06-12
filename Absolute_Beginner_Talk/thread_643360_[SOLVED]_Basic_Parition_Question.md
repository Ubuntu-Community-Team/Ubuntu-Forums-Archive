---
title: "[SOLVED] Basic Parition Question"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by yianni.elias on 2007-12-17
I was wondering if someone could explain why Ubuntu sets up a double partition by default. There's a dev/sda1, a 2.89gb dev/sda2 called "extended", and as a sub-partition to "extended", there's also dev/sda5, "linux-swap".

Out of curiosity I'm just wondering what these different partitions used for and why they exist.

Thanks!

---

### Post by thelatinist on 2007-12-17
Linux uses a swap partition in place of a swap file.  If you're coming from Windows, it's like your 'virtual memory.'  This is perfectly normal.

---

### Post by yianni.elias on 2007-12-17
Thanks very much - good explanation.

---

