---
title: "Ive compiled from source -- how do I make the .deb and install through package mgr?"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-09-14
Ive completed the ./configure, make process.  How do I make a .deb file and install through pckage manager rather than simply do a sudo make install?

Anything more than simply
sudo checkinstall

---

### Post by mcduck on 2007-09-14
Install the 'checkinstall'-package, and the when compiling the program instead of running 'sudo make install' use 'sudo checkinstall' and it will create a .deb package for you.

Edit. I just read the end of your post, and I need to ask what's the problem with using checkinstall? It's the tool for this kind of tasks.

If you want to create a 'real' .deb package instead of one made with checkinstall the Absolute Beginner forum is not the right place ;)

---

### Post by kevdog on 2007-09-14
Not a problem but should it be

./configure
make
sudo checkinstall
sudo dpkg -i ******.deb


Ive seen someone post something like
sudo checkinstall -D make install

Does that make any sense?

---

### Post by mcduck on 2007-09-14
> **kevdog said:**
> Not a problem but should it be

./configure
make
sudo checkinstall
sudo dpkg -i ******.deb


Ive seen someone post something like
sudo checkinstall -D make install

Does that make any sense?

OK, you can run 'sudo checkinstall --install' to install the package right away. The '-D' switch would tell checkinstall to create a .deb package, but it's not needed as that's the default option anyway.

---

