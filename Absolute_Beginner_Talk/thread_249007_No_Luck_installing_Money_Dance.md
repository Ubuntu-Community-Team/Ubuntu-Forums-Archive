---
title: "No Luck installing Money Dance"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Zoolook on 2006-09-01
Help...


hallmr@hallmr-laptop:~$ sudo chmod -x moneydance_linux_x86wj.sh
hallmr@hallmr-laptop:~$ ./moneydance_linux_x86wj.sh
bash: ./moneydance_linux_x86wj.sh: Permission denied
hallmr@hallmr-laptop:~$ sudo ./moneydance_linux_x86wj.sh
sudo: ./moneydance_linux_x86wj.sh: command not found
hallmr@hallmr-laptop:~$
hallmr@hallmr-laptop:~$

Wassup?

---

### Post by szf on 2006-09-01
The first chmod (chmod -x) removed the execute priviledge, as written... are you certain you want the *wj (with-java) package?

Did you try sudo sh ./moneydance-install...sh?

---

### Post by clapper65 on 2006-10-22
You want to do a chmod +x to make the file executable.

---

