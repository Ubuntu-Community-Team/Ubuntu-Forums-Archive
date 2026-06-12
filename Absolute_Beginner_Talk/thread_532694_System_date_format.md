---
title: "System date format"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Andre_3608 on 2007-08-23
Please let me have the full code necessary to alter the system date format to yyyy-mm-dd.  Many thanks.

---

### Post by daradib on 2007-08-23
```
sudo gedit /etc/environment
```

edit line

[HTML]PATH=”/usr/local/sbin:/usr/local/bin:/usr/sbin:/us r/bin:/sbin:/bin:/usr/games”
LANG=”en_US.UTF-8&#8243;[/HTML]

replace with LANG=”x&#8243; where x is the locale with the yyyy-mm-dd format (i.e. LANG="en_DK.UTF-8").

---

### Post by Andre_3608 on 2007-08-23
Worked like a charm - sincere thanks.  André

---

