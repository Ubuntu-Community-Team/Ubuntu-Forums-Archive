---
title: "Wine"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by gamer91 on 2007-04-29
I seem to be having problems using wine - when trying to load winamp it says it cant find the arial font, any games I try to load just crash, and the macromedia suite (which is supported) just wont load, does anybody know why?

---

### Post by thefoolisme on 2007-04-29
What version of Ubuntu are you using?  What version of Wine are you using?  Is there any particular reason you're using Winamp over a native Linux installation?  What games are you trying to run?

---

### Post by Happy_Man on 2007-04-29
You need to install Microsoft Core Fonts:

```
sudo apt-get install msttcorefonts
```

---

### Post by gamer91 on 2007-04-29
I am running edgy eft, I downloaded wine using the package manager so I'd assume its the latest version. 
I want to be able to play WMA's and create/save playlists 
as for the games BF2 and virtual sailor 7

---

### Post by Happy_Man on 2007-04-29
Ubuntu can play WMA's; you need to install the correct codecs, though. Search Add/Remove for "gstreamer" and install everything codec-related that comes up. As for playlists, there are a lot of players for Linux that can do this; I'd recommend AmaroK or Exaile as a start.

---

### Post by gamer91 on 2007-04-29
what about games like battlefield - it seems it doesnt like those, on the website it mentions about open gl - is their anyway i can update/install open gl?

---

### Post by Double-X on 2007-04-29
> **gamer91 said:**
> what about games like battlefield - it seems it doesnt like those, on the website it mentions about open gl - is their anyway i can update/install open gl?

Go to application, Accessories, Terminal.
type: **glxinfo**
If you scroll up, you see something like: 
 ```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:

```

If glx vendor string says ATI or NVidia, you can try Envy.
[Ubuntu's Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

It worked for me.

---

### Post by gamer91 on 2007-04-29
I get:

"name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None"

I dont think thats good

---

### Post by gamer91 on 2007-04-29
> **Double-X said:**
> 
[Ubuntu's Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

It worked for me.

envy has set it up wrong and it now wont load ubuntu because of x org (or something like that) 

how can i recover it

---

### Post by Happy_Man on 2007-04-29
```
sudo dpkg-reconfigure xserver-xorg
```

Be sure to choose "vesa" instead of "nvidia" when it asks what graphics driver you want to use.

---

