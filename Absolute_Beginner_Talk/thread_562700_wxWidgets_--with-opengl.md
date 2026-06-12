---
title: "wxWidgets --with-opengl"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Ryuusen on 2007-09-29
i'm trying to compile aegisub from source and need wxwidgets-2.8.4 with opengl support. when i download and compile the source for wxwidgets, on the ./config i do 

"../configure --enable-unicode --with-opengl --with-stc" everything goes fine until it tries to get openGL support, i get

"checking for OpenGL headers... found in /usr/include
checking for GL/gl.h... yes
checking GL/glu.h usability... no
checking GL/glu.h presence... no
checking for GL/glu.h... no
configure: error: OpenGL libraries not available



i'm in ubuntu fiesty fawn

---

### Post by Bothered on 2007-09-29
You're missing the OpenGL development files. I think you need to install the "libgl1-mesa-dev" package.

---

### Post by Ryuusen on 2007-09-29
i run sudo apt-get install libgl1-mesa-dev     and it says it's already the newest version. and that it's set to manual installed.

---

### Post by Perfect Storm on 2007-09-29
```
sudo aptitude install libglu1-mesa-dev
```

Should do it.

You might also add --prefix=/usr to add it correct installation path.

---

### Post by Ryuusen on 2007-09-29
awesome, thanks AI

---

