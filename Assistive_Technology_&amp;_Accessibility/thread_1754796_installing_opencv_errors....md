---
title: "installing opencv errors..."
date: 2011-05-10
forum: Assistive Technology &amp; Accessibility
---

### Post by kinderen on 2011-05-10
hi everyone,
i have been trying to install opencv, after run ./configure i ran the make file and I got this message:
```
/bin/bash ../../../libtool --tag=CXX   --mode=link g++ -Wall -fno-rtti -pipe -O3 -g -march=i686 -ffast-math -fomit-frame-pointer  -msse2     -o opencv-haartraining haartraining.o libcvhaartraining.a ../../../otherlibs/highgui/libhighgui.la ../../../cv/src/libcv.la ../../../cxcore/src/libcxcore.la -lpthread -ldl -lm 
g++ -Wall -fno-rtti -pipe -O3 -g -march=i686 -ffast-math -fomit-frame-pointer -msse2 -o .libs/opencv-haartraining haartraining.o  libcvhaartraining.a ../../../otherlibs/highgui/.libs/libhighgui.so ../../../cv/src/.libs/libcv.so ../../../cxcore/src/.libs/libcxcore.so -lpthread -ldl -lm 
../../../otherlibs/highgui/.libs/libhighgui.so: undefined reference to `cvCreateCameraCapture_V4L(int)'
collect2: ld returned 1 exit status
make[4]: *** [opencv-haartraining] Error 1
make[4]: Leaving directory `/home/vincent/teracking/opencv-1.1.0/apps/haartraining/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/vincent/teracking/opencv-1.1.0/apps/haartraining'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/vincent/teracking/opencv-1.1.0/apps'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vincent/teracking/opencv-1.1.0'
make: *** [all] Error 2

```

what does this mean and what can i do about it? please help...

---

### Post by LeBreton on 2011-08-02
Hi Kinderen

I have the same error and I wondering if you have succeed to resolve it and how you do it?

I read in others forum that it may be a problem with link.

---

