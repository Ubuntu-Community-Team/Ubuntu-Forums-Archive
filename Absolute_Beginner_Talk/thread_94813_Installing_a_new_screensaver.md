---
title: "Installing a new screensaver"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by Rumor on 2005-11-24
Hello:
This is a *very insignificant* question. The successful resolution of it will not affect my decision to stay with Ubuntu as my only OS.
 
I want to install a screensaver. Just something aesthetic.

The URL for the screensaver is: [http://www.linuxhotbox.com/fun/Linux-screensavers-5.htm](http://www.linuxhotbox.com/fun/Linux-screensavers-5.htm)


I want the Hufo's Smokev screensaver.

When I download the file and unarchive it, I end up with a directory called rss-glx_0.7.6 in my home directory. My question is, now what? There are several files and other directories in this one directory, but I don't really know where to begin, being (appropriately enough) an absolute beginner.

Thanks for reading this and rolling your eyes quietly :D

---

### Post by davmac on 2005-11-26
When you download this you've got source code so you need to compile it.

Open up a terminal window and then change into the directory where you've downloaded the bz2 file and type "tar -xvjf nameoffile.tar.bz2"

This will create a new directory. Change into this directory and run the following commands;

./configure
make
sudo make install

Hope this helps,

Dave Mac

---

