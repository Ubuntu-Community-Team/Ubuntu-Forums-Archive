---
title: "Can I save  telnet session?"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Minker17 on 2007-11-16
I need to be able to telnet into a server dozens of times a day, I've just been going to Applications > Accessories > Terminal in Xubuntu and typing it in, but I'd really love to create a launcher on my desktop that will automatically telnet into the server and get me to the log in screen. 

Is that possible?

---

### Post by evilregis on 2007-11-16
I'm pretty sure FreeNX will give you the option of terminating a session completely or just closing the session for resumption later.

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

### Post by PointyWombat on 2007-11-18
On the desktop, right-click and select 'Create Launcher...'
For Type, select "Application"
For Name, enter something like: "Session to <your server>"
For Command, enter: gnome-terminal -e "ssh <youruserid>@<yourtargetserver>"
For Comment: enter something like: "Sesseion to <your server>"

Hit OK and you should get a working icon on your desktop...

---

### Post by Minker17 on 2007-11-19
I don't have the option for "type" to select application. Do I need to run this in terminal?

Oh, this is in Xubuntu.

---

### Post by PointyWombat on 2007-11-20
Well I don't know anything about how the xubuntu desktop looks, but I suspect that it wouldn't be too hard to just try a few things out and find what works.. there aren't too many options.. Do you at least have a place where you can enter in a command to execute with the launcher? Also, you may need to use xterm instead of gnome-terminal if xubuntu isn't gnome based.

---

