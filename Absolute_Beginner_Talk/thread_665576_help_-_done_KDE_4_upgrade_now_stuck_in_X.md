---
title: "help - done KDE 4 upgrade now stuck in X"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by llangwm on 2008-01-12
hello,
tried the kde 4.0 upgrade (followed [http://ubuntu-tutorials.com/2008/01/11/how-to-install-kde-40-in-kubuntu-710/](http://ubuntu-tutorials.com/2008/01/11/how-to-install-kde-40-in-kubuntu-710/)) and I now only have X windows.
ran   sudo apt-get install kubuntu-desktop   to try to fix
but no joy

then  sudo dpkg-reconfigure xserver-xorg   in desperation
still in X windows

I am choosing KDE4 from the menu on the X windows login ....
.... how do I fix it?

---

### Post by llangwm on 2008-01-12
I removed kde4-core (I'd used aptitude to install it) and then reinstalled .... this time I chose kdm instead of kdm-kde4 (which I had done previously)

and it works now. :)

---

