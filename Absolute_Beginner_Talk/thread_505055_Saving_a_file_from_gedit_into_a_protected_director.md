---
title: "Saving a file from gedit into a protected directory"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-07-19
How do I save a file from gedit into a protected directory like var/www?

I'm trying to edit some files directly through terminal, prior to this I've been saving them on my desktop then copying them through terminal, which is a pain when you have to do it repeatedly

---

### Post by Kralizec on 2007-07-19
Open gedit as super user: interminal, do 'sudo gedit'. Then it should open gedit with administrative privileges allowing you to save the file wherever you want.

---

### Post by AlexenderReez on 2007-07-19
gedit is gui application....it is better to use 

> gksudo gedit

instead of 

> sudo gedit

---

### Post by woodsonoversoul on 2007-07-19
Thanks so much

---

### Post by Kralizec on 2007-07-19
sudo or gksudo works. gksudo merely provides a GUI for entering the administrator password, while sudo asks for it in the terminal.

However, if there's something special about gksudo, please let me know because for the most part I only use sudo.

---

### Post by aysiu on 2007-07-19
I'd use ```
gksudo
``` for graphical applications.

---

### Post by dondad on 2007-07-19
> **Kralizec said:**
> sudo or gksudo works. gksudo merely provides a GUI for entering the administrator password, while sudo asks for it in the terminal.

However, if there's something special about gksudo, please let me know because for the most part I only use sudo.

Sometimes using sudo rather than gksudo on a graphical app can mess up your permissions on your home directory. I have had it happen to me a couple of times.

---

### Post by aysiu on 2007-07-20
> **dondad said:**
> Sometimes using sudo rather than gksudo on a graphical app can mess up your permissions on your home directory. I have had it happen to me a couple of times.
More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

