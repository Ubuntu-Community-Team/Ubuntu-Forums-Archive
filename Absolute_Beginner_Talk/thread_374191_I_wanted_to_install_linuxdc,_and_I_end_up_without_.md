---
title: "I wanted to install linuxdc, and I end up without my X Window!!!"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Carlos Santiago on 2007-03-02
Hi. I wanted to install linuxdc, and I end up without my X Window!!!
To compile linuxdc ([http://sourceforge.net/projects/linuxdc](http://sourceforge.net/projects/linuxdc)) it needs libGTK+2.0 lib, and its headers.

However it didn't accept my version, so I had to install it by hand.
I download the .deb, then I made 'apt-get -f install', and finally made dpkg -i <.deb file>.

This procedure successful installs the version of libGTK that linuxdc needs, but I really don't recommend it. Why? Keep on reading.

Linuxdc also needs libglib2.0 and its headers. So I repeat the procedure. 
But now, after the command 'apt-get -f install', it start to delete everything related to X Window.
It even deletes nautilus and firefox.

When this deletes start, I thought it would install it again, but it up ends with an exit(1) !!!!

Now I am without my X!!! And it was so nice, finally I got it configured as I wanted it to be .... :-(((

---

