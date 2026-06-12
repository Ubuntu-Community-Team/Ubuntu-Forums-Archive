---
title: "Difference between sudo and gksudo?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by islander_810 on 2007-02-26
What's the difference between sudo and gksudo?

---

### Post by taurus on 2007-02-26
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by nickoli_02 on 2007-02-26
sudo is meant to be used when the commands you type stay withing the terminal. Use gksudo when the command launches a graphical interface. For example:

```
sudo gedit /etc/apt/sources.list
```

will work, but technically is not correct.

```
gksudo gedit /etc/apt/sources.list
```

is correct. Using sudo to launch graphical interfaces can sometimes screw things up (not seriously, though!)

---

