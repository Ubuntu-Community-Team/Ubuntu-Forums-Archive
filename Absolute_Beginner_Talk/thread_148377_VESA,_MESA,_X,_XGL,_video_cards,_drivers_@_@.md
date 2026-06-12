---
title: "VESA, MESA, X, XGL, video cards, drivers @_@"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Jucato on 2006-03-21
VESA, MESA, X, XGL, OpenGL, GLX, video cards, drivers... 

Can somebody explain to me what all these are? What are their purposes? How they fall into place in the Linux system?

I looked into wikipedia, but all I got are definitions, sometimes in very technical terms. But I don't understand how they interact with one another, especially when XGL is involved... ](*,)

---

### Post by dcstar on 2006-03-22
[QUOTE=Fenyx]VESA, MESA, X, XGL, OpenGL, GLX, video cards, drivers... 

Can somebody explain to me what all these are? What are their purposes? How they fall into place in the Linux system?

I looked into wikipedia, but all I got are definitions, sometimes in very technical terms. But I don't understand how they interact with one another, especially when XGL is involved... ](*,)[/QUOTE]
VESA is a basic video hardware specification that most (if not all) video cards have built into them - so at worst you can use this if all else fails.

X is the graphical system that Unix and Linux use, the Gnome and KDE desktops run on top of X.

Video cards are the hardware that convert data representing what you see on your screen into the correct format the video monitors need to have it sent along the cable and displayed to you.

Drivers are what various operating systems (Linux, Windows et al) use to "drive" various bits of hardware (like video cards). Drivers provide the interface between generic commands (like "Draw me a blue dot in the top left hand corner of the screen") and the specific commands each individual manufacturers piece of hardware requires (like "XYZ123" to draw the dot) to actually do what the computer wants it to.

---

### Post by Jucato on 2006-03-22
Ok, so far I understand:
Video card - Driver - kernel - X

Where does VESA fall into that? is it a sort of driver that could be used?

THanks for the info. Now I just have to wait for XGL, OpenGL, and MESA. :D

---

### Post by wout.wepsait.com on 2006-03-22
**VESA**

Used by almost all video card makers for easy graphics without specific graphics drivers for that video card.

**OpenGL**

Is an industry standard for 3d graphics. Almost al 3d graphics cards have hardware accelration for this system. You need graphics drivers for this to work

**MESA**

Implements opengl for the linux OS.

**XGL**

The X graphical system which talks opengl to the graphics card. By doing so everything is hardware accelerated and thus takes some load off of the processor.


These are extremely short descriptions and there for not fully cover the systems.

---

