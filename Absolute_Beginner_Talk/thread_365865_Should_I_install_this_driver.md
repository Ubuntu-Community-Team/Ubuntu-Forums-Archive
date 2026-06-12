---
title: "Should I install this driver?"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by jordi_rc on 2007-02-20
Hello

I have a barebone with Xubuntu Linux installed. Runs fine. It is XCCube EX761 and has a SiS 761 graphics chip.
I know that SiS chips have not 3d acceleration support for 3d. When I use the glxinfo command I see that "direct Rendering: no" message. 

But I need 3d acceleration for some programs, not games. For Xj3d: X3D and VRML Java browser.

But as my computer runs very fast with Xubuntu (faster than Windows XP), I wonder if this is possible this solution: to install a driver that provides 3d acceleration via software rendering.

I looked at packages for this at Synaptic.
I saw I have opengl, and mesa, and SiS drivers installed, but they don't give 3d acceleration.
I saw a package named:

> 
libgl1-mesa-swrast


The description says this:

> 
This library provides a pure software rasteriser; it does not provide
a direct rendering-capable library, or one which uses GLX.  For that,
please see libgl1-mesa.

On Linux, this library is also known as libGL or libGL.so.1.


I wonder if I can install this and get programs that require 3d acceleration work, even if they go to a slow framerate.

Would it be dangerous to my system to install this?
Will this fix the problem?
May this be incompatible with my other graphics drivers?

Thanks for any advice or info.

Jordi R. Cardona.

---

### Post by tgalati4 on 2007-02-21
There's and X11proto-gl-dev package that is supposed to allow Opengl rendering.  What is the output of:  glxgears -printfps

If you see gears and get a number like 60 fps then you are doing software rendering.  If you get 1200 or 3000 fps then you are using hardware rendering.  If it crashes your machine--then you have been warned.

---

### Post by jordi_rc on 2007-02-21
Thanks tgalati4,

I did what you said and get a totally different resul:

I get aprox. 390-400 fps and my machine doesn't crash at all.

Jordi

---

### Post by tgalati4 on 2007-02-21
Well, you have really fast software 3D rendering or really slow hardware rendering.  Try loading Blender (install it via Synaptic Package Manager) and let us know how useable it is on your system.  If it is too slow to be useable, then time to purchase a good video card that has decent Linux support.  Search the forum for lots of recommendations on video cards.

Also, Google earth is a good test of 3D rendering.  It's either useable or it's dreadfully painful to use.

My understanding is that hardware 3D rendering is called "accelerated 3D rendering"  therefore there is no such thing as accelerated software rendering.  OpenGL will perform software 3D rendering, but by definition it is not accelerated, nor could it ever be considered accelerated.

glxgears -printfps is a simple test that lets you know how well your machine processes 3D (software or hardware, it doesn't care).  I've seen some posts (do a search on glxgears) that report 12,000 to 20,000 fps.  Now that is fast.

I am writing this with a 1GHz powerbook (ATI Mobile Radeon 9600, 64MB VRAM) and I get 2920 frames per second running glxgears under an XDarwin window (Xserver running on top of Mac Tiger 10.4.8).  Google Earth is quite useable with this performance.  Next time I reboot I will try it under PPC Ubuntu and see if it is any different.

---

### Post by jordi_rc on 2007-02-21
Hello, thanks for replying again

In fact  I installed some 3d software, like WhiteDune to view vrml models, and played armagetron, and used art of illusion, a java modeller.
I also run Xj3d the X3D browser wich uses opengl, but I don't get textures in that.

They said me in Web3d.org that maybe my SiS card has not hardware 3d because it says in glxinfo: "Direct rendering: no".

So I thought if I can force it to render by software or I am missing something.

I don't want to install any video card because this pc is going to be a server in near future, and less is more.

Jordi

---

