---
title: "&quot;Rename&quot; a command"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by ziofu on 2007-03-27
Hi!

I've just installed g++-4.1 and I'm interested in renaming the command to something like g++. How can I do that?

Thank you.

---

### Post by taurus on 2007-03-27
You can make a symbolic link to it.

```
sudo ln -s /usr/bin/g++-4.1 /usr/bin/g++
```

---

### Post by annda on 2007-03-27
or create an alias in .bashrc in your home directory. add a line like this:

alias g++='g++-4.1'

---

### Post by ziofu on 2007-03-27
Thank you!! :P

---

### Post by x1a4 on 2007-03-27
> **ziofu said:**
> Thank you!! :P

How rude.  People are helping you and you're sticking your tongue out at them. ;)

---

