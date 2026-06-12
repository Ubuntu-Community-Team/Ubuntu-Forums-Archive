---
title: "Trying to compile Dega..."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by dpzektor on 2007-05-21
Well, since I have had tremendously great luck with Ubuntu so far, I figured I'd *try* to compile a certain program (emulator) that I really loved in the Windows world today. But, no luck. Of course installing apps and such via the repositories or via downloadable .deb packages is such a breeze, but maybe I was never meant to compile sources. I just don't have a clue when it comes to this. Perhaps someone can help? I simply dropped to a prompt in the directory of the extracted sources and ran "sudo make", and here is what I got:

gcc -O3 -fomit-frame-pointer -funroll-loops -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -Imast -Idoze -D__cdecl=   -c -o sdl/main.o sdl/main.c
In file included from sdl/main.c:7:
mast/mast.h:22: error: conflicting types for ‘dprintf’
/usr/include/stdio.h:388: error: previous declaration of ‘dprintf’ was here
make: *** [sdl/main.o] Error 1


Here is the link for the program:

[http://www.emulinks.de/emus/](http://www.emulinks.de/emus/)  (Dega/SDL)

I would really love to get this going. It is a fantastic Sega Master System/Game Gear emulator with some features that other emulators do not have...most notably Sega 3-D glasses emulation via those red/blue movie glasses :)

---

### Post by Cypher on 2007-05-22
Do the following
```

cd mast
gedit mast.h

```
Go to the line: extern int dprintf (char *Format, ...); on line 22 and change it to
```

// extern int dprintf (char *Format, ...);

```
Now do
```

cd ..
make

```
if that works and gets you a binary, then you can do
```

sudo cp dega /usr/local/bin

```

---

### Post by dpzektor on 2007-05-22
Yes! I did what you said, and of course has to install g++ and nasm to get it to compile. It worked! It runs fantastic as well (perfect sound, full speed). Thank you so much for your help!

---

### Post by %hMa@?b&lt;C on 2007-05-22
whoops, i am a moron :)

---

### Post by sabrewolf2006 on 2007-06-15
nevermind :)

---

