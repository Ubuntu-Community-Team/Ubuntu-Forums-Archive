---
title: "Installing downloaded programs"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by danny71 on 2007-05-12
Hi there,

I don't know what happened to my computer, but I cannot install downloaded programs - I see them in the desktop, but I don't know how to open them.

Recently I downloaded the Ati X600 driver for Linux, the File is in the desktop, but I cannot open it.

If I open it with Text Editor, I have a message that there is a font problem. Also, I don't see it with Synaptic Package Manager.

Can you please help me?

---

### Post by aysiu on 2007-05-12
Maybe one of these might help?
[Howto: installing X800 X700 X600 X500 X300 Ati Video Cards](http://ubuntuforums.org/showthread.php?t=190133)
[HOWTO: ATI drivers](http://ubuntuforums.org/showthread.php?t=22496)

---

### Post by jiminycricket on 2007-05-12
Hi,
-EDIT-
Are you sure you don't have 3d already though?  type ```
glxinfo | grep rendering
``` into a terminal, if it's yes you might not need the ati drivers unless for intensive games.

---

### Post by danny71 on 2007-05-12
home@home-desktop:~$ glxinfo | grep rendering
Unknown device ID 5B62, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
direct rendering: Yes

Does it tell you something?

---

### Post by jiminycricket on 2007-05-12
Those extra messages are weird, but since direct rendering says 'yes', you should have 3d capability (if that's what you're aiming for).  What happens if you run 'glxgears'?

With ATI cards, there are two drivers that have their upsides and downsides, see here: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by danny71 on 2007-05-12
> **jiminycricket said:**
> Those extra messages are weird, but since direct rendering says 'yes', you should have 3d capability (if that's what you're aiming for).  What happens if you run 'glxgears'?

With ATI cards, there are two drivers that have their upsides and downsides, see here: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

I run glxgears, and besides getting a window with 3 rolling wheels, I've got the following message:

home@home-desktop:~$ glxgears
Unknown device ID 5B62, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
*********************************WARN_ONCE*********************************
File r300_render.c function r300_get_num_verts line 188
user error: Need more than 2 vertices to draw primitive QS !
***************************************************************************

---

### Post by jiminycricket on 2007-05-12
OK that means 3d is working for you then, have you tried enabling desktop effects (if that's your ultimate goal?).  I guess you would just ignore the text messages, or perhaps that should be reported to [https://bugs.freedesktop.org](https://bugs.freedesktop.org)

Seems related to [this]("https://bugs.freedesktop.org/show_bug.cgi?id=5413"), they say it was resolved yet it's odd that you would get those messages, then.

---

