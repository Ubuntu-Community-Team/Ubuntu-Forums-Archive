---
title: "[SOLVED] mlt make errors"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-03-11
I am trying to rebuild ffmpeg, mlt and finally kdenlive to try to fix the audio being faster than the video.  At any rate, I got ffmpeg made and installed, but when trying to make mlt it keeps coming up saying it can't find avformat.h.  The libavcodec is installed in /usr/local/include but the make doesn't seem to find it.  I even copied the avformat.h from there to the folder where the src is that needed it and it still doesn't find it.  Can anyone help with getting it config'd somehow so that this will make?

Thanks in advance! :)

---

### Post by intel on 2008-03-11
You need to describe what you typed.

also provide(copy/paste) the exact error

---

### Post by anewguy on 2008-03-11
This is the ./configure, as recommended by the wiki page:

dave@dave-desktop:~/mlt$ ./configure --enable-gpl --enable-shared --enable-libvorbis --enable-libogg --enable-pp --enable-swscaler
Configuring framework:
Configuring modules:
Configuring modules/avformat:
Configuring modules/core:
Configuring modules/dv:
Configuring modules/effectv:
Configuring modules/feeds:
Configuring modules/fezzik:
Configuring modules/frei0r:
- frei0r plugin disabled. Install frei0r-plugins and make sure frei0r.h is available.
Configuring modules/gtk2:
No GTK2 components found - disabling
Configuring modules/inigo:
Configuring modules/jackrack:
Configuring modules/kdenlive:
Configuring modules/kino:
Configuring modules/lumas:
Configuring modules/motion_est:
- motion estimation components disabled. Add --enable-motion-est to enable.
Configuring modules/normalize:
Configuring modules/oldfilm:
Configuring modules/plus:
Configuring modules/qimage:
Configuring modules/resample:
Configuring modules/sdl:
Configuring modules/sox:
Configuring modules/valerie:
Configuring modules/vmfx:
Configuring modules/vorbis:
Configuring modules/westley:
Configuring modules/xine:
Configuring inigo:
Configuring valerie:
Configuring miracle:
GPL License Used
dave@dave-desktop:~/mlt$ 


This is the make output (note a re-run, so some pieces were already "made"):



dave@dave-desktop:~/mlt$ make
list='src/framework src/inigo src/valerie src/miracle src/humperdink src/albino src/modules profiles'; \
        for subdir in $list; do \
                make -s -C $subdir depend || exit 1; \
                make -C $subdir all || exit 1; \
        done
make[1]: Entering directory `/home/dave/mlt/src/framework'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/dave/mlt/src/framework'
make[1]: Entering directory `/home/dave/mlt/src/inigo'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/dave/mlt/src/inigo'
make[1]: Entering directory `/home/dave/mlt/src/valerie'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/dave/mlt/src/valerie'
make[1]: Entering directory `/home/dave/mlt/src/miracle'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/dave/mlt/src/miracle'
make[1]: Entering directory `/home/dave/mlt/src/humperdink'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/dave/mlt/src/humperdink'
make[1]: Entering directory `/home/dave/mlt/src/albino'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/dave/mlt/src/albino'
make[1]: Entering directory `/home/dave/mlt/src/modules'
list='xine dv oldfilm valerie motion_est gtk2 vmfx westley sox kino kdenlive feeds plus effectv sdl inigo resample fezzik core vorbis avformat lumas jackrack qimage frei0r normalize'; \
        for subdir in $list; do \
                if [ -f $subdir/Makefile -a ! -f disable-$subdir ] ; \
                then make -C $subdir all || exit 1; \
                fi \
        done
make[2]: Entering directory `/home/dave/mlt/src/modules/xine'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/xine'
make[2]: Entering directory `/home/dave/mlt/src/modules/dv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/dv'
make[2]: Entering directory `/home/dave/mlt/src/modules/oldfilm'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/oldfilm'
make[2]: Entering directory `/home/dave/mlt/src/modules/valerie'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/valerie'
make[2]: Entering directory `/home/dave/mlt/src/modules/vmfx'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/vmfx'
make[2]: Entering directory `/home/dave/mlt/src/modules/westley'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/westley'
make[2]: Entering directory `/home/dave/mlt/src/modules/sox'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/sox'
make[2]: Entering directory `/home/dave/mlt/src/modules/kino'
g++ -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../../ `pkg-config --cflags libquicktime`  `pkg-config --cflags libdv` -Wno-deprecated `pkg-config --cflags libquicktime`    -c -o kino_wrapper.o kino_wrapper.cc
g++ -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../../ `pkg-config --cflags libquicktime`  `pkg-config --cflags libdv` -Wno-deprecated `pkg-config --cflags libquicktime`    -c -o avi.o avi.cc
g++ -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../../ `pkg-config --cflags libquicktime`  `pkg-config --cflags libdv` -Wno-deprecated `pkg-config --cflags libquicktime`    -c -o filehandler.o filehandler.cc
g++ -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../../ `pkg-config --cflags libquicktime`  `pkg-config --cflags libdv` -Wno-deprecated `pkg-config --cflags libquicktime`    -c -o riff.o riff.cc
cc -shared -o ../libmltkino.so factory.o producer_kino.o kino_wrapper.o avi.o error.o filehandler.o riff.o -L../../framework -lmlt -lstdc++ `pkg-config --libs libquicktime` `pkg-config --libs libdv`
make[2]: Leaving directory `/home/dave/mlt/src/modules/kino'
make[2]: Entering directory `/home/dave/mlt/src/modules/kdenlive'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/kdenlive'
make[2]: Entering directory `/home/dave/mlt/src/modules/feeds'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/feeds'
make[2]: Entering directory `/home/dave/mlt/src/modules/plus'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/plus'
make[2]: Entering directory `/home/dave/mlt/src/modules/effectv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/effectv'
make[2]: Entering directory `/home/dave/mlt/src/modules/sdl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/sdl'
make[2]: Entering directory `/home/dave/mlt/src/modules/inigo'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/inigo'
make[2]: Entering directory `/home/dave/mlt/src/modules/resample'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/resample'
make[2]: Entering directory `/home/dave/mlt/src/modules/fezzik'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/fezzik'
make[2]: Entering directory `/home/dave/mlt/src/modules/core'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/core'
make[2]: Entering directory `/home/dave/mlt/src/modules/vorbis'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dave/mlt/src/modules/vorbis'
make[2]: Entering directory `/home/dave/mlt/src/modules/avformat'
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I/usr/local/include   -I../..   -c -o factory.o factory.c
factory.c:34:22: error: avformat.h: No such file or directory
factory.c: In function &#8216;avformat_init&#8217;:
factory.c:90: warning: implicit declaration of function &#8216;av_register_all&#8217;
factory.c:92: warning: implicit declaration of function &#8216;av_log_set_level&#8217;
make[2]: *** [factory.o] Error 1
make[2]: Leaving directory `/home/dave/mlt/src/modules/avformat'
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/dave/mlt/src/modules'
make: *** [all] Error 1
dave@dave-desktop:~/mlt$


EDIT:  I had the option string for the make wrong - went back and copied from the wiki, so I used the correct ones, reran, got the same result.

---

### Post by lloyd_b on 2008-03-11
Try installing the package "libavformat-dev".  If this fixes the problem, then please drop a line to the maintainer of that package - if it's required to build the package, then ideally "configure" should be verifying that it's present.

Lloyd B.

---

### Post by anewguy on 2008-03-11
> **lloyd_b said:**
> Try installing the package "libavformat-dev".  If this fixes the problem, then please drop a line to the maintainer of that package - if it's required to build the package, then ideally "configure" should be verifying that it's present.

Lloyd B.

Thanks, Lloyd.  Trouble is, libavformat-dev is already installed.  I don't know what this thing wants - it's almost as if it's not seeing the /usr/loca/include  av  files, yet, as mentioned, even when I copied the avformat.h file from there to the particular source folder (/home/dave/mlt/src/modules/avformat) it still didn't find it.

:)

---

### Post by anewguy on 2008-03-11
Okay, a dumb question:  does make somehow already know about /usr/loca/include, or does that path have to specified someway?  I noticed in the configure script that it has a definition for /usr/loca/lib, but the av lib stuff is in /usr/loca/include.

---

### Post by lloyd_b on 2008-03-11
> **anewguy said:**
> Okay, a dumb question:  does make somehow already know about /usr/loca/include, or does that path have to specified someway?  I noticed in the configure script that it has a definition for /usr/loca/lib, but the av lib stuff is in /usr/loca/include.

From one of your earlier posts:
```
cc -Wall -fPIC -DPIC -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread **-I/usr/local/include** -I../.. -c -o factory.o factory.c
```
Note the bolded section - the "-I" directive tells the compiler "look here for include files (in addition to the standard directories)"

Lloyd B.

---

### Post by anewguy on 2008-03-11
> **lloyd_b said:**
> From one of your earlier posts:
```
cc -Wall -fPIC -DPIC -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread **-I/usr/local/include** -I../.. -c -o factory.o factory.c
```
Note the bolded section - the "-I" directive tells the compiler "look here for include files (in addition to the standard directories)"

Lloyd B.


Same result.  I really don't understand what's going on with this.

---

### Post by Oldsoldier2003 on 2008-03-11
does running ```
sudo apt-get build-dep ffmpeg mlt kdenlive
``` before configuring and compiling make any difference?

---

### Post by anewguy on 2008-03-11
> **Oldsoldier2003 said:**
> does running ```
sudo apt-get build-dep ffmpeg mlt kdenlive
``` before configuring and compiling make any difference?

I'll try that and see, but I doubt it.  I already have ffmpeg compiled, and I know for sure that the library and the includes that the make of mlt is looking for are installed (I even tried the big apt-get as mentioned in the wiki page last night but it said I already had everything).

If I can ever get this to go, then I can move on to kdenlive.  I already have the source package installed.  Originally I had gotten ffmpeg, mlt and mlt++ to all make - but using source from a different place.  When I got to kdenlive it would bomb out on the make after a long period of time saying MLT_PREFIX wasn't defined.  Never got an answer on any of that here or in the mutlimedia forum.  So, I deleted everything and started from scratch (hence the big apt-get last night).  Got ffmpeg made like last time, but now it's stuck in this mlt problem.

:)

---

### Post by anewguy on 2008-03-11
While it did pick up some of the gtk2 stuff (which the package says are not needed anymore), it did not fix the problem.  

:confused:

---

### Post by anewguy on 2008-03-11
I FINALLY got mtl made - I had to manually edit each source file and explicitly declare the full path for the non-system includes.  I assume there must be something wierd about the makefile in that folder.

Now I'll move on to kdenlive again, and make a new thread for it's error.

:)

---

### Post by mridkash on 2008-03-12
Actually, I found that the script uses wrong paths with 

cc -Wall -fPIC -DPIC -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread **-I/usr/local/include** -I../.. -c -o factory.o factory.c

Instead of /usr/local/include , it should be /usr/local/include/libavformat/

A simple solution, 
move the .h files in /usr/local/include/libavformat/ out of this folder. It worked

---

