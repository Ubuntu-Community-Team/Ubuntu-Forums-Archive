---
title: "Having Problems with Terminal Access"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by tkn4everb on 2008-01-22
Whenever we try to use the terminal to install something it will ask us for the user password, but it wont let us type the password or anything in for that matter. Is their a way to disable ubuntu from asking us to put in a password, or is there something that we are doing wrong when we try to enter the password?

---

### Post by gvartser on 2008-01-22
Im guessing that you are using:

```
sudo apt-get install <package_name>
```

from your shell / terminal while installing appz etc.

Well thats how it works, as you are installing using root privileges, the password you should specify is your own accounts, password. That is if you are in the correct group.

Best regz,
/g

---

### Post by Paul820 on 2008-01-22
The password will not show for security reasons. You can just type the password and press enter.

---

### Post by alsamman on 2008-01-22
when u type password in terminal, it looks like it isnt typing anything but it is, so when u are asked for password, just put it in (even though it nothing appears on the screen) and then press enter.

---

### Post by tkn4everb on 2008-01-22
Wow we feel really stupid right now. We thought the keyboard was responding. :lolflag::lolflag::lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by tkn4everb on 2008-01-22
Where does it install to?:confused:

---

### Post by Paul820 on 2008-01-22
You can type the name of the package in the terminal. Or you can press Alt+f2 and type the name there or you can type in the terminal:
> whereis package_name
to locate the program and then make a menu entry for it by going to System->Preferences->Main Menu and fill in the info from there.

---

