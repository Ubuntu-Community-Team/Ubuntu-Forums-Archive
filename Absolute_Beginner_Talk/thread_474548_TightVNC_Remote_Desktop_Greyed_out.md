---
title: "TightVNC Remote Desktop Greyed out"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Stew_2 on 2007-06-15
Hi,

Using latest version of ubuntu + tightvnc server. 
Trying to attach to the tightvnc server (from another unbuntu computer) using vncviewer serverip:1 typing in my password for the vnc server. (the one that you use while setting up the vnc server).
Everything seems to be fine after i type in the password and press "ok". I get a screen, and a mouse. But everything is grey! Like a grey wallpaper/background. I can move the mouse around, but i cant give any commands to the vnc desktop. I dont see any icons or anything... :(

Help would have been really nice here :) I have been trying to solve this for several nights  a row now, and my daily work is getting punished for that, since i dont get enough sleep :)

CHeers,

Stefan

---

### Post by Damanther on 2007-06-15
I use vnc4server and a tightvnc client on my machine.

I had a similar problem. 3 things you can try that helped me.

1st. Check the parameters of the vncserver and make sure the fonts path is correct for your machine.
2nd. Depending on your install, there is a .vnc/.vncstartup file that should have been created that tells your server which display manager to start. I think the default is twn&. You probably want that to be gdm&.
3rd. Restart the machine after you've enabled your vncserver( simple restart of xinetd did not do the trick for me)

Also, some other helpful coments on this thread

[VNC HOWTO]("http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc4server+resumable")

---

