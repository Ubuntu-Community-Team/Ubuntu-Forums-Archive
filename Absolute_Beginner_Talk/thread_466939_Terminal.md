---
title: "Terminal"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by jay88 on 2007-06-07
i have been trying to set up my wireless card going through the throuble shooting guide and every terminal command i have tried has returned command not found is there anything you can think of thati could be missing

---

### Post by taurus on 2007-06-07
It would be real helpful if you can list the commands that you have tried.  A model of your wireless card doesn't hurt, either.

---

### Post by meng on 2007-06-07
What commands have you tried?

---

### Post by jay88 on 2007-06-07
sorry i should have been more specific
i have an hp pc and im trying to install the wn5301 adapter so far ive tried

sudo 1shw

and

sudo pccardctl ident

both returned
bash: command: command not found

thx for your help

---

### Post by meng on 2007-06-07
I think the first command should be:
sudo lshw
(not 1, the letter L in lower case)

---

### Post by hillbilly on 2007-06-07
What is the output of > echo $PATH
maybe its not set properly or you have overridden the system defaults.

---

