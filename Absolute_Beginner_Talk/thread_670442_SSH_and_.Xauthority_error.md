---
title: "SSH and .Xauthority error"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2008-01-17
I am getting an error when remotely using my computer via X forwarding.

ssh -X tom@hostname

yields the following:
/usr/bin/X11/xauth:  error in locking authority file /home/tom/.Xauthority

ls -l .Xauthority
yields:
-rw------- 1 tom tom 52 2008-01-17 13:35 .Xauthority

running any application yields
X11 connection rejected because of wrong authentication.
The application lost its connection to the display localhost:10.0;
most likely the X server was shut down or you killed/destroyed
the application.
-or-
X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).

X forewarding has been working beautifully until now... not sure what the problem is at all

please please help
tom

I've tried restarting x "startx", rm .Xauthority, creating a new one... etc. and nothing seems to work

---

### Post by kernel tom on 2008-01-17
okay so it fixed itself... 

but does anyone know what happened?

---

