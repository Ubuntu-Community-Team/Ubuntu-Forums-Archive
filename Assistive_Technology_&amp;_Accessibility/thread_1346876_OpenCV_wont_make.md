---
title: "OpenCV wont make?"
date: 2009-12-05
forum: Assistive Technology &amp; Accessibility
---

### Post by The End of The World on 2009-12-05
(assuming this is accessibility as its controling the cursor withought the mouse)

yeah i've been trying to install OpenCV yet it wont make...it comes up with this line of code in the terminal 

```
make  all-recursive
make[1]: Entering directory `/usr/local/src/opencv-1.0.0'
Making all in cxcore
make[2]: Entering directory `/usr/local/src/opencv-1.0.0/cxcore'
Making all in src
make[3]: Entering directory `/usr/local/src/opencv-1.0.0/cxcore/src'
if /bin/bash ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I. -I../../cxcore/include -I../..  -DNDEBUG   -Wall -fno-rtti -pipe -O3 -g -march=i686 -ffast-math -fomit-frame-pointer -fno-strict-aliasing -MT cxalloc.lo -MD -MP -MF ".deps/cxalloc.Tpo" -c -o cxalloc.lo cxalloc.cpp; \
    then mv -f ".deps/cxalloc.Tpo" ".deps/cxalloc.Plo"; else rm -f ".deps/cxalloc.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I. -I../../cxcore/include -I../.. -DNDEBUG -Wall -fno-rtti -pipe -O3 -g -march=i686 -ffast-math -fomit-frame-pointer -fno-strict-aliasing -MT cxalloc.lo -MD -MP -MF .deps/cxalloc.Tpo -c cxalloc.cpp  -fPIC -DPIC -o .libs/cxalloc.o
In file included from _cxcore.h:60,
                 from cxalloc.cpp:42:
../../cxcore/include/cxmisc.h:133:6: error: #elif with no expression
make[3]: *** [cxalloc.lo] Error 1
make[3]: Leaving directory `/usr/local/src/opencv-1.0.0/cxcore/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/opencv-1.0.0/cxcore'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/opencv-1.0.0'
make: *** [all] Error 2
```Thanks in advance if u can help :D

---

### Post by pratik069 on 2010-01-05
Did u get the solution. I'm facing the same problem.
Please do help....

---

### Post by Sef on 2010-01-05
Have either of you checked the [OpenCV wiki]("http://opencv.willowgarage.com/wiki/")?

---

### Post by Unterseeboot_234 on 2010-01-16
OpenCV 2.x does build using the recipe from the OpenCV wiki. [http://opencv.willowgarage.com/wiki/InstallGuide_Linux]("http://opencv.willowgarage.com/wiki/InstallGuide_Linux"). The samples run. I don't have a webcam. Some of the samples require webcam.

Two things:

I wished I had used **check install** instead of **make install** to gain package removal.

the ubuntu repositories for OpenCV 1.0 make you remove one of the codec libs used by video programs, but that doesn't seem to affect ffmpeg.

Everyone seems overly-eager to make Face Recognition with OpenCV and a webcam. I want Object Recognition from a file graphic. So now, I'm trying to link OpenCV - Java - Processing. I have a link issue, Processing wants OpenCV 1.0. I may push on and try [shudder] JNI to use the OpenCV 2.0 libs.

---

### Post by Frizzle on 2011-03-29
For all the people finding this topic through google (like me): I 'solved' this problem by commenting out the line cxcore/include/cxmisc.h:133 + 134. Make went fine after that. I am now at the stage of compiling against the lib but i think this does not change the functionality.

This is how the part now looks:
```
#elif defined HAVE_ALLOCA
    #include <stdlib.h>
//#elif
//    #error
#endif
```

---

### Post by Fernando Siqueira on 2011-04-09
Apparently a newer version of GCC changes the pre-processor, so this command elif without any expression will result in a compilation error.

 [http://gcc.gnu.org/gcc-4.4/porting_to.html](http://gcc.gnu.org/gcc-4.4/porting_to.html)

So, to fix this change the elif to else, and it compiles functionally.

---

### Post by kinderen on 2011-05-10
> **Frizzle said:**
> For all the people finding this topic through google (like me): I 'solved' this problem by commenting out the line cxcore/include/cxmisc.h:133 + 134. Make went fine after that. I am now at the stage of compiling against the lib but i think this does not change the functionality.

This is how the part now looks:
```
#elif defined HAVE_ALLOCA
    #include <stdlib.h>
//#elif
//    #error
#endif
```
instead of commenting out line 133-134, you should change "#elif" to "#else". that is the proper way to do it. but i am not sure if it makes a difference...

---

### Post by luxOFlux on 2011-07-10
Are you aware that openCV is in the repositories? It is called libcv though.

---

### Post by wangkeit on 2012-11-03
> **The End of The World said:**
> (assuming this is accessibility as its controling the cursor withought the mouse)

yeah i've been trying to install OpenCV yet it wont make...it comes up with this line of code in the terminal 

```
make  all-recursive
make[1]: Entering directory `/usr/local/src/opencv-1.0.0'
Making all in cxcore
make[2]: Entering directory `/usr/local/src/opencv-1.0.0/cxcore'
Making all in src
make[3]: Entering directory `/usr/local/src/opencv-1.0.0/cxcore/src'
if /bin/bash ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I. -I../../cxcore/include -I../..  -DNDEBUG   -Wall -fno-rtti -pipe -O3 -g -march=i686 -ffast-math -fomit-frame-pointer -fno-strict-aliasing -MT cxalloc.lo -MD -MP -MF ".deps/cxalloc.Tpo" -c -o cxalloc.lo cxalloc.cpp; \
    then mv -f ".deps/cxalloc.Tpo" ".deps/cxalloc.Plo"; else rm -f ".deps/cxalloc.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I. -I../../cxcore/include -I../.. -DNDEBUG -Wall -fno-rtti -pipe -O3 -g -march=i686 -ffast-math -fomit-frame-pointer -fno-strict-aliasing -MT cxalloc.lo -MD -MP -MF .deps/cxalloc.Tpo -c cxalloc.cpp  -fPIC -DPIC -o .libs/cxalloc.o
In file included from _cxcore.h:60,
                 from cxalloc.cpp:42:
../../cxcore/include/cxmisc.h:133:6: error: #elif with no expression
make[3]: *** [cxalloc.lo] Error 1
make[3]: Leaving directory `/usr/local/src/opencv-1.0.0/cxcore/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/opencv-1.0.0/cxcore'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/opencv-1.0.0'
make: *** [all] Error 2
```Thanks in advance if u can help :D


[http://stackoverflow.com/questions/11470217/compile-opencv-2-4-2-for-debian-lenny](http://stackoverflow.com/questions/11470217/compile-opencv-2-4-2-for-debian-lenny)

---

### Post by overdrank on 2012-11-03
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

