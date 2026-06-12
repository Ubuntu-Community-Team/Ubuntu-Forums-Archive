---
title: "Login to Ubuntu GUI via SSH?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by zuccs on 2007-07-19
Ok, I have sort of confused myself...

The X11vnc service that I have setup, only runs once I have logged into ubuntu GUI. If I try to VNC to this before I have logged in it won't connect. 

If my headless computer gets reset, how can I login via SSH, without connecting a monitor to  the computer and logging that way? 

SSH is working, and I can connect to the computer before it is logged into the GUI.

..Or should VNC be running on the ubuntu GUI login if I set it up properly?

Thanks in advance, sorry if I made it more confusing than it needs to be!

---

### Post by scrooge_74 on 2007-07-19
Yes it is confusing :)

You should be able to log remotetly that is the point.  Probably you need to check on your config files.  But remember that using the GUI this way  is not exactly secure.

---

### Post by zuccs on 2007-07-19
Yeah I can SSH into the server okay, but I do not know how to log my computer on so that the X11vnc server will start properly...

By log on, I mean the screen that comes up on boot before you access ubuntu. I think I am right when I say the GUI login screen? 

I want to be able to login to this via SSH somehow, so the VNC server will start, so I can VNC into the machine if I need to...

---

### Post by scrooge_74 on 2007-07-19
Take a look at this thread, I havent tried it myself

[http://ubuntuforums.org/showthread.php?t=499431](http://ubuntuforums.org/showthread.php?t=499431)

---

