---
title: "Problems with dpkg !"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by WILL_CHAN on 2008-03-13
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
chan@MrChan:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
chan@MrChan:~$ sudo apt-get install boostlib
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Lately I tried to install Codeblock 8.2, I changed some of repositories and now I can't install anything :(. Anyone could help me out :(. What's dpkg ? Why it is interrupted ?

---

### Post by joshrobinson on 2008-03-13
```
sudo dpkg --configure -a
```

you need sudo in front of the command it asked you to run

---

### Post by WILL_CHAN on 2008-03-13
Thanks a lot Josh. I think I really need time to get used to Linux system. Too many commands T_T !

---

### Post by joshrobinson on 2008-03-13
> **WILL_CHAN said:**
> Thanks a lot Josh. I think I really need time to get used to Linux system. Too many commands T_T !

your welcome, just a quick rundown of why you had this problem

sudo stands for super user do, as in do(run) this command as a super user
whenever you need to install packages, or edit config files that are vital to your computer, you have to use sudo to show that you have permission to edit or change those settings

so if a command comes back saying "permission denied, run as super user, etc." throw a sudo in front of it :)

---

