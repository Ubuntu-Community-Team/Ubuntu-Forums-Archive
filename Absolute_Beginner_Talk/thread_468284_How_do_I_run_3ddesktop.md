---
title: "How do I run 3ddesktop"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by StevenP9891 on 2007-06-08
I just installed 3ddesktop but I can find any icons or options to launch the application. Where would I find it or what would I need to do in the terminal in order to run it?

---

### Post by testube_babies on 2007-06-08
[http://ubuntuforums.org/showthread.php?t=100167](http://ubuntuforums.org/showthread.php?t=100167)

---

### Post by StevenP9891 on 2007-06-08
When I try to run it i get an error message in the terminal:

[I]steven@steven-desktop:~$ 3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)[/I]

---

### Post by StevenP9891 on 2007-06-08
Also, I only have a generic video card, if that helps...

---

### Post by testube_babies on 2007-06-09
Here are two of the requirements of 3ddesktop (from the author's website):
OpenGL/Mesa (Hardware acceleration is strongly recommended)
GLX

It looks like you don't have GLX enabled.  If you post your video card specs and /etc/X11/xorg.conf file, I'm sure somebody in these forums will be able to help you.

---

