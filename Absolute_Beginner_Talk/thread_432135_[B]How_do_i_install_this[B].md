---
title: "[B]How do i install this[/B]"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-05-03
I just downloaded this game GNUfo.tgz what code do i need to put into the Terminal to install it.
Please Help

---

### Post by taurus on 2007-05-03
Make sure you are in the same directory as the file, then run

```
tar xvzf GNUfo.tgz
cd GNUfo
ls -la
```
and post the output of the last command here.

---

### Post by microsoft92sucks on 2007-05-03
justin@EggHead:~/Desktop/GNUfo$ ls -la
total 92
drwxr-xr-x 5 justin justin  4096 2001-05-08 13:09 .
drwxr-xr-x 4 justin justin  4096 2007-05-03 18:17 ..
drwxr-xr-x 3 justin justin  4096 2001-03-12 15:28 bmp
drwxr-xr-x 2 justin justin  4096 2001-05-04 21:36 data
-rw-r--r-- 1 justin justin  1522 2001-03-26 16:43 direc_enemi.cpp
-rw-r--r-- 1 justin justin 16589 2001-03-26 16:57 main.cpp
-rw-r--r-- 1 justin justin   780 2001-02-21 18:57 Makefile
-rw-r--r-- 1 justin justin  4658 2001-05-04 21:58 obj_enemi.cpp
-rw-r--r-- 1 justin justin  4338 2001-01-16 17:06 other.cpp
-rw-r--r-- 1 justin justin   819 2001-01-04 19:53 README
drwx------ 2 justin justin  4096 2001-05-04 21:29 SDLSprite-1.2
-rw-r--r-- 1 justin justin  1348 2001-02-21 19:17 starship.cpp
-rw-r--r-- 1 justin justin  5710 2001-03-25 15:08 tilebg.cpp
-rw-r--r-- 1 justin justin  2802 2001-03-25 14:47 tilebg.h
-rw-r--r-- 1 justin justin  1010 2001-05-04 21:59 TODO
-rw-r--r-- 1 justin justin  2955 2001-03-26 16:56 ufo.h
justin@EggHead:~/Desktop/GNUfo$ 



thats what it said after i put in the code 
thanks for the help

---

### Post by taurus on 2007-05-03
What does the README say anyway?

```
more README
```
Hit space bar for the next 24 lines.

---

### Post by microsoft92sucks on 2007-05-03
here what ur code brought up
justin@EggHead:~/Desktop/GNUfo$ more README
GnuFo.

A space invader. 

You need SDL ( [http://www.libsdl.org](http://www.libsdl.org) )
I have include the SDLSprite 
( [http://membres.tripod.fr/edorul/Other.htm](http://membres.tripod.fr/edorul/Other.htm) )

To compile 
make

To play : ufo

Have fun
charles vidal

The file ****************** :

Makefile
README
TODO

The Source in .:
--More--(32%)






And heres what the Read Me file in the GNUfo folder says

GnuFo.

A space invader. 

You need SDL ( [http://www.libsdl.org](http://www.libsdl.org) )
I have include the SDLSprite 
( [http://membres.tripod.fr/edorul/Other.htm](http://membres.tripod.fr/edorul/Other.htm) )

To compile 
make

To play : ufo

Have fun
charles vidal

The file ****************** :

Makefile
README
TODO

The Source in .:
direc_enemi.cpp
main.cpp
obj_enemi.cpp
other.cpp
starship.cpp
ufo.h

SDLSprite-1.2:
Makefile
SDLSprite.cpp
SDLSprite.h
SDLSprite.htm
SDLSpriteList.cpp
SDLSpriteList.h
SDLSpritelist.htm

bmp:
Voiture.bmp
alphabet.bmp
alphabet2.bmp
bonus.bmp
chiffre.bmp
enemimissile.bmp
explosion.bmp
levellife.bmp
mine.bmp
missile.bmp
projectile.bmp
saucer.bmp
starship.bmp
starship2.bmp
ufo.bmp

data:
gentraj.tcl
gentraj2.tcl
gentraj3.tcl
gentraj4.tcl
none.txt
scenario.txt
scenario.txt.old
toto.txt
traject.txt
traject2.txt
traject3.txt
traject4.txt
traject5.txt

---

### Post by taurus on 2007-05-03
Okay.  You first need to install the build-essential package before you can compile it.

```
sudo aptitude update
sudo aptitude install build-essential
make
./ufo
```

---

### Post by microsoft92sucks on 2007-05-03
justin@EggHead:~$ make
make: *** No targets specified and no makefile found.  Stop.

i cant get passed the make command wat should i do

---

### Post by taurus on 2007-05-03
Try

```
make -f Makefile
./ufo
```

---

### Post by microsoft92sucks on 2007-05-03
justin@EggHead:~$ make -f Makefile
make: Makefile: No such file or directory
make: *** No rule to make target `Makefile'.  Stop.
is what tgats given me if i change diractory to GNUfo  i get

justin@EggHead:~/Desktop/GNUfo$ make -f Makefile
make -f SDLSprite-1.2/Makefile
make[1]: Entering directory `/home/justin/Desktop/GNUfo'
g++ -c SDLSprite-1.2/SDLSprite.cpp  -I.  `sdl-config --cflags` 
/bin/sh: sdl-config: not found
In file included from SDLSprite-1.2/SDLSprite.cpp:32:
SDLSprite-1.2/SDLSprite.h:39:21: error: SDL/SDL.h: No such file or directory
SDLSprite-1.2/SDLSprite.h:69: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:70: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:80: error: ‘Uint8’ has not been declared
SDLSprite-1.2/SDLSprite.h:80: error: ‘Uint8’ has not been declared
SDLSprite-1.2/SDLSprite.h:80: error: ‘Uint8’ has not been declared
SDLSprite-1.2/SDLSprite.h:86: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:88: error: ‘Uint32’ has not been declared
SDLSprite-1.2/SDLSprite.h:91: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:93: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:95: error: ‘SDL_Surface’ has not been declared
SDLSprite-1.2/SDLSprite.h:97: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:99: error: ‘Uint8’ has not been declared
SDLSprite-1.2/SDLSprite.h:99: error: ‘Uint32’ has not been declared
SDLSprite-1.2/SDLSprite.h:103: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:118: error: ‘Uint32’ does not name a type
SDLSprite-1.2/SDLSprite.h:123: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:125: error: ISO C++ forbids declaration of ‘SDL_Surface’ with no type
SDLSprite-1.2/SDLSprite.h:125: error: expected ‘;’ before ‘*’ token
SDLSprite-1.2/SDLSprite.h:126: error: ISO C++ forbids declaration of ‘SDL_Surface’ with no type
SDLSprite-1.2/SDLSprite.h:126: error: expected ‘;’ before ‘*’ token
SDLSprite-1.2/SDLSprite.h:136: error: ‘Uint32’ does not name a type
SDLSprite-1.2/SDLSprite.h:137: error: ‘Uint32’ does not name a type
SDLSprite-1.2/SDLSprite.h:138: error: ‘Uint32’ does not name a type
SDLSprite-1.2/SDLSprite.h:139: error: ‘Uint32’ does not name a type
SDLSprite-1.2/SDLSprite.h: In member function ‘void SDLSprite::SetAlphaValue(int)’:
SDLSprite-1.2/SDLSprite.h:88: error: ‘m_AlphaValue’ was not declared in this scope
SDLSprite-1.2/SDLSprite.h:89: error: ‘m_Surface’ was not declared in this scope
SDLSprite-1.2/SDLSprite.h:89: error: ‘SDL_SRCALPHA’ was not declared in this scope
SDLSprite-1.2/SDLSprite.h:89: error: ‘SDL_SetAlpha’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp: In constructor ‘SDLSprite::SDLSprite(SDLSprite*)’:
SDLSprite-1.2/SDLSprite.cpp:48: error: ‘Create’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp: In constructor ‘SDLSprite::SDLSprite(const char*, int, int, int)’:
SDLSprite-1.2/SDLSprite.cpp:60: error: ‘Create’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp: In member function ‘void SDLSprite::Init()’:
SDLSprite-1.2/SDLSprite.cpp:80: error: ‘m_DelayStart’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:84: error: ‘m_Shadowed’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:84: error: ‘SDL_FALSE’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:88: error: ‘m_ShadowValue’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:89: error: ‘m_ColorKey’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:90: error: ‘m_AlphaValue’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:91: error: ‘m_TileCreated’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:93: error: ‘NULL’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp: In destructor ‘virtual SDLSprite::~SDLSprite()’:
SDLSprite-1.2/SDLSprite.cpp:102: error: ‘m_TileCreated’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:103: error: ‘m_Surface’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:103: error: ‘SDL_FreeSurface’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:105: error: ‘NULL’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp: At global scope:
SDLSprite-1.2/SDLSprite.cpp:112: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.cpp:141: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.cpp:188: error: variable or field ‘Draw’ declared void
SDLSprite-1.2/SDLSprite.cpp:188: error: ‘int SDLSprite::Draw’ is not a static member of ‘class SDLSprite’
SDLSprite-1.2/SDLSprite.cpp:188: error: ‘SDL_Surface’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:188: error: ‘lpSDLS’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:188: error: expected primary-expression before ‘long’
SDLSprite-1.2/SDLSprite.cpp:188: error: expected primary-expression before ‘long’
SDLSprite-1.2/SDLSprite.cpp:188: error: initializer expression list treated as compound expression
SDLSprite-1.2/SDLSprite.cpp:189: error: expected ‘,’ or ‘;’ before ‘{’ token
SDLSprite-1.2/SDLSprite.cpp:247: error: variable or field ‘SetColorKey’ declared void
SDLSprite-1.2/SDLSprite.cpp:247: error: ‘int SDLSprite::SetColorKey’ is not a static member of ‘class SDLSprite’
SDLSprite-1.2/SDLSprite.cpp:247: error: ‘Uint8’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:247: error: ‘Uint8’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:247: error: ‘Uint8’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:247: error: initializer expression list treated as compound expression
SDLSprite-1.2/SDLSprite.cpp:248: error: expected ‘,’ or ‘;’ before ‘{’ token
SDLSprite-1.2/SDLSprite.cpp: In member function ‘void SDLSprite::SetColorKey()’:
SDLSprite-1.2/SDLSprite.cpp:259: error: ‘m_Surface’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:262: error: ‘m_ColorKey’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:262: error: ‘Uint8’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:262: error: expected primary-expression before ‘)’ token
SDLSprite-1.2/SDLSprite.cpp:262: error: expected `;' before ‘m_Surface’
SDLSprite-1.2/SDLSprite.cpp:263: error: ‘SDL_SRCCOLORKEY’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:263: error: ‘SDL_SetColorKey’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:266: error: ‘Uint16’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:266: error: expected primary-expression before ‘)’ token
SDLSprite-1.2/SDLSprite.cpp:266: error: expected `;' before ‘m_Surface’
SDLSprite-1.2/SDLSprite.cpp:271: error: ‘Uint32’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:271: error: expected primary-expression before ‘)’ token
SDLSprite-1.2/SDLSprite.cpp:271: error: expected `;' before ‘m_Surface’
SDLSprite-1.2/SDLSprite.cpp: At global scope:
SDLSprite-1.2/SDLSprite.cpp:367: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.cpp:379: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.cpp:453: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.cpp:900: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.cpp:991: error: variable or field ‘SetShadowValue’ declared void
SDLSprite-1.2/SDLSprite.cpp:991: error: ‘int SDLSprite::SetShadowValue’ is not a static member of ‘class SDLSprite’
SDLSprite-1.2/SDLSprite.cpp:991: error: ‘Uint8’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:991: error: ‘Uint32’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:991: error: initializer expression list treated as compound expression
SDLSprite-1.2/SDLSprite.cpp:992: error: expected ‘,’ or ‘;’ before ‘{’ token
make[1]: *** [SDLSprite.o] Error 1
make[1]: Leaving directory `/home/justin/Desktop/GNUfo'
make: *** [SDLSprite] Error 2
justin@EggHead:~/Desktop/GNUfo$

---

### Post by taurus on 2007-05-03
Looks like you need to build SDLSprite first.

```
cd SDLSprite-1.2
make -f Makefile
cd ../
make -f Makefile
```

or

```
sudo aptitude update
sudo aptitude install libsdl1.2-dev
cd ~/Desktop/GNUfo
make -f Makefile
```

---

### Post by microsoft92sucks on 2007-05-03
That gave me all this 

justin@EggHead:~/Desktop/GNUfo$ cd SDLSprite-1.2
justin@EggHead:~/Desktop/GNUfo/SDLSprite-1.2$ 
justin@EggHead:~/Desktop/GNUfo/SDLSprite-1.2$ make -f Makefile
make: *** No rule to make target `SDLSprite-1.2/SDLSprite.cpp', needed by `SDLSprite.o'.  Stop.
justin@EggHead:~/Desktop/GNUfo/SDLSprite-1.2$ cd ../
justin@EggHead:~/Desktop/GNUfo$ make -f Makefile
make -f SDLSprite-1.2/Makefile
make[1]: Entering directory `/home/justin/Desktop/GNUfo'
g++ -c SDLSprite-1.2/SDLSprite.cpp  -I.  `sdl-config --cflags` 
/bin/sh: sdl-config: not found
In file included from SDLSprite-1.2/SDLSprite.cpp:32:
SDLSprite-1.2/SDLSprite.h:39:21: error: SDL/SDL.h: No such file or directory
SDLSprite-1.2/SDLSprite.h:69: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:70: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:80: error: ‘Uint8’ has not been declared
SDLSprite-1.2/SDLSprite.h:80: error: ‘Uint8’ has not been declared
SDLSprite-1.2/SDLSprite.h:80: error: ‘Uint8’ has not been declared
SDLSprite-1.2/SDLSprite.h:86: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:88: error: ‘Uint32’ has not been declared
SDLSprite-1.2/SDLSprite.h:91: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:93: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:95: error: ‘SDL_Surface’ has not been declared
SDLSprite-1.2/SDLSprite.h:97: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:99: error: ‘Uint8’ has not been declared
SDLSprite-1.2/SDLSprite.h:99: error: ‘Uint32’ has not been declared
SDLSprite-1.2/SDLSprite.h:103: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:118: error: ‘Uint32’ does not name a type
SDLSprite-1.2/SDLSprite.h:123: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.h:125: error: ISO C++ forbids declaration of ‘SDL_Surface’ with no type
SDLSprite-1.2/SDLSprite.h:125: error: expected ‘;’ before ‘*’ token
SDLSprite-1.2/SDLSprite.h:126: error: ISO C++ forbids declaration of ‘SDL_Surface’ with no type
SDLSprite-1.2/SDLSprite.h:126: error: expected ‘;’ before ‘*’ token
SDLSprite-1.2/SDLSprite.h:136: error: ‘Uint32’ does not name a type
SDLSprite-1.2/SDLSprite.h:137: error: ‘Uint32’ does not name a type
SDLSprite-1.2/SDLSprite.h:138: error: ‘Uint32’ does not name a type
SDLSprite-1.2/SDLSprite.h:139: error: ‘Uint32’ does not name a type
SDLSprite-1.2/SDLSprite.h: In member function ‘void SDLSprite::SetAlphaValue(int)’:
SDLSprite-1.2/SDLSprite.h:88: error: ‘m_AlphaValue’ was not declared in this scope
SDLSprite-1.2/SDLSprite.h:89: error: ‘m_Surface’ was not declared in this scope
SDLSprite-1.2/SDLSprite.h:89: error: ‘SDL_SRCALPHA’ was not declared in this scope
SDLSprite-1.2/SDLSprite.h:89: error: ‘SDL_SetAlpha’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp: In constructor ‘SDLSprite::SDLSprite(SDLSprite*)’:
SDLSprite-1.2/SDLSprite.cpp:48: error: ‘Create’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp: In constructor ‘SDLSprite::SDLSprite(const char*, int, int, int)’:
SDLSprite-1.2/SDLSprite.cpp:60: error: ‘Create’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp: In member function ‘void SDLSprite::Init()’:
SDLSprite-1.2/SDLSprite.cpp:80: error: ‘m_DelayStart’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:84: error: ‘m_Shadowed’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:84: error: ‘SDL_FALSE’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:88: error: ‘m_ShadowValue’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:89: error: ‘m_ColorKey’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:90: error: ‘m_AlphaValue’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:91: error: ‘m_TileCreated’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:93: error: ‘NULL’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp: In destructor ‘virtual SDLSprite::~SDLSprite()’:
SDLSprite-1.2/SDLSprite.cpp:102: error: ‘m_TileCreated’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:103: error: ‘m_Surface’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:103: error: ‘SDL_FreeSurface’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:105: error: ‘NULL’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp: At global scope:
SDLSprite-1.2/SDLSprite.cpp:112: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.cpp:141: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.cpp:188: error: variable or field ‘Draw’ declared void
SDLSprite-1.2/SDLSprite.cpp:188: error: ‘int SDLSprite::Draw’ is not a static member of ‘class SDLSprite’
SDLSprite-1.2/SDLSprite.cpp:188: error: ‘SDL_Surface’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:188: error: ‘lpSDLS’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:188: error: expected primary-expression before ‘long’
SDLSprite-1.2/SDLSprite.cpp:188: error: expected primary-expression before ‘long’
SDLSprite-1.2/SDLSprite.cpp:188: error: initializer expression list treated as compound expression
SDLSprite-1.2/SDLSprite.cpp:189: error: expected ‘,’ or ‘;’ before ‘{’ token
SDLSprite-1.2/SDLSprite.cpp:247: error: variable or field ‘SetColorKey’ declared void
SDLSprite-1.2/SDLSprite.cpp:247: error: ‘int SDLSprite::SetColorKey’ is not a static member of ‘class SDLSprite’
SDLSprite-1.2/SDLSprite.cpp:247: error: ‘Uint8’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:247: error: ‘Uint8’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:247: error: ‘Uint8’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:247: error: initializer expression list treated as compound expression
SDLSprite-1.2/SDLSprite.cpp:248: error: expected ‘,’ or ‘;’ before ‘{’ token
SDLSprite-1.2/SDLSprite.cpp: In member function ‘void SDLSprite::SetColorKey()’:
SDLSprite-1.2/SDLSprite.cpp:259: error: ‘m_Surface’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:262: error: ‘m_ColorKey’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:262: error: ‘Uint8’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:262: error: expected primary-expression before ‘)’ token
SDLSprite-1.2/SDLSprite.cpp:262: error: expected `;' before ‘m_Surface’
SDLSprite-1.2/SDLSprite.cpp:263: error: ‘SDL_SRCCOLORKEY’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:263: error: ‘SDL_SetColorKey’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:266: error: ‘Uint16’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:266: error: expected primary-expression before ‘)’ token
SDLSprite-1.2/SDLSprite.cpp:266: error: expected `;' before ‘m_Surface’
SDLSprite-1.2/SDLSprite.cpp:271: error: ‘Uint32’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:271: error: expected primary-expression before ‘)’ token
SDLSprite-1.2/SDLSprite.cpp:271: error: expected `;' before ‘m_Surface’
SDLSprite-1.2/SDLSprite.cpp: At global scope:
SDLSprite-1.2/SDLSprite.cpp:367: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.cpp:379: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.cpp:453: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.cpp:900: error: ‘SDL_bool’ does not name a type
SDLSprite-1.2/SDLSprite.cpp:991: error: variable or field ‘SetShadowValue’ declared void
SDLSprite-1.2/SDLSprite.cpp:991: error: ‘int SDLSprite::SetShadowValue’ is not a static member of ‘class SDLSprite’
SDLSprite-1.2/SDLSprite.cpp:991: error: ‘Uint8’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:991: error: ‘Uint32’ was not declared in this scope
SDLSprite-1.2/SDLSprite.cpp:991: error: initializer expression list treated as compound expression
SDLSprite-1.2/SDLSprite.cpp:992: error: expected ‘,’ or ‘;’ before ‘{’ token
make[1]: *** [SDLSprite.o] Error 1
make[1]: Leaving directory `/home/justin/Desktop/GNUfo'
make: *** [SDLSprite] Error 2
justin@EggHead:~/Desktop/GNUfo$

---

### Post by taurus on 2007-05-03
Try the second method in my previous post, installing SDL from aptitude.

---

### Post by microsoft92sucks on 2007-05-03
that worked thank u

---

