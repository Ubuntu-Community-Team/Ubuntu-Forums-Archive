---
title: "Booting to Windows on default"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by tromik on 2006-07-19
Just installed Ubuntu, and I was looking through the Ubuntu Guide for the how-to on altering the GRUB boot order. I'd like Windows, not Ubuntu, to boot by deafult, ie. after ten seconds.

---

### Post by jd65pl on 2006-07-19
hi 

in terminal

```
sudo gedit /boot/grub/menu.lst
```

Edit the file to reflect the change you wish

---

### Post by risbac on 2006-07-19
You have to edit /boot/grub/menu.lst 

They explain in the file how to define the default OS: 

> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.

Otherwise, you have a line like this:

```
default 0
```

You can change the 0 into the number of the default OS (0 first choice from the top).

---

### Post by aysiu on 2006-07-19
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

