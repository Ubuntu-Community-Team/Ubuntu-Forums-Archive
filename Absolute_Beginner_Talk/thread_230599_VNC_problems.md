---
title: "VNC problems"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by helino on 2006-08-06
Hi, when I use VNC, the only thing I see through vncviewer is the terminal, then I can launch apps through the terminal. I want to be able to see the desktop, and launch apps through the menu. Is that possible?

thanks for a great os and an even greater community

---

### Post by x64Jimbo on 2006-08-06
I recommend using x11vnc. It's a package that installs the VNC server in a similar fashion to how it installs on a Windows machine. Whatever is on the screen is what the remote client sees. Keep in mind that *nix is designed to be multi-user, and thus is having to overcome some hurdles to become usable as a desktop (or laptop) OS.

---

### Post by eXisor on 2006-08-06
I second the x11vnc suggestion, but suggest you do not install it from the ubuntu archives (if you have, then uninstall it). I recommend you get your hardware specific bin from the developer (they are newer and faster). The 12/07/2006 versions are stable.

[http://www.karlrunge.com/x11vnc/bins/](http://www.karlrunge.com/x11vnc/bins/)

Just copy the one you need to /usr/local/bin and rename it to x11vnc.

---

### Post by helino on 2006-08-06
I installed it from Synaptic ](*,) Although it works great, except for one thing. When I exit vncviewer and wants to connect again, I get an error. Then I have to ssh in, kill x11vnc and then start it again. Then can I connect using vncviewer. Is there a solution to this?

---

### Post by eXisor on 2006-08-06
Yes there is. One of the x11vnc parameters (I can't remember which offhand) tells it to connect to the current session, and another tells it to use a shared connection, both options will let you disconnect/reconnect to the current session.

Check out the extensive help on the developers website [www.karlrunge.com/x11vnc](www.karlrunge.com/x11vnc)

PS: I find his binaries are quicker than the ubuntu binaries.

---

### Post by eXisor on 2006-08-06
you need to start x11vnc with -forever

---

