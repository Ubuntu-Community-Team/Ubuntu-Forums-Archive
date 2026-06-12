---
title: "New to Ubuntu"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by aklk1998 on 2007-04-11
I am new to Linux and Ubuntu.

I just installed the Ubuntu Server version.  Want to understand whether I can install the desktop version on top using the machine as a server and desktop at the same time.

Thanks

---

### Post by BarfBag on 2007-04-11
I'm sure you could.  I don't know a lot about servers, so somebody should verify this.

To install a graphical desktop, just type:

> sudo apt-get install ubuntu-desktop

---

### Post by Iowa Dave on 2007-04-11
The difference between the two distributions is mostly what comes on the installation CD. The server version comes without the graphical interface, but adding it probably doesn't take anything away from the server side of your installation.

You might run into some configuration "features" in the process of getting your desktop graphical user interface to your liking. Be philosophical about it and search the forums.

A good discussion on the topic can be found at [http://ubuntuforums.org/showthread.php?t=407245]("http://ubuntuforums.org/showthread.php?t=407245").

---

### Post by jem7v on 2007-04-11
I think you should be able to.  Surely you could just load your desktop and then move over to another virtual terminal (i.e., Ctrl+Alt+F1 through F6), log in there, and do your server stuff that way, right? Right? (I'm guessing.)

Instead of using apt-get to install a desktop environment, though, it might be smarter to use aptitude because it does a cleaner job if you decide to remove it later... you can read more about that here: [http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

---

### Post by karamba_kid on 2007-04-11
A server install doesn't come with a GUI because it is not needed, and it reduces the amount of bugs and security vulnerabilities your system will have.  With that in mind you can run a GUI on your server but I believe that it is not generally recommended.

---

