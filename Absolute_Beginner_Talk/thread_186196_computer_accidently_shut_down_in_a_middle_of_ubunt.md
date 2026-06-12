---
title: "computer accidently shut down in a middle of ubuntu install"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by gardara on 2006-06-01
I was installing ubuntu on a laptop and accidently the power plug loosened and it turned of (there was no battery in it) I tried booting up ubuntu and then I got some error message about broken packages, when I clicked ok in the broken packages message ubuntu just came up wit the graphical login window and I was able to log in... now I want to finish the installion that I was doing but I don't know how I should do that? Should I start some repair or recover? Or should I start the installion again?

---

### Post by Jagot on 2006-06-01
In terminal, do:

```
sudo aptitude install ubuntu-desktop
```

This should make sure you have everything you need.

---

### Post by gardara on 2006-06-01
when I do that I get:

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
```

What do I need to do now?

---

### Post by Kyzon on 2006-06-01
do what it tells you to:

dpkg --configure -a

---

### Post by Sef on 2006-06-01
First open the terminal (Applications > Accessories > Terminal)

then

sef@jokat1:~$ dpkg --configure -a (enter)
password:  xxxxxxx (enter)

---

### Post by gardara on 2006-06-02
I did ```
sudo dpkg --configure -a
```
then 
```
sudo aptitude install ubuntu-desktop
```

Now everything seems to be working :)

---

