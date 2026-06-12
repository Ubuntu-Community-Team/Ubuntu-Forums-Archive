---
title: "Root problem"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-09-16
I have realplayer in desktop but I need it in home, trouble is I can't move it as I do not have permission. How do I correct this please?

---

### Post by Majorix on 2007-09-16
By typing "sudo" infront of whatever command you are using.

---

### Post by saj0577 on 2007-09-16
```
Sudo mv /home/folder/ /home/qwerty/
```

/home/folder/ the folder you wish to move.
/home/qwerty/ the destination to move the folder too.

Saj

---

### Post by man_bash on 2007-09-16
If you REALLY need root priviliges
in terminal type 

"sudo passwd"
type a password for the root
retype a password for the root

now you can restart and login as root, with the password you typed, or invoke root mode in terminal via 

"su"
password

---

