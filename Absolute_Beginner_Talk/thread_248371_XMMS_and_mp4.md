---
title: "XMMS and mp4"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by violentgandhi on 2006-09-01
I've been searching the forums and been tryinig all the solutions. I got really close when I downloaded a package and did the ./configure and it worked, but when I tried to make, it gave me an error. 

Making all in mp4ff
make[2]: Entering directory `/home/shehzad/Downloads/xmms-mp4_20050213/mp4ff'
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -DUSE_TAGGING=1    -g -O2 -MT mp4ff.lo -MD -MP -MF ".deps/mp4ff.Tpo" -c -o mp4ff.lo mp4ff.c; \
        then mv -f ".deps/mp4ff.Tpo" ".deps/mp4ff.Plo"; else rm -f ".deps/mp4ff.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -DUSE_TAGGING=1 -g -O2 -MT mp4ff.lo -MD -MP -MF .deps/mp4ff.Tpo -c mp4ff.c  -fPIC -DPIC -o .libs/mp4ff.o
mp4ff.c:104: error: static declaration of 'mp4ff_track_add' follows non-static declaration
mp4ffint.h:350: error: previous declaration of 'mp4ff_track_add' was here
mp4ff.c: In function 'mp4ff_read_sample':
mp4ff.c:431: warning: pointer targets in passing argument 2 of 'mp4ff_read_data' differ in signedness
mp4ff.c: In function 'mp4ff_read_sample_v2':
mp4ff.c:457: warning: pointer targets in passing argument 2 of 'mp4ff_read_data' differ in signedness
make[2]: *** [mp4ff.lo] Error 1
make[2]: Leaving directory `/home/shehzad/Downloads/xmms-mp4_20050213/mp4ff'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/shehzad/Downloads/xmms-mp4_20050213'
make: *** [all] Error 2


That's the error I'm getting. At this point I am also willing to just try and convert these mp4 files into some other format. It took me 2 weeks to find a media player I liked and I really don't want to switch to Amarok or Media Player, because I really like the Winamp model for a media player. 

Any help will be greatly appreciated.

Thank you

---

### Post by matko on 2006-09-01
xmms is for music and mp4 is video i think. :) try video player instead of audio player

---

