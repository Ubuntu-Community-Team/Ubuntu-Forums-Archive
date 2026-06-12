---
title: "Install help"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by SilentScream0320 on 2008-02-21
Ok, so I am very very new to linux and i'm have trouble with installing programs in general.  I know how to log in as root and how to change directories.  However it is after this that i run into trouble.  i have tried sh /install-sh, and it simply says can't open /install-sh.  i have tried every possible combination of sh install-sh, ./install-sh, typing in the full directory and then /install-sh.  I am 100% certain i am in the correct directory.  What am I doing wrong?

---

### Post by bodhi.zazen on 2008-02-21
Permissions. You have to make it executable first

```
sudo chmod a+x ./install,.sh
```

Then run it :

```
sudo ./install.sh
```

See also the sticky on these forums.

---

### Post by raja on 2008-02-21
What are you trying to install?
Can you post the ouput of ```
ls
```after you are in the 'right' directory?

---

### Post by SilentScream0320 on 2008-02-21
it says no input file specified

---

