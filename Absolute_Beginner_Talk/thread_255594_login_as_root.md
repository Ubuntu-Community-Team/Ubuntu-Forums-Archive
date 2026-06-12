---
title: "login as root?"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by MeRcYFuL_FaTe on 2006-09-11
i want to change a file but get an error message saying i don't have enough permissions.how do i do this(eg. edit a file with admin rights) without using console?

---

### Post by madmetal on 2006-09-11
sudo gedit <filename>
then give password

---

### Post by John.Michael.Kane on 2006-09-11
Read here [[COLOR="Blue"]**Going back to a traditional root account**[/COLOR]]("https://help.ubuntu.com/community/RootSudo") listed at the bottom will explain howto: do what your asking.



[COLOR="Red"]**Note: This is not recommended! You Do This At Your Own Risk Should You Screw Your Machine Up Do Not Ask For Help.**[/COLOR]

---

### Post by John.Michael.Kane on 2006-09-11
madmetal he/she does not want to use the CL as you have posted.

---

### Post by madmetal on 2006-09-11
ok mea culpa..

---

### Post by aysiu on 2006-09-11
How about Alt-F2 ```
gksudo nautilus
```? That's a good, quick graphical way to make root changes.

---

### Post by ruedu on 2006-09-11
Can I ask...what are you trying to change that you need root permissions?  Maybe there is a different tool that will do the trick.

---

