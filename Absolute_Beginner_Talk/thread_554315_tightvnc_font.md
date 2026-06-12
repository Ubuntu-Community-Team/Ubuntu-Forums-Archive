---
title: "tightvnc font"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Eagle784 on 2007-09-18
I'm running ubuntu 6.0.6 LTS on an i386 remote server in .de. I've installed tightvnc via apt-get install tighvnc; however, when I try to run it with tightvnc :1, I Get the following error:
Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the tightvncserver script.
Couldn't start Xtightvnc process.

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
MAXSOCKS=1000
19/09/07 04:10:04 Xvnc version 3.3.tight1.2.9
19/09/07 04:10:04 Copyright (C) 1999 AT&T Laboratories Cambridge.
19/09/07 04:10:04 Copyright (C) 2000-2002 Constantin Kaplinsky.
19/09/07 04:10:04 All Rights Reserved.
19/09/07 04:10:04 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
19/09/07 04:10:04 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
19/09/07 04:10:04 Desktop name 'X' (xxx:1)
19/09/07 04:10:04 Protocol version supported 3.3
19/09/07 04:10:04 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/share/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/share/X11/fonts/misc/' not found - ignoring
Font directory '/usr/share/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/share/X11/fonts/100dpi/' not found - ignoring

Fatal server error:
could not open default font 'fixed'
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
MAXSOCKS=1000
19/09/07 04:10:05 Xvnc version 3.3.tight1.2.9
19/09/07 04:10:05 Copyright (C) 1999 AT&T Laboratories Cambridge.
19/09/07 04:10:05 Copyright (C) 2000-2002 Constantin Kaplinsky.
19/09/07 04:10:05 All Rights Reserved.
19/09/07 04:10:05 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
19/09/07 04:10:05 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
19/09/07 04:10:05 Desktop name 'X' (xxx:1)
19/09/07 04:10:05 Protocol version supported 3.3
19/09/07 04:10:05 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/X11/fonts/misc/' not found - ignoring
Font directory '/usr/share/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/share/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/share/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/share/X11/fonts/100dpi/' not found - ignoring

Fatal server error:
could not open default font 'fixed'

I've heard people casually just say to fix the font path, but I couldn't figure out how to do it. (first time using linux)  If anyone has some easy instructions I'd appreciate it.

---

### Post by jnorth on 2007-09-18
Try this... 50/50 chance it can help.```
sudo apt-get install --reinstall xfonts-base
```Post back if not...

---

### Post by Eagle784 on 2007-09-18
> **jnorth said:**
> Try this... 50/50 chance it can help.```
sudo apt-get install --reinstall xfonts-base
```Post back if not...

Worked! Thank you!

---

### Post by jnorth on 2007-09-18
> **Eagle784 said:**
> Worked! Thank you!

NP - I like the short answers that work :)

---

