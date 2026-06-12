---
title: "Installing xine from source"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by knoc on 2006-12-17
I recently downloaded the xine.tar.gz because I read that it was a pretty versatile media program. (I suppose that .tar.gz is indicative of the file being the source) I have no idea how to install it. I have already installed the build-essential packages to compile source packages (if I even needed to do that.)

The location of the file is on my desktop and the name is "xine-lib-1.1.3.tar.gz"

I've looked at various tutorials on installing applications from their sources and I have been getting Errors saying:

dieter@dieter-ubuntu:~$ sudo apt-get install xine
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xine
dieter@dieter-ubuntu:~$ sudo apt-get -b source xine
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for xine

I don't really know where to start. Assistance would be much appreciated. Thanks. ](*,)

---

### Post by Bachstelze on 2006-12-17
Hi and welcome to Ubuntu :)

Xine is just a playing engine, which can be embedded in numerous frontends. If you're using GNOME, you can use Totem as a frontend for Xine, just do :

```
sudo apt-get install totem-xine
```

---

### Post by aysiu on 2006-12-17
Xine is in the Universe repositories.

**Step 1**: Delete the .tar.gz you downloaded. It's not needed.

**Step 2**: Enable extra repositories
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 3**: Install Xine by pasting this command into the terminal: ```
sudo aptitude update && sudo aptitude install xine-ui
```

---

### Post by knoc on 2006-12-17
Thank you very much :)

---

