---
title: "Problem compiling allegro sprite editor"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by grimdaze on 2006-06-10
I'm trying to compile the allegro sprite editor([http://ase.sourceforge.net/index.html]("http://ase.sourceforge.net/index.html")), but I keep getting an error. 
Here's my output:
```
grimdaze@Ubuntu:~/ase-0.4r1$ sh fix.sh
What platform (unix/djgpp/mingw32)? [unix]
Do you want debug ASE (y/n)? [n] n
Do you want profile ASE (y/n)? [n] y
Where do you want install ASE by default? [/usr/local]
Do you want use precompiled header (needs GCC >= 3.4) (y/n)? [n] n
Do you have LibJPEG (6.2 recommended) library (y/n)? [n] y
The GIF patent expired in your country (y/n)? [n] n
ASE configured:
  Platform:             Unix
  Debug suppport:       no
  Profile suppport:     yes
  Prefix:               /usr/local
  Precompiled header:   no
  JPEG suppport:        yes (LibJPEG)
  GIF suppport: no

Is it right (y/n)? [y] y
creating makefile...
creating jinete/makefile...
grimdaze@Ubuntu:~/ase-0.4r1$ make
gcc  -Wall -I. -Isrc -Ijinete/include -Iextern -Ijinete/freetype/include -Iextern/lua/include -Iextern/gfli -Wno-deprecated-declarations -s -O3 -DDEFAULT_PREFIX="\""/usr/local"\"" -DHAVE_LIBJPEG -o obj/unix/console.o -c src/console/console.c
gcc  -Wall -I. -Isrc -Ijinete/include -Iextern -Ijinete/freetype/include -Iextern/lua/include -Iextern/gfli -Wno-deprecated-declarations -s -O3 -DDEFAULT_PREFIX="\""/usr/local"\"" -DHAVE_LIBJPEG -o obj/unix/app.o -c src/core/app.c
gcc  -Wall -I. -Isrc -Ijinete/include -Iextern -Ijinete/freetype/include -Iextern/lua/include -Iextern/gfli -Wno-deprecated-declarations -s -O3 -DDEFAULT_PREFIX="\""/usr/local"\"" -DHAVE_LIBJPEG -o obj/unix/cfg.o -c src/core/cfg.c
gcc  -Wall -I. -Isrc -Ijinete/include -Iextern -Ijinete/freetype/include -Iextern/lua/include -Iextern/gfli -Wno-deprecated-declarations -s -O3 -DDEFAULT_PREFIX="\""/usr/local"\"" -DHAVE_LIBJPEG -o obj/unix/config.o -c src/core/config.c
src/core/config.c: In function ‘init_config’:
src/core/config.c:224: error: too few arguments to function ‘_add_exit_func’
make: *** [obj/unix/config.o] Error 1

```

I tried it with the recomended(I assume that's what the [answer] things are) answers and got the same error.

---

### Post by darkali on 2006-06-11
You can't compile it because there's and error in a file, this is the line:
src/core/config.c:224: error: too few arguments to function ‘_add_exit_func’

Since this is the last version try downloading an older one (if available). You should also contact the author about this bug.

Or you can try to fix 'config.c' line 224, but that's another story...

---

### Post by grimdaze on 2006-06-13
After a few emails with the author it turns out that the problem was that I have a too newer version of allegro to compile it. It needs 4.0. 
If anyone else has this problem and don't want to bother with an older version of allegro there is a binary package available [here]("http://www.jamyskis.net/ase.php") that runs fine with 4.2. Thanks to the author of ASE for the link.

---

