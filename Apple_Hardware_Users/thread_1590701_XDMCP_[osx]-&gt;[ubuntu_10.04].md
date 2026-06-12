---
title: "XDMCP [osx]-&gt;[ubuntu 10.04]"
date: 2010-10-08
forum: Apple Hardware Users
---

### Post by psicomant on 2010-10-08
Hi to all!
I have a problem with XDMCP service.

I want to access a remote server with ubuntu 10.04 from my osx machine (10.6.04), using a login window instead of VNC.

I follow [**this thread**]("http://ubuntuforums.org/showpost.php?p=8204519&postcount=3") to setting up XDMCP.

After I tried to connect myself with 
[COLOR="Blue"]Xnest :1.0 -query my_host[/COLOR]
and I obtain a window all black and those messages:
> (EE) AIGLX error: dlopen of /usr/X11/lib/dri/swrast_dri.so failed (dlopen(/usr/X11/lib/dri/swrast_dri.so, 5): image not found)
(EE) GLX: could not load software renderer
(EE) XKB: Couldn't open rules file /usr/X11/share/X11/xkb/rules/base
(EE) XKB: No components provided for device Virtual core keyboard
Couldn't get keyboard.


In alternative I tried this command
[COLOR="Blue"]/usr/X11R6/bin/X -q my_host[/COLOR]
obtaining
> launch_msg("CheckIn") IPC failure: Operation not permitted



I'm confused and really need some help!! :confused:

Thank you for attention, i hope in a response! [-o<

Bye

---

### Post by psicomant on 2010-10-18
Some answer?

[-o< please help me!

---

