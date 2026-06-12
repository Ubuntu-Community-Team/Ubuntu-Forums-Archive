---
title: "Odd Desktop Effects error (also in Beryl): disappearing window title bars"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Her Ghost on 2007-04-21
Hi, 

I'm having an odd problem, and was wondering if this is something anyone else has come up against before:

Upgraded to Feisty and everything is fine, so I decided to have a look at the Desktop Effects.  As soon as I turn them on, all my windows lose their title bars, so I can't minimise, close or move them.  When I turn it off, they come back and everything is normal.

I just installed Beryl too, and the exact same thing happened.

I am using an nVidia 7600 GT gfx card.

---

### Post by DSn0wMan on 2007-04-21
This happens to me when I forget to add:


 Option "AddARGBGLXVisuals" "True"


Here is what the beryl wiki suggests - 

[http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia) 

My windows don't have any decorations (title bar, resize handles, minimize/maximize/close buttons)

Before try this, make sure that you have the window decoration enabled at your beryl-manager's settings. It can be the problem.

You can try these solutions by modifying sections of /etc/X11/xorg.conf :


1. Try changing DefaultDepth to 24 in the ' Screen ' section.

2. Delete, if existing, these entries in ' Section "Module" ' :

 Load "dri"
 Load "GLCore"

3. Add this entry in ' Section "Module" ' :

 Load "glx"

4. Change in Section "Device" the ' Driver "nv" ' entry to :

 Driver "nvidia"

5. Add this entry in ' Section "Screen" ' :

 Option "AddARGBGLXVisuals" "True"

6. Add this section at the end of the file:

 Section "Extensions"
     Option "Composite" "Enable"
 EndSection

---

### Post by Psychomechanix on 2007-04-22
I am having the exact same issue here except I have never installed Beryl or any other such graphics software. Mine started doing this when I went to dual monitors. I set up TwinView in my NVidia control panel and everything works fine except when I enable Desktop Effects the title bars go missing and I can't move or resize any windows. Desktop effects worked great when I was just using one monitor.

Any ideas out there for us?

---

### Post by Her Ghost on 2007-04-22
DSn0wMan:

Thank you - those suggestions worked perfectly!

Psychomechanix:

I am using twin monitors on nVidia too, and the changes to the xorg.conf file mentioned by DSn0wMan fixed it for me.  I don't think that my problem (and the solution) were Beryl specific, because it affects Desktop Effects too.  Give the suggestions in the previous post a try

---

