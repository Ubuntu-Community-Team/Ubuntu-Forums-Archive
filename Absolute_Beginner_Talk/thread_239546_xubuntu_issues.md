---
title: "xubuntu issues"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by wisconsin on 2006-08-19
1. Even after successful install to HD, booting hangs 50% of the time at "Loading Hardward Drivers." Strange since the other half of the time everything boots just fine.

2. Need to log out as user & temporarily log in as root to copy certain files to a specific directory under user. Docs say that I can set a root pass by running "sudo passwd root" in a terminal window. But I get the message "sorry, try again." I'm stuck.

Thanks very much for any suggestions.

---

### Post by kepos on 2006-08-19
> **wisconsin said:**
> 2. Need to log out as user & temporarily log in as root to copy certain files to a specific directory under user. Docs say that I can set a root pass by running "sudo passwd root" in a terminal window. But I get the message "sorry, try again." I'm stuck.

why don't you use
[INDENT]
sudo cp <source> <destination>[/INDENT]

to copy this files?

---

### Post by bodhi.zazen on 2006-08-19
To change your root password (you did  not hear {read} this from me):

```
sudo passwd
```

TAKE GREAT CARE WITH ROOT

---

