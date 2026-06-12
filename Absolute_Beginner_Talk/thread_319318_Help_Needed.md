---
title: "Help Needed"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by cingh on 2006-12-15
hello, well i want to download sun java and to do that you need to be a super user (su), i go onto to terminal and type in su and my password, but it keeps on saying sorry you arnt a su, please please someone help me

---

### Post by Scorpuk on 2006-12-15
try typing


```
sudo su
```


in the terminal window. It will ask for your password and then any command u run after that will be as a super user.

---

### Post by cingh on 2006-12-15
thanks, now i can use frostwire

---

### Post by PriceChild on 2006-12-15
[uwiki]RootSudo[/uwiki] Might be a good read.

---

### Post by bulldog on 2006-12-15
> **Scorpuk said:**
> try typing


```
sudo su
```


in the terminal window. It will ask for your password and then any command u run after that will be as a super user.

Don't forget to exit the root user.
It's better to use sudo somecommand so you have root permission for that command.
You can break your Ubuntu running it as root very easily.

---

