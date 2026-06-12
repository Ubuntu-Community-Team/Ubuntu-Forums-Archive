---
title: "xfce4 loads metacity instead of xfwm4 by default."
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by jw5801 on 2007-12-20
I've used Gnome for quite a while now and I've recently been experimenting with other desktop environments. I'm having an issue with XFCE4 loading metacity rather than XFWM4. I'm new to the environment so I'm not entirely sure where to start with trying to debug the problem. XFWM4 starts fine once I've killed metacity, but it's annoying having to do it every time I log in, and I'd prefer not to run a script on login that kills metacity and starts xfwm4. Has anyone had this issue and managed to fix it, or can point me in the right direction?

---

### Post by capink on 2007-12-20
Try this: reboot you pc and make sure you unchek the box that says "save session for future logins"

---

### Post by DarKnyht on 2007-12-20
I had the same issue until I had Xfce4 save my session information.  For me it caused a session screen to open before bringing up the desktop but it is better than having metacity running automatically.

Btw, I stopped having these problems when I killed metacity in gnome (which I use more than Xfce4) and switched gnome over to xfwm4.  I personally, like the look of gnome, but want the compositing of xfwm4.

---

### Post by jw5801 on 2007-12-20
Ok, after some investigation I have some more information! Since I use both Gnome and Xfce4, Xfce4 is running the startup scripts that Gnome would also run, namely the script to start compiz. Since compiz failed in the desktop environment, it would go to the fallback window manager, metacity. After some tinkering compiz now runs in Xfce4 (albeit without any window decorations), however I'd like to stop Xfce4 from running the compiz script on login, but keep Gnome running it. Does anyone know if that's possible? And if so how I would go about it.

---

