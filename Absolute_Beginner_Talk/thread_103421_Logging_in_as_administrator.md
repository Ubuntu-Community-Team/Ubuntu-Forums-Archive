---
title: "Logging in as administrator?"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Phuayj on 2005-12-14
How do I log in as an administrator?

---

### Post by gosh on 2005-12-14
Perhaps this Wiki helps you?

[https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin](https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin)

bye

---

### Post by kont.raen on 2005-12-14
[QUOTE=Phuayj]How do I log in as an administrator?[/QUOTE]

Actually, I do not think that you will be gaining much advantage by logging in as root - therefore you should consider opening a terminal and launching the desired app as root from there with :

sudo <name-your-app>

If you are in need of a root-shell, then - again - lauch a terminal and make it a root shell by typing

sudo bash

Hope that solves your problem.

---

### Post by Sokraates on 2005-12-14
If you want to work in a graphical environment as superuser, start the desired app with sudo.

```
sudo nautilus
```

will open nautilus as superuser, so you can edit systemfiles. Of course, you should know exactly, what you are doing.

If you want to follow a wiki or how-to, it is usually safer to simply copy&paste the given commands and execute them in a terminal.

---

### Post by Brunellus on 2005-12-14
Consult the RootSudo wikipage for an explanation of how Ubuntu handles root permissions:

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

