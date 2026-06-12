---
title: "3dDesktop"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by codecaine on 2006-04-10
Im trying to run 3dDesktop but im getting an error. "Xlib: Extension "GLX" missing on display ":0.0" anybody know how I can fix this?

---

### Post by trent dillman on 2006-04-10
You need glx running...

What graphics board do you have?

---

### Post by codecaine on 2006-04-10
NVIDIA  GeFore Go 7300

---

### Post by trent dillman on 2006-04-10
First, are you using 'nv' or 'nvidia' driver in xorg.conf?

You should install nvidia-glx, switch nv to nvidia and comment out GLcore as a module in /etc/X11/xorg.conf

---

### Post by professor_chaos on 2006-04-10
make sure your using the nvidia driver. Check your /etc/X11/xorg.conf file for that and then make sure glx is enabled in that file.
```
Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
#Load "dri"
#Load “GLcore”
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
```

then try enabling glx

```
nvidia-glx-config enable
```

---

### Post by codecaine on 2006-04-10
nv when I tried to put nvidia my screen is black at start up can't do anything

---

### Post by trent dillman on 2006-04-10
Did you install nvidia-glx ? Did you comment glcore and dri?

---

### Post by codecaine on 2006-04-10
Yes im going to try to install NVIDA from the site see if that works.

---

### Post by codecaine on 2006-04-12
damn just can't get this accel to work in unbuntu :(

---

### Post by taurus on 2006-04-12
Why don't you check out this post, [http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074), on how to install the latest nVidia driver for your card!!!  Then, glxgears will work...

---

### Post by varunmittal91 on 2006-04-13
I get this message when i try running ***_3ddektop_***

varun@ubuntu:~$ 3ddesk
Attempting to start 3ddesktop server.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

what should i do next

---

### Post by Christmas on 2006-04-13
```

christmas@cpp:~$ 3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
christmas@cpp:~$ 3ddesk
```

It works for me. What is the use of this 3ddesktop anyway? After I select one of the 3d workspaces it brings it in front and then to enter the 3d session again I have to type again in the terminal 3ddesk...

---

### Post by xenmax on 2006-04-13
varun, what is your graphics card?

---

