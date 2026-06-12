---
title: "I'd like to write software for Ubuntu Linux, and I need a starting point."
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Altarbo on 2007-06-06
Hi,

Programming interests me.  I'd like to learn C++ and use it to write applications for Linux.  I don't know where to start, though.  I've written in Basic and 650x assembly before, so I have a general idea of what I'm going to do, but nothing specific to get started.

What I really need is to be pointed in the direction of some kind of tutorial explaining:
[LIST]
[*]where to get compilers
[*]how to use them (unless they come with docs.)
[*]how to use the Linux API
[*]how to use tool kits and libraries (GTK, X lib, etc.)
[/LIST]

I'm somewhat confused by how the different desktop environments work, too.  My understanding of them is this:  If I use only the basic tool kits for the X environment (X lib, I think) my software will look fine on any Linux system, but it'll lack consistency.  If I use a tool kit (say QT), then my software will look consistent on a system that has the library (KDE) but won't display on a system lacking it (Xfce, GNOME).  Is this right?  Do I even need to take it into account or will all Linux distros come with QT, GTK, Motif, etc.?

Last.  Could someone explain, or point me to an article that explains how to package software.  It seems like an excellent way to distribute software, but I don't know anything about it.



Thank you,
Altarbo

---

### Post by Celegorm on 2007-06-06
You'll want to check out the programming talk section of these forums: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39) the stickied threads have a lot of good information, and links to various useful sites, tutorials, etc. and there is a subforum about packaging software. Also, you'll want to install the build-essential package to get compilers and things. There are also various integrated development environments available in the repos.

---

