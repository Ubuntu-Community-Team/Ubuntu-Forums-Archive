---
title: "What is the difference between..."
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by jecahn on 2007-05-01
The server edition of Feisty and the Desktop edition?

---

### Post by starcraft.man on 2007-05-01
Server edition is for people who want to run websites... Desktop is for the average day user.

Simple enough question, its likely you want the Desktop edition unless your planning on hosting a website.

---

### Post by Tomosaur on 2007-05-01
Server edition: Command line only, server's dont need GUIs.

Desktop edition: GUI, desktop computer's generally aren't servers.

The server edition can become the desktop edition by installing the 'ubuntu-desktop' package. Desktop edition can become server edition by purging the 'ubuntu-desktop' package.

---

### Post by annda on 2007-05-01
well, server is a plain server. it has apache, mysql, php and perl (i think) but it has no GUI/desktop/window manager. if you want it, you will have to install them via command line.

the desktop edition has a window manager GNOME (kubuntu has KDE), but you will have the install the server packages yourself.

---

### Post by jecahn on 2007-05-01
OK, so since basically the only thing I know about the command line is that it exists, I should stick with "Desktop..."

I accidentally downloaded the server ISO and was wondering if I could use it. The answer, I guess, is: It's usable just not by me, yet.

Thanks guys.

---

### Post by starcraft.man on 2007-05-01
Have fun with Ubuntu :)

---

### Post by Tomosaur on 2007-05-01
> **jecahn said:**
> OK, so since basically the only thing I know about the command line is that it exists, I should stick with "Desktop..."

I accidentally downloaded the server ISO and was wondering if I could use it. The answer, I guess, is: It's usable just not by me, yet.

Thanks guys.

Well, you can install it, then just type:
```

sudo aptitude install ubuntu-desktop

```

at the command line. After it's finished downloading and installing, just reboot your machine and you'll have the Desktop version :P

But it may be quicker to just download the desktop version as an iso anyway, plus the installer is far more user-friendly.

---

