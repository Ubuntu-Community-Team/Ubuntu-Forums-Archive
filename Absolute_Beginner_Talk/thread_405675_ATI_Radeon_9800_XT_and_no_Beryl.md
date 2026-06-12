---
title: "ATI Radeon 9800 XT and no Beryl"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by bizarrosephiroth on 2007-04-09
OK - I just tried this and well I don't really know what is going on.  I tried to start beryl afterwards and but it won't start.

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  33
  Current serial number in output stream:  33

glxinfo | grep rendering
direct rendering: No

Is that supposed to happen? (I don't know the reason for the two lines
 "# causes fglrx to fail and mesa drivers to load
blacklist ati-agp" 

I have a ATI Radeon 9800 XT --- and all I want is to be able to run beryl with the best graphics possible to this video card.

---

### Post by freebird54 on 2007-04-10
bizarrosephiroth, doesn't even look as if the fglrx driver has even been loaded on your system.  Try this to see where we have to start:

```
lsmod | grep fglrx
```

which should result in something like this

```
freebird@nest:~$ lsmod | grep fglrx
fglrx                 540004  11 
agpgart                35400  2 fglrx,via_agp

```

How did you install fglrx?  Did you use this link?
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9)

We can 'walk' you through it, if we know your starting point...

---

### Post by adampyre on 2007-04-24
Hi. I have an ATI x1300 on my desktop and I'm in the same boat. I did look at fglrx and it looks like your screenshot...... any suggestions on starting beryl? It is installed, but when I attempt to start the winow manager it seems like it's trying to load then stops and unloads/falls back to metacity. thanks!

---

