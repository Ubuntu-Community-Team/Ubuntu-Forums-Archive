---
title: "[SOLVED] Identify Ubuntu Version @ The CLI"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by _crash_ on 2008-02-23
In Bash, is there a way I can identify which version of Ubuntu I am currently running on my CPU?

Thanks for the help!

crash

---

### Post by PmDematagoda on 2008-02-23
```
cat /etc/lsb-release
```
should do the trick.

---

### Post by _crash_ on 2008-02-23
PmDematagoda,

THANKS TONS!!!

To help others out, here is what I got:


```
username@cpuname:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.2 LTS"
username@cpuname:~$
```


Again, thanks for the help!

crash

---

