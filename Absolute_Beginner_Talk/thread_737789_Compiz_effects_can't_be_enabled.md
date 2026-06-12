---
title: "Compiz effects can't be enabled"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by lorderico on 2008-03-27
I have an ATI radeon 9600 card, some how the first time I installed ubuntu 7.10 I got compiz fusion to work.  It stopped working (don't know why), so I reinstalled ubuntu.  The first time I logged in, it had me use a restricted driver from ATI (same as first time I installed Ubuntu).  When I installed compiz fusion, the error was "The composite extension could not be found"  I followed other forums, and changed the
Option		"Composite"	"0"
to
Option		"Composite"	"2"
in the config file.  Now I get the error "Desktop Effects could not be enabled".  When I do it in a terminal, I get:

leo@Eric-desktop:~$ compiz --replace &
[1] 5494
leo@Eric-desktop:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e51 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

All of my settings seem write.
leo@Eric-desktop:~$  fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6473 (8.37.6)

leo@Eric-desktop:~$ glxinfo | grep direct
direct rendering: Yes

Let me know if you want to see all or part of the /etc/x11/xorg.conf file.
Thanks,
Eric

---

### Post by cisforcojo on 2008-03-27
ATI can be a bit tricky to get working with Compiz, but it appears that XGL is your problem.

This should help you: [http://ubuntuforums.org/showthread.php?t=580748&highlight=howto+ati+xgl+compiz](http://ubuntuforums.org/showthread.php?t=580748&highlight=howto+ati+xgl+compiz)

Also of note, I believe it should be:
```
Option "Composite" "1"
```

From what I understand, it's a TRUE/FALSE setting so "2" would be what... "MAYBE"? :p

---

### Post by Saint Angeles on 2008-03-27
the newest fglrx from the ati website works great for me

i'll atatch my xorg.conf so you can see.

---

### Post by FuturePilot on 2008-03-27
You probably need to install XGL.
```
sudo apt-get install xserver-xgl
```

---

### Post by lorderico on 2008-03-28
Thank you cisforcojo.  I followed the instructions on that page you gave me, and now it works fine.  You can always count on Ubuntu forums.

Thank yo all for answering, I appreciate it,
Eric

---

### Post by cisforcojo on 2008-03-28
Glad to help!

---

