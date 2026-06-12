---
title: "Need help compiling driver, gspcav1-20070508"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-09-18
I extracted to my desktop. In the extracted directory there's a file called gspca_build but if I type sudo gspca_build it says sudo: gspca_build: command not found. Is there a correct way to run this shell script?

---

### Post by SmokinJuan on 2007-09-18
Your desktop is in your home directory and your home directory is not in your path (security stuff, so I've read).

Anything ran from a command line in your home directory needs to be proceeded by ./ (current directory) like this:

```
./gspca_build
```

---

### Post by philinux on 2007-09-18
Yes but I used sudo.

---

