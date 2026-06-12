---
title: "Ubuntu 64bit SMP folding@home"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by hughlle on 2007-03-22
[IMG]http://i2.photobucket.com/albums/y8/hughlle/fh.png[/IMG]

tried lots of things, different directories but i simply can't get it to work, every single time i get unknown file or directory whether the console is running in the f@h folder or whether i use the [email]fa@h.exe[/email] link from cd /

help! :(

---

### Post by laredo7mm on 2007-03-30
Make sure you install the ia32-libs package, SMP FAH needs that when you are running a 64bit distro.

Then, in the terminal, cd into your folding directory and type:

```
./fah5
```That should do it.  You can also add the -verbosity9 flag after your fah5 and it will write more info to the log file.

---

