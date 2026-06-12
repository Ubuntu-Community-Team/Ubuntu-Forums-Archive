---
title: "gedit: command not found"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by ruzinfruz on 2007-03-23
Hi,

I have install server 6.06 as a LAMP. I also have installed ftp.

I need to go in and edit the vsftp.conf file, but gedit isn't working!?!

all i get is

[INDENT]-bash: gedit: command not found[/INDENT]

when I try to install it, my machine gives out

[INDENT]E: Couldn't find package gedit[/INDENT]

It does not attempt to spinn up the cd drive (if that is what E: actually is)

I can not actually find any package, no matter what I try to install.

---

### Post by taurus on 2007-03-23
Gedit is a GUI editor for Gnome.  Since you have a server, you need to use nano instead.

```
sudo nano -Bw **filename**
```
Save and exit with <Ctrl>o and <Ctrl>x.

---

