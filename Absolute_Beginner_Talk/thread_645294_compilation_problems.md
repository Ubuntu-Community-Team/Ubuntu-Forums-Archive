---
title: "compilation problems"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Luksion Knight on 2007-12-19
```
:~/Desktop/quetoo-0.6.1$ make
make  all-recursive
make[1]: Entering directory `/home/linkous/Desktop/quetoo-0.6.1'
Making all in data
make[2]: Entering directory `/home/linkous/Desktop/quetoo-0.6.1/data'
Making all in baseq2
make[3]: Entering directory `/home/linkous/Desktop/quetoo-0.6.1/data/baseq2'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/linkous/Desktop/quetoo-0.6.1/data/baseq2'
make[3]: Entering directory `/home/linkous/Desktop/quetoo-0.6.1/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/linkous/Desktop/quetoo-0.6.1/data'
make[2]: Leaving directory `/home/linkous/Desktop/quetoo-0.6.1/data'
Making all in src
make[2]: Entering directory `/home/linkous/Desktop/quetoo-0.6.1/src'
Making all in .
make[3]: Entering directory `/home/linkous/Desktop/quetoo-0.6.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -pipe  -Wall -Werror   -I/include  -I/include -g -O2 -MT quetoo-gl_sdl.o -MD -MP -MF ".deps/quetoo-gl_sdl.Tpo" -c -o quetoo-gl_sdl.o `test -f 'gl_sdl.c' || echo './'`gl_sdl.c; \
        then mv -f ".deps/quetoo-gl_sdl.Tpo" ".deps/quetoo-gl_sdl.Po"; else rm -f ".deps/quetoo-gl_sdl.Tpo"; exit 1; fi
gl_sdl.c:22:17: error: SDL.h: No such file or directory
gl_sdl.c:27: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gl_sdl.c:127: error: expected ‘)’ before ‘*’ token
gl_sdl.c:329: error: expected ‘)’ before ‘*’ token
gl_sdl.c: In function ‘IN_HandleEvents’:
gl_sdl.c:379: error: ‘SDL_Event’ undeclared (first use in this function)
gl_sdl.c:379: error: (Each undeclared identifier is reported only once
gl_sdl.c:379: error: for each function it appears in.)
gl_sdl.c:379: error: expected ‘;’ before ‘event’
gl_sdl.c:381: error: ‘surface’ undeclared (first use in this function)
cc1: warnings being treated as errors
gl_sdl.c:385: warning: implicit declaration of function ‘SDL_PollEvent’
gl_sdl.c:385: error: ‘event’ undeclared (first use in this function)
gl_sdl.c:386: warning: implicit declaration of function ‘HandleEvents’
gl_sdl.c:390: warning: implicit declaration of function ‘SDL_WM_GrabInput’
gl_sdl.c:390: error: ‘SDL_GRAB_OFF’ undeclared (first use in this function)
gl_sdl.c:395: error: ‘SDL_GRAB_ON’ undeclared (first use in this function)
gl_sdl.c:403: warning: implicit declaration of function ‘SDL_GetMouseState’
gl_sdl.c:410: warning: implicit declaration of function ‘SDL_WarpMouse’
gl_sdl.c:414: warning: implicit declaration of function ‘SDL_BUTTON’
gl_sdl.c: In function ‘GL_SetIcon’:
gl_sdl.c:447: error: ‘SDL_Surface’ undeclared (first use in this function)
gl_sdl.c:447: error: ‘icon’ undeclared (first use in this function)
gl_sdl.c:448: error: ‘SDL_Color’ undeclared (first use in this function)
gl_sdl.c:448: error: expected ‘;’ before ‘color’
gl_sdl.c:449: error: ‘Uint8’ undeclared (first use in this function)
gl_sdl.c:449: error: ‘ptr’ undeclared (first use in this function)
gl_sdl.c:452: warning: implicit declaration of function ‘SDL_CreateRGBSurface’
gl_sdl.c:453: error: ‘SDL_SWSURFACE’ undeclared (first use in this function)
gl_sdl.c:460: warning: implicit declaration of function ‘SDL_SetColorKey’
gl_sdl.c:460: error: ‘SDL_SRCCOLORKEY’ undeclared (first use in this function)
gl_sdl.c:462: error: ‘color’ undeclared (first use in this function)
gl_sdl.c:463: warning: implicit declaration of function ‘SDL_SetColors’
gl_sdl.c:468: error: expected expression before ‘)’ token
gl_sdl.c:476: warning: implicit declaration of function ‘SDL_WM_SetIcon’
gl_sdl.c:477: warning: implicit declaration of function ‘SDL_FreeSurface’
gl_sdl.c: In function ‘GL_InitGraphics’:
gl_sdl.c:487: warning: implicit declaration of function ‘SDL_WasInit’
gl_sdl.c:487: error: ‘SDL_INIT_AUDIO’ undeclared (first use in this function)
gl_sdl.c:487: error: ‘SDL_INIT_VIDEO’ undeclared (first use in this function)
gl_sdl.c:488: warning: implicit declaration of function ‘SDL_Init’
gl_sdl.c:489: warning: implicit declaration of function ‘SDL_GetError’
gl_sdl.c:489: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
gl_sdl.c:492: warning: implicit declaration of function ‘SDL_InitSubSystem’
gl_sdl.c:493: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
gl_sdl.c:497: error: ‘surface’ undeclared (first use in this function)
gl_sdl.c:499: error: ‘SDL_FULLSCREEN’ undeclared (first use in this function)
gl_sdl.c:500: warning: implicit declaration of function ‘SDL_WM_ToggleFullScreen’
gl_sdl.c:513: warning: implicit declaration of function ‘SDL_GL_SetAttribute’
gl_sdl.c:513: error: ‘SDL_GL_RED_SIZE’ undeclared (first use in this function)
gl_sdl.c:514: error: ‘SDL_GL_GREEN_SIZE’ undeclared (first use in this function)
gl_sdl.c:515: error: ‘SDL_GL_BLUE_SIZE’ undeclared (first use in this function)
gl_sdl.c:516: error: ‘SDL_GL_DEPTH_SIZE’ undeclared (first use in this function)
gl_sdl.c:517: error: ‘SDL_GL_DOUBLEBUFFER’ undeclared (first use in this function)
gl_sdl.c:519: error: ‘SDL_OPENGL’ undeclared (first use in this function)
gl_sdl.c:522: warning: implicit declaration of function ‘SDL_SetVideoMode’
gl_sdl.c:523: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
gl_sdl.c:527: warning: implicit declaration of function ‘SDL_EnableKeyRepeat’
gl_sdl.c:527: error: ‘SDL_DEFAULT_REPEAT_DELAY’ undeclared (first use in this function)
gl_sdl.c:528: error: ‘SDL_DEFAULT_REPEAT_INTERVAL’ undeclared (first use in this function)
gl_sdl.c:530: warning: implicit declaration of function ‘SDL_WM_SetCaption’
gl_sdl.c:531: warning: implicit declaration of function ‘SDL_ShowCursor’
gl_sdl.c: In function ‘GL_EndFrame’:
gl_sdl.c:552: warning: implicit declaration of function ‘SDL_SetGamma’
gl_sdl.c:555: warning: implicit declaration of function ‘SDL_GL_SwapBuffers’
gl_sdl.c: In function ‘GL_ShutdownGraphics’:
gl_sdl.c:563: error: ‘surface’ undeclared (first use in this function)
gl_sdl.c:568: error: ‘SDL_INIT_EVERYTHING’ undeclared (first use in this function)
gl_sdl.c:568: error: ‘SDL_INIT_VIDEO’ undeclared (first use in this function)
gl_sdl.c:569: warning: implicit declaration of function ‘SDL_Quit’
gl_sdl.c:570: warning: implicit declaration of function ‘SDL_QuitSubSystem’
make[3]: *** [quetoo-gl_sdl.o] Error 1
make[3]: Leaving directory `/home/linkous/Desktop/quetoo-0.6.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/linkous/Desktop/quetoo-0.6.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/linkous/Desktop/quetoo-0.6.1'
make: *** [all] Error 2

```

---

### Post by macogw on 2007-12-19
Uh, what are you compiling?  It looks like the code's broken, based on the abundance of syntax errors.  The SDL.h error makes it look like you're missing come build dependencies too (did you do ./configure first?).  If it's a version of something already in the repos, you can do "sudo apt-get build-deb <package>" to get all of the build-dependencies.

---

### Post by Luksion Knight on 2007-12-19
its quetoo a quake2 engine. what do i need to run to get SDL.h?

---

