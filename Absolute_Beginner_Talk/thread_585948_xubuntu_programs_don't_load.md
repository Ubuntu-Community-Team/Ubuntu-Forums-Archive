---
title: "xubuntu: programs don't load"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by tablaboi on 2007-10-21
Just installed xubuntu gusty off the live cd. For some reason, few of the programs seem to actually work. For instance, if I try to open the network manager (applications--system--network), i get a loading icon next to my mouse pointer, and then the loading icon goes away and nothing loads. None of the games seem to load either. Is anybody else having the same problem? Any solutions found yet?

---

### Post by Flying caveman on 2007-10-22
sounds like it could be a video driver problem, if you don't have your graphics driver installed that can happen.

open a terminal and type > glxinfo

Is direct rendering enabled?

sherman@sherman-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering:[COLOR="Red"] Yes[/COLOR]
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation.............>>

---

### Post by tablaboi on 2007-10-22
sweet so that is the problem: here's what it says:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)



How do i fix that (i.e. turn on direct rendering)? 

Thanks a lot for your help so far.

---

### Post by 3rdalbum on 2007-10-22
What are some of the other programs that won't open? You could try running them from the terminal, and if you get any error messages post them here.

---

### Post by LanDan on 2007-10-22
you could try the restricted drivers manager under system

if that works at least ;)

---

### Post by tablaboi on 2007-10-22
Solution Found:

I have no idea why this worked, but I changed my internet connection preferences from automatic configuration to manual configuration, and that seemed to make everything work properly. Now all my programs load. 

thanks for your help you guys.

---

### Post by Flying caveman on 2007-10-22
I'm not sure why that would have done anything, but i'm glad you got it working. 

Here's a link you might find useful [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/).

Also: you could google for ubuntu guide, but the gutsy one doesn't look like its finished yet, but there's plenty of good info in the ubuntu dapper guide that more than likely still works the same.  [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by tablaboi on 2007-10-22
thx for the links flying caveman :)

---

