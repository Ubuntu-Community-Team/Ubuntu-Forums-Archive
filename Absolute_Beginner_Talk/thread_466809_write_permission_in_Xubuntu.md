---
title: "write permission in Xubuntu?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Rita G. on 2007-06-07
how do i get write permission to edit /etc/apt/sources.list in xubuntu?

---

### Post by renzokuken on 2007-06-07
with the sudo command......not sure what the text editor in xubuntu is but in gnome you would run

```
sudo gedit /etc/apt/sources.list
```

you could use the terminal text editor "nano" though

```
sudo nano /etc/apt/sources.list
```

---

### Post by Wim Sturkenboom on 2007-06-07
Use sudo in front of the command, e.g. *sudo vi /etc/apt/sources.list*

---

### Post by Rita G. on 2007-06-07
thank you for your replies.

---

