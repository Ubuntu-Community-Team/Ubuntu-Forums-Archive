---
title: "/opt question"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by dagamer on 2008-01-26
how can i paste a file into /opt?
i'm trying to make a webserver and when i go to overwrite the htdocs folder, it says i need special permissions. can anyone please help me?

---

### Post by HereInOz on 2008-01-26
The easiest way is to open a terminal and type 
gksudo nautilus
then enter your password.

This will open Nautilus with root permissions (take care accordingly) and allow you to do what you want to do.

---

### Post by dagamer on 2008-01-26
it says

server@server-desktop:~$ gksudo nautilus
bash: gksudo: command not found

---

### Post by taurus on 2008-01-26
You want to copy a file to /opt directory?  Run

```
sudo cp filename /opt
```

p.s.  Gksudo nautilus if you are running Gnome but looks like you are running a server version, commandline only.

---

### Post by HereInOz on 2008-01-26
Well, that is a new one on me.  Works fine from where I sit.  

Are you using gnome, KDE, or xfce desktop?  If you are not using gnome, then nautilus is probably not installed.

---

