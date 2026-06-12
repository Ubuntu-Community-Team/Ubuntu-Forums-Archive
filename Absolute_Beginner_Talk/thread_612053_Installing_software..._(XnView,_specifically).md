---
title: "Installing software... (XnView, specifically)"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Himself2007 on 2007-11-13
Hello

I'm a 100% genuine Ubuntu newbie!
And also to this forum.
So please don't be rough on me!
I naturally come from Windows.
And up to now, I've been impressed with Ubuntu.
And installing Windows software was simply double-clicking on a setup.exe file or something.
Now I'm just about to install Xnview for Linux.
So I just downloaded a file named "XnView-x86-unknown-linux2.x-static-fc4.tgz" pour installer Xnview."
Up to here I'm lost!
Can you please indicate me the steps to successfully install this software on Ubuntu?
I just want to you to be very precise on the "How to..." as I'm a bit lost.
But I intend to change this situation for the next incoming times!
In adavance, thanks very much!

Himself

---

### Post by aysiu on 2007-11-13
For XnView, I'd try pasting these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update
sudo apt-get install alien
wget -c http://download.xnview.com/XnView-static-fc4.i386.rpm
sudo alien -i XnView-static-fc4.i386.rpm
``` If you get any error messages, copy and paste them back here.

To learn how to install software in general, read these two links:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by aysiu on 2007-11-13
Actually, try [this](http://ubuntuforums.org/showthread.php?t=86306) instead.

---

### Post by Himself2007 on 2007-11-14
Aysiu

Thanks very much for the help!
Appreciated very much.
I'll  try it tomorrow.
Thanks for the link.

Himself

---

### Post by Jerry N on 2007-11-14
The current Linux version of Xnview is ugly and works poorly. However, Version 1.9 for Windows installs and works great under Wine. Irfanview is also supposed to work with Wine but when I tried it the thumbnails were washed out almost completely and the performance was poor. I am going to stick with Wine and Xnview for Windows until the next Xnview for Linux is released.

Jerry

---

### Post by daniber on 2008-04-01
Uhmmmm..... sure the next release planned date for XnView Linux version isn't "never".....????:popcorn:

---

