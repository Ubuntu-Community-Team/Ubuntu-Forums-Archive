---
title: "ffmpeg --enable xvid"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by hackarre on 2007-04-22
Hi, 

I have just installed ubntu festy fawn and I wanted to convert my videos to my ipod. Before I used to use thinliquidfilm, the problem is that I need to have enabled xvid in ffmpeg, I have followed 3 guides, which I think they saied the same, but when I put make, this error show up:

./libavcodec/libavcodec.so: undefined reference to `x264_encoder'
collect2: ld va retornar l'estat de sortida 1
make: *** [ffmpeg_g] Error 1


Is in Festy different? 

If the version is useful: 
[email]hackarre@hackarre-desktop:~/ffmpeg-0.cvs[/email]20060823$

---

### Post by RobsterUK on 2007-04-22
Please post a link to the tutorial you followed so people can see what you've done

---

### Post by hackarre on 2007-04-22
[https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)

That one!

Thank you!

---

### Post by hackarre on 2007-04-23
[email]hackarre@hackarre-desktop:~/ffmpeg-0.cvs[/email]20060823$ make
/home/hackarre/ffmpeg-0.cvs20060823/version.sh "/home/hackarre/ffmpeg-0.cvs20060823"
make -C libavutil   all
make[1]: Entering directory `/home/hackarre/ffmpeg-0.cvs20060823/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/hackarre/ffmpeg-0.cvs20060823/libavutil'
make -C libavcodec  all
make[1]: Entering directory `/home/hackarre/ffmpeg-0.cvs20060823/libavcodec'
gcc -DHAVE_AV_CONFIG_H -I.. -I/home/hackarre/ffmpeg-0.cvs20060823/libavutil -O3  -pthread -Wdeclaration-after-statement -Wall -Wno-switch -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE    -c -o x264.o x264.c
x264.c: In function ‘X264_init’:
x264.c:147: error: ‘struct <anonymous>’ has no member named ‘i_rf_constant’
make[1]: *** [x264.o] Error 1
make[1]: Leaving directory `/home/hackarre/ffmpeg-0.cvs20060823/libavcodec'
make: *** [lib] Error 2


There is any library I need or something?

Please I really need to convert my ipod videos

---

### Post by hackarre on 2007-04-24
Please I beg you I really need help :(

---

### Post by dharrigan on 2007-04-25
Hi,

Change line 147 in libavcodec/x264.c from

    x4->params.rc.i_rf_constant = avctx->crf

to

    x4->params.rc.f_rf_constant = avctx->crf

(notice the f instead of the i)

-=david=-

---

### Post by slim_chiply on 2007-04-27
That change did the trick.  Thanks. 

One thing I noticed is that after I made x264.c edit, I was getting a 'libavcodec.so: undefined reference to `x264_encoder' error. 

I did a 'make clean' and the configure again.  That seemed to do the trick.

Just in case anyone gets stuck.

Slim

---

### Post by gubemton on 2007-10-27
hi, i'm a total newb so i was wondering how you would be able to change lines. ty in advance :)

---

