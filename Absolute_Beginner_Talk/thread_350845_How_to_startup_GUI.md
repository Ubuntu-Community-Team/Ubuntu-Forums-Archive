---
title: "How to startup GUI?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by inspiron on 2007-02-01
I have installed Ubuntu 6.06 and after the installation it hangs after the message: "Uncompressing Linux... Ok, booting the kernel"
That problem I fixed by running in rescue mode and give the commands:
apt-get install linux-386
apt-get remove linux-server

Now ubuntu starts up and I can log in to my system but how do I load a GUI, like Gnome or KDE?

---

### Post by aberry5555 on 2007-02-01
If it is the server edition you will need to install the ubuntu-desktop by typing sudo apt-get install ubuntu-desktop, otherwise if it's the normal version then type in "start-x" or "startx" or "start x" or, if they all fail, "gnome". I think the first of these is the one to go for, I can't remember the exact wording!

---

