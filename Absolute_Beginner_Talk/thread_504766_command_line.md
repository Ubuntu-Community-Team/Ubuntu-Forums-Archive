---
title: "command line"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-07-19
what is the command to list all installed applications?

---

### Post by Happy_Man on 2007-07-19
> **k33bz said:**
> what is the command to list all installed applications?
```
ls -a /bin
```

---

### Post by k33bz on 2007-07-19
thank you, wait no thats not the one i was looking for, there was a command some one had told me before that list the number of installed applications, as well as all application and packages by name in a scrolling list

---

### Post by asmoore82 on 2007-07-19
to see a list of all installed packages: use synaptic graphically or read the manual to apt for the command line

to see a list of all programs that you can actually run from your command line, hit Tab a few times

---

### Post by newlinux on 2007-07-19
```
 sudo dpkg --get-selections 
``` will list packages and their install/deinstall status

This would clean the output up a bit.

```

sudo dpkg --get-selections | grep '[[:space:]]install$' | awk '{print }' > package_listing

```

which would put them in a file

---

