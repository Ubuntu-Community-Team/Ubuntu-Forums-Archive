---
title: "Help! I've managed to kill direct rendering"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by jimbob1977 on 2007-05-09
Help! I've managed to kill direct rendering on my install of Ubuntu
Fiesty!

I had the fglrx drivers installed and everything was working fine - fgl_glxgears
 showed me lovely spinning gears ... until
- stupidly I thought my gfx card wasn't rendering as fast as it should
(ATI 9600 Saphire 128meg) I typed the following command into the
console:

 sudo aticonfig --overlay-type=Xv

Since then - direct rendering fails no matter what I do!

Can anyone help me? When I type fglrxinfo I get:-
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600
OpenGL version string: 2.0.6334 (8.34.8)

And fgl_glxgears gives:-
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Error: couldn't get fbconfig

Here's my Xorg.conf file (attached)

I've also attached my Xorg.0.log where it seems have a problem with the
bus id? I didn't think this was a Xorg.conf file problem but I'm not so
sure now - can anyone shed any light? Cheers

---

### Post by dcstar on 2007-05-09
> **jimbob1977 said:**
> Help! I've managed to kill direct rendering on my install of Ubuntu
Fiesty!

I had the fglrx drivers installed and everything was working fine - fgl_glxgears
 showed me lovely spinning gears ... until
- stupidly I thought my gfx card wasn't rendering as fast as it should
(ATI 9600 Saphire 128meg) I typed the following command into the
console:

 sudo aticonfig --overlay-type=Xv

Since then - direct rendering fails no matter what I do!

Can anyone help me? When I type fglrxinfo I get:-
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600
OpenGL version string: 2.0.6334 (8.34.8)

And fgl_glxgears gives:-
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Error: couldn't get fbconfig

Here's my Xorg.conf file (attached)

I've also attached my Xorg.0.log where it seems have a problem with the
bus id? I didn't think this was a Xorg.conf file problem but I'm not so
sure now - can anyone shed any light? Cheers

Edit the xorg.conf file and comment out the overlay lines.

---

### Post by jimbob1977 on 2007-05-09
Thanks - it seems to have got a bit further but still no direct render - I've posted the latest log file as an attachment again - thanks for your help!

---

### Post by RavanH on 2007-05-14
Are you loggin into a session with XGL? If so, that might explain it...

What's the output of the command
> echo $DISPLAY
in a terminal window?

And
> glxinfo | grep direct

If the output shows anything different for the name of display than :0.0 (probably :1.0), try
> DISPLAY=:0 fgl_glxgears

Does that work for you? If so, I'm in the same boat as you are, but do not have a solution... :(

---

### Post by cadamr on 2007-05-17
try 

```

sudo aticonfig --ovt=opengl

```

---

