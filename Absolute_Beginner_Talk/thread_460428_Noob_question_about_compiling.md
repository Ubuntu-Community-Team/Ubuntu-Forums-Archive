---
title: "Noob question about compiling"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by mystman on 2007-05-31
I'm learning SDL currently and I've been trying to compile my example programs.  I can do it in Windows but I can't compile it in Ubuntu.  I wanted to know what GCC parameters I should use to compile the following:

```
#include "SDL.h"
bool        WINDOW_ISALIVE    = true;
const int   WINDOW_HEIGHT     = 600;
const char* WINDOW_TITLE      = "Teh Game";
const int   WINDOW_WIDTH      = 800;

int main (int argc, char **argv){
	// Initialize SDL
	SDL_Init (SDL_INIT_VIDEO);
	// Set Window Properties
	SDL_Surface* screen = SDL_SetVideoMode (WINDOW_WIDTH,WINDOW_HEIGHT,0,SDL_HWSURFACE | SDL_DOUBLEBUF);
	// Set Window Caption
	SDL_WM_SetCaption (WINDOW_TITLE,0);
	while (WINDOW_ISALIVE){}
	// Kill SDL
	SDL_Quit();
	return (0);
	}
```

---

### Post by PandaGoat on 2007-05-31
Assuming you know how to use gcc: -lSDL

---

### Post by mystman on 2007-05-31
I got the following error.  Do I need any libraries other than gcc, libsdl1.2-dev, and libsdl1.2debian-all?


```
andy@andy:~$ gcc -lSDL sdltest.cpp -o sdltest
/tmp/ccCITRLT.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```

---

### Post by PandaGoat on 2007-05-31
Yeah you need to install the libraries for SDL to use them.

Here's a good page.  It lists the libs you need to install to use everything in SDL and it has the command line compile at the bottom.
[http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development]("http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development")

---

### Post by mystman on 2007-05-31
Thanks!  That fixed my problem.

---

