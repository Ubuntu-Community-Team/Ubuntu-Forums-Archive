---
title: "Error message"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-12-27
I received this error message. How do I fix this

```
: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

---

### Post by taurus on 2007-12-27
Close whatever window you have where you got that error message.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by bump_ on 2007-12-27
Go to Applications>Accessories>Terminal

and type the command the message tells you to try:

```
sudo dpkg --configure -a
```

---

