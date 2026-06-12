---
title: "new linux user"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by ShatoriKiriyama on 2007-09-15
just installed ubuntu 7.04 after backing up my media and work.
i have it on a HP ze2000 laptop and only two problems really so far.i can't get two monitors set up so that my external one is the left half and the laptop screen is the right half.. :S
and i cant seem to get the psptoolchain setup properly.

i used to use cygwin in windows xp before and i tried to install the toolchain the same as i did for it but it didnt go right i think....when i try to compile a game i made that i KNOW compiled in cygwin after all the setting-up it comes up with a load of error messages....

> menace@menace-laptop:~/Desktop/Source$ make
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -Wall -D_PSP_FW_VERSION=150   -c -o game.o game.c
In file included from game.c:5:
/usr/include/sys/stat.h:26:22: error: features.h: No such file or directory
/usr/include/sys/stat.h:28:58: error: bits/types.h: No such file or directory
/usr/include/sys/stat.h:105:23: error: bits/stat.h: No such file or directory
In file included from game.c:5:
/usr/include/sys/stat.h:207: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘extern’
/usr/include/sys/stat.h:212: warning: ‘struct stat’ declared inside parameter list
/usr/include/sys/stat.h:212: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/include/sys/stat.h: In function ‘fstat’:
/usr/include/sys/stat.h:212: error: expected declaration specifiers before ‘__THROW’
/usr/include/sys/stat.h:280: error: expected declaration specifiers or ‘...’ before ‘__mode_t’
/usr/include/sys/stat.h:281: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/sys/stat.h:307: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘umask’
/usr/include/sys/stat.h:316: error: expected declaration specifiers or ‘...’ before ‘__mode_t’
/usr/include/sys/stat.h:317: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/sys/stat.h:345: error: expected declaration specifiers or ‘...’ before ‘__mode_t’
/usr/include/sys/stat.h:346: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/sys/stat.h:380: warning: ‘struct stat’ declared inside parameter list
/usr/include/sys/stat.h:381: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/sys/stat.h:383: warning: ‘struct stat’ declared inside parameter list
/usr/include/sys/stat.h:383: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/sys/stat.h:385: warning: ‘struct stat’ declared inside parameter list
/usr/include/sys/stat.h:385: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/sys/stat.h:387: warning: ‘struct stat’ declared inside parameter list
/usr/include/sys/stat.h:388: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/sys/stat.h:423: error: expected declaration specifiers or ‘...’ before ‘__mode_t’
/usr/include/sys/stat.h:424: error: expected declaration specifiers or ‘...’ before ‘__dev_t’
/usr/include/sys/stat.h:424: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/sys/stat.h:427: error: expected declaration specifiers or ‘...’ before ‘__mode_t’
/usr/include/sys/stat.h:427: error: expected declaration specifiers or ‘...’ before ‘__dev_t’
/usr/include/sys/stat.h:428: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/sys/stat.h:434: error: expected ‘)’ before ‘(’ token
/usr/include/sys/stat.h:448: error: expected ‘)’ before ‘(’ token
/usr/include/sys/stat.h:515: error: expected declaration specifiers before ‘__END_DECLS’
In file included from game.c:6:
graphics.h:22: error: expected specifier-qualifier-list before ‘Color’
graphics.h:23: error: storage class specified for parameter ‘Image’
graphics.h:32: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
graphics.h:51: error: expected declaration specifiers or ‘...’ before ‘Image’
graphics.h:51: error: expected declaration specifiers or ‘...’ before ‘Image’
graphics.h:51: error: storage class specified for parameter ‘blitImageToImage’
graphics.h:69: error: expected declaration specifiers or ‘...’ before ‘Image’
graphics.h:69: error: storage class specified for parameter ‘blitImageToScreen’
graphics.h:88: error: expected declaration specifiers or ‘...’ before ‘Image’
graphics.h:88: error: expected declaration specifiers or ‘...’ before ‘Image’
graphics.h:88: error: storage class specified for parameter ‘blitAlphaImageToImage’
graphics.h:106: error: expected declaration specifiers or ‘...’ before ‘Image’
graphics.h:106: error: storage class specified for parameter ‘blitAlphaImageToScreen’
graphics.h:116: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
graphics.h:124: error: expected ‘)’ before ‘*’ token
graphics.h:133: error: expected ‘)’ before ‘color’
graphics.h:140: error: expected ‘)’ before ‘color’
graphics.h:153: error: expected ‘)’ before ‘color’
graphics.h:165: error: expected ‘)’ before ‘color’
graphics.h:175: error: expected ‘)’ before ‘color’
graphics.h:185: error: expected ‘)’ before ‘color’
graphics.h:195: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘getPixelScreen’
graphics.h:205: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘getPixelImage’
graphics.h:215: error: storage class specified for parameter ‘printTextScreen’
graphics.h:226: error: expected declaration specifiers or ‘...’ before ‘Image’
graphics.h:226: error: storage class specified for parameter ‘printTextImage’
graphics.h:239: error: expected declaration specifiers or ‘...’ before ‘Color’
graphics.h:239: error: storage class specified for parameter ‘saveImage’
graphics.h:244: error: storage class specified for parameter ‘flipScreen’
graphics.h:249: error: storage class specified for parameter ‘initGraphics’
graphics.h:254: error: storage class specified for parameter ‘disableGraphics’
graphics.h:266: error: expected declaration specifiers or ‘...’ before ‘Color’
graphics.h:278: error: expected declaration specifiers or ‘...’ before ‘Color’
graphics.h:278: error: expected declaration specifiers or ‘...’ before ‘Image’
graphics.h:278: error: storage class specified for parameter ‘drawLineImage’
graphics.h:285: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
graphics.h:292: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
graphics.h:294: error: storage class specified for parameter ‘guStart’
In file included from game.c:7:
images.h:4: error: storage class specified for parameter ‘drawBase’
In file included from game.c:8:
functions.h:4: error: storage class specified for parameter ‘GameOver’
functions.h:5: error: expected ‘)’ before ‘*’ token
functions.h:6: error: storage class specified for parameter ‘ResetInvadersS’
functions.h:7: error: storage class specified for parameter ‘ResetInvadersX’
functions.h:8: error: storage class specified for parameter ‘ResetInvadersY’
In file included from game.c:9:
rounddisplay.h:4: error: storage class specified for parameter ‘RoundDisplay’
game.c:16: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
game.c:917: error: old-style parameter declarations in prototyped function definition
game.c:917: error: expected ‘{’ at end of input
make: *** [game.o] Error 1

i've really no idea what happened there... :\


so any advice on those two problems would be great :)


but also,since i am completely new to linux,would anyone like to point to any good emulators or games and maybe a good media player with winamp-like features?

---

### Post by Steve1961 on 2007-09-15
This link might help with the psptoolchain issue:

[http://forums.maxconsole.net/showthread.php?t=69699#post598059](http://forums.maxconsole.net/showthread.php?t=69699#post598059)

For winamp like media players you could takea look at XMMS or Audacious

---

### Post by mlentink on 2007-09-15
> **ShatoriKiriyama said:**
> ...and maybe a good media player...

Let's start with the easy one: have a look at Amarok and Banshee, and Rhythmbox  is buit-in. Banshee was a bit unstable for me, and so far I really like Amarok

---

