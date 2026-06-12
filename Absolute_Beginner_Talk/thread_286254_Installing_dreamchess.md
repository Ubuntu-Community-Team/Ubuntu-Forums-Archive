---
title: "Installing dreamchess"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by BdON003 on 2006-10-27
I am using Edgy and am trying to get dreamchess installed.  I untar'd it and ran ./configure, it looked like everything was normal(I'm still pretty new to this) except it said ```
User interface driver requirements:

sdlgl
-----

  Requirement  | Found
------------------------
"SDL_image.h"  |  no
"SDL_opengl.h" |  no
libSDL         |  no
libSDL_image   |  no
libGL          |  no

Supported:        no
Build:            no

You can now run `make'.


```
But then when I run 'make' I get a bunch of errors like (this is a short exerpt): ```
ui_sdlgl.c:458: error: ‘SDL_HWPALETTE’ undeclared (first use in this function)
ui_sdlgl.c:463: error: ‘SDL_FULLSCREEN’ undeclared (first use in this function)
ui_sdlgl.c:468: error: ‘SDL_HWSURFACE’ undeclared (first use in this function)
ui_sdlgl.c:470: error: ‘SDL_SWSURFACE’ undeclared (first use in this function)
ui_sdlgl.c:473: error: ‘SDL_HWACCEL’ undeclared (first use in this function)
ui_sdlgl.c:485: error: ‘SDL_DISABLE’ undeclared (first use in this function)
ui_sdlgl.c:489: error: ‘joy’ undeclared (first use in this function)
ui_sdlgl.c: In function ‘sdlgl_exit’:
ui_sdlgl.c:656: error: ‘texture_t’ has no member named ‘id’
ui_sdlgl.c:658: error: ‘joy’ undeclared (first use in this function)
make[4]: *** [ui_sdlgl.o] Error 1
make[4]: Leaving directory `/home/bdon/Desktop/dreamchess-0.1.0/src/ui_sdlgl'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/bdon/Desktop/dreamchess-0.1.0/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bdon/Desktop/dreamchess-0.1.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bdon/Desktop/dreamchess-0.1.0'
make: *** [all] Error 2

```
Any help?

---

### Post by Marsolin on 2006-10-27
Try installing the following packages first, and then reinstalling DreamChess.

libgl1-mesa-glx
libglu1-mesa
libsdl-mixer1.2
libsdl1.2debian

---

### Post by BdON003 on 2006-10-28
Thanks, but it didn't work.  All of those were already installed and up to date.  I do get something weird when untar'ing, I don't think it affects much but it says: ```
tar: dreamchess-0.1.0/ChangeLog: time stamp 2038-01-18 21:14:07 is 985471421.601214 s in the future
``` But it still makes the directory Dreamchess-0.1.0

---

### Post by Marsolin on 2006-10-28
You are correct in thinking that the timestamp message would not make a difference. I wonder if [DreamChess]("http://linuxappfinder.com/package/dreamchess") actually needs the source for sdlgl instead of just having it installed since it listed some header files.

---

### Post by BdON003 on 2006-10-28
I installed 'libsdl-gfx1.2-dev' and now after ./configure it displayes ```
User interface driver requirements:

sdlgl
-----

  Requirement  | Found
------------------------
"SDL_image.h"  |  no
"SDL_opengl.h" |  yes
libSDL         |  yes (-L/usr/lib -lSDL -lpthread)
libSDL_image   |  yes (-lSDL_image)
libGL          |  yes (-lGL -lGLU)

Supported:        no
Build:            no

You can now run `make'.


``` I looked up SDL_image on google and found a tar file, I had to install tiff-3.8.2 first, but I got SDL_image installed, but it didn't change anything except make everything really slow.  I'm about to give up unless anyone has any suggestions

---

### Post by Marsolin on 2006-10-28
There is a libsdl-image1.2-dev package.  Maybe that's the missing piece.

---

### Post by BdON003 on 2006-10-29
> **Marsolin said:**
> There is a libsdl-image1.2-dev package.  Maybe that's the missing piece.
Beautiful, that did it.  Thanks a lot for all your help

---

