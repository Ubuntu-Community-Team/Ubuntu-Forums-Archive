---
title: "libSDL problem, OpenGL software"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by Jc1991 on 2006-12-10
Whenever I try to run anything that uses OpenGL for rendering, the software refuses to run and I recieve this error message: error while loading shared libraries: libSDL-1.3.so.0: cannot open shared object file: No such file or directory.

My graphics card is an Nvidia GeForce4 4200 Go, using driver version 1.0-8776. (The newest version obtained via Synaptic.)

I have the libsdl1.2debian and libsdl1.2debian-all packages installed.

Does anyone here know what the problem is?

---

### Post by Jc1991 on 2006-12-10
I've been doing some experimentation with both the generic nv driver and the nvidia driver available via Synaptic.

Both drivers result in the above error with the application I'm testing, but the nv drivers work semi-correctly with another openGL app. (The app runs, but does so extremely slowly. It's impossible to use because the mouse lags horribly.) The nv drivers also break the speed slider for the xscreensaver app.
The nvidia driver breaks the xscreensaver app entirely and errors on all OpenGL apps. (Again, as far as I can tell.)

---

