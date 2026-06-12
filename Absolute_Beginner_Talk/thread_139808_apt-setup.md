---
title: "apt-setup"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by WackToMack on 2006-03-04
Hello again people!  What does
```
apt-setup
```
do?  Thanks in advance! :D

---

### Post by Mustard on 2006-03-04
[QUOTE=WackToMack]Hello again people!  What does
```
apt-setup
```
do?  Thanks in advance! :D[/QUOTE]

It adds apt-get download sources. If recall correctly it takes you through a dialog to do so.

I found this on google. :)

[http://nixdoc.net/man-pages/Linux/man8/apt-setup.8.html](http://nixdoc.net/man-pages/Linux/man8/apt-setup.8.html)

---

### Post by Sef on 2006-03-04
What is the advantage to installing it?

---

### Post by az on 2006-03-05
It's part of the apt suite of tools.  A new setup uses it to configure apt (it is run by base-config).


You can also just run it if you bork your sources.list and want to start over, but I'm not sure how it handles the different repository naming scheme considering it is a debian tool.

---

### Post by Mustard on 2006-03-05
[QUOTE=azz]It's part of the apt suite of tools.  A new setup uses it to configure apt (it is run by base-config).


You can also just run it if you bork your sources.list and want to start over, but I'm not sure how it handles the different repository naming scheme considering it is a debian tool.[/QUOTE]

I'm pretty sure it handles the ubuntu repositories.  Perhaps its been modified on Ubuntu.  I've seen people recommending it on IRC, on occasion, and haven't seen anyone coming back with complaints. :)

---

