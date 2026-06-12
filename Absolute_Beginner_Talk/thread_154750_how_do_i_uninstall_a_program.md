---
title: "how do i uninstall a program"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2006-04-03
I am about to install a program called EAGLE from a .tgz file using the command
./install
afterwards, i would run it by typing "eagle" in my terminal.

How would I uninstall this program later on?

Please provide me with step-by-step instructions.

---

### Post by chuckyp on 2006-04-03
[QUOTE=racermike1967]I am about to install a program called EAGLE from a .tgz file using the command
./install
afterwards, i would run it by typing "eagle" in my terminal.

How would I uninstall this program later on?

Please provide me with step-by-step instructions.[/QUOTE]


Most likely there are directions for uninstalling in the readme.  If not the common way when installing something from source is to make uninstall in the directory that you downloaded the source.

---

### Post by Sweet on 2006-04-03
[QUOTE=chuckyp]Most likely there are directions for uninstalling in the readme.  If not the common way when installing something from source is to make uninstall in the directory that you downloaded the source.[/QUOTE]

Chuckyp is right, but just to clarify, the comand is:

```
make uninstall
```

---

### Post by racermike1967 on 2006-04-03
I tried make uninstall but i get the message:
make: *** No rule to make target `uninstall'.  Stop.
What should I do?

---

