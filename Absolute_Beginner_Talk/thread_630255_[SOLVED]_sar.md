---
title: "[SOLVED] sar"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-12-03
Hi,
executing command 'sar' in Ubuntu 7.10 32-bit Desktop from Terminal it reports error:
"Cannot open /var/log/sysstat/sa03: No such file or directory"

Any idea how to make this command work?

Thanks,
Abcuser

---

### Post by abcuser on 2007-12-03
Hi,
I have found out. On Linux it must be defined "count", so:
```
sar 1 -A
```

Thanks. Problem solved.
Abcuser

---

