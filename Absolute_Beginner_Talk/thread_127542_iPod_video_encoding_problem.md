---
title: "iPod video encoding problem"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by Edward The Bonobo on 2006-02-09
I've followed the instructions on the wiki - [https://wiki.ubuntu.com/iPodVideoEncoding](https://wiki.ubuntu.com/iPodVideoEncoding) but it doesn't work for me.

I had the following problems:
[LIST=1]
[*]In the Configure step, I had a couple of errors, 'array type has incomplete element type'
[*]Checkinstall gave me 'command not found'.  I used 'Sudo make install' instead, as instructed...but I didn't get any of the prompts I was expecting.
[*]When I run the ipodvidenc script, I'm getting 'ffmpeg command not found' and '-acodec command not found'
[/LIST]

Any ideas?

Why won't checkinstall work anyway?

---

### Post by davmac on 2006-02-09
Sounds like the compilation hasn't worked. You mention that you got some error/warning messages from the configure step. Can you post these back here?

You then go on to say there was a problem with the checkinstall and the sudo make install, but did you run a "make" between the configure and checkinstall? If this is the case you won't have actually compiled anything and there'll be nothing to install.

Hope this helps,

Dave Mac

---

### Post by Edward The Bonobo on 2006-02-09
Thanks.

Correction...I got the errors on Make, not Configure.  Here's the relevant lines.  C&P from the wiki highlighted in [COLOR="Orange"]orange.[/COLOR]

(Sorry - I don't know how to do that cool thing where you paste a grey box)

[email]bonobo@cpc1-eswd2-4-1-cust78:~/ffmpeg-0.cvs[/email]20050121$ ./configure [COLOR="Orange"]--enable-gpl --enable-pp --enable-zlib --enable-vorbis \
>         --enable-libogg --enable-theora --enable-a52 --enable-dts \
>         --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
>         --enable-faad --enable-faac --enable-xvid[/COLOR]
Install prefix   /usr/local
Source path      /home/bonobo/ffmpeg-0.cvs20050121
C compiler       gcc
make             make
CPU              x86 (generic)
Big Endian       no
inttypes.h       yes
broken inttypes.h no
MMX enabled      yes
Vector Builtins  no
gprof enabled    no
zlib enabled     yes
mp3lame enabled  yes
vorbis enabled   yes
faad enabled     yes
faadbin enabled  no
faac enabled     yes
xvid enabled     yes
a52 support      yes
a52 dlopened     no
dts support      yes
pp support       yes
debug symbols    no
strip symbols    yes
optimize         yes
shared pp        no
Video hooking    yes
SDL support      yes
risky / patent encumbered codecs yes
Imlib2 support   yes
freetype support yes
Sun medialib support no
pthreads support no
AMR-NB float support no
AMR-NB fixed support no
AMR-WB float support no
network support      yes
IPv6 support         yes
License: GPL
Creating config.mak and config.h
config.h is unchanged
[email]bonobo@cpc1-eswd2-4-1-cust78:~/ffmpeg-0.cvs[/email]20050121$ [COLOR="Orange"]make[/COLOR]
make -C libavcodec all
make[1]: Entering directory `/home/bonobo/ffmpeg-0.cvs20050121/libavcodec'
gcc -O3 -Wall -Wno-switch  -DHAVE_AV_CONFIG_H -I.. -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE  -c -o b itstream.o bitstream.c
In file included from avcodec.h:14,
                 from bitstream.c:28:
common.h:59: error: array type has incomplete element type
common.h:63: error: array type has incomplete element type
make[1]: *** [bitstream.o] Error 1
make[1]: Leaving directory `/home/bonobo/ffmpeg-0.cvs20050121/libavcodec'
make: *** [lib] Error 2
[email]bonobo@cpc1-eswd2-4-1-cust78:~/ffmpeg-0.cvs[/email]20050121$ [COLOR="Orange"]sudo checkinstall -D make install[/COLOR]
sudo: checkinstall: command not found
[email]bonobo@cpc1-eswd2-4-1-cust78:~/ffmpeg-0.cvs[/email]20050121$ [COLOR="Orange"]sudo make install[/COLOR]
make -C libavcodec all
make[1]: Entering directory `/home/bonobo/ffmpeg-0.cvs20050121/libavcodec'
gcc -O3 -Wall -Wno-switch  -DHAVE_AV_CONFIG_H -I.. -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE  -c -o b itstream.o bitstream.c
In file included from avcodec.h:14,
                 from bitstream.c:28:
common.h:59: error: array type has incomplete element type
common.h:63: error: array type has incomplete element type
make[1]: *** [bitstream.o] Error 1
make[1]: Leaving directory `/home/bonobo/ffmpeg-0.cvs20050121/libavcodec'
make: *** [lib] Error 2
[email]bonobo@cpc1-eswd2-4-1-cust78:~/ffmpeg-0.cvs[/email]20050121$

---

### Post by davmac on 2006-02-10
[QUOTE=Edward The Bonobo]In file included from avcodec.h:14,
                 from bitstream.c:28:
common.h:59: error: array type has incomplete element type
common.h:63: error: array type has incomplete element type
make[1]: *** [bitstream.o] Error 1
make[1]: Leaving directory `/home/bonobo/ffmpeg-0.cvs20050121/libavcodec'
make: *** [lib] Error 2
[/QUOTE]

Hmmm. I think this is the relevant part and looks like something going wrong with the source code. It doesn't sound like you're doing anything wrong.

Sorry, can't be of more help.

BTW: It looks like need to install checkinstall - a simple "sudo apt-get install checkinstall" will do it.

Regards,

Dave Mac

---

### Post by endersshadow on 2006-02-17
In your ffmpeg folder, there's a folder called libavutil.  Inside that folder is a file called common.h.  Use gedit to open that, and past in lines 50-70 here.  On mine, 59 is a commented line (ergo, should not have any error), and 63 is an #endif line...

Also, what gcc version are you using? (gcc --version in the terminal)

---

### Post by Edward The Bonobo on 2006-02-20
Thanks for responding.  I won't be able to look at this for a couple of days (I'll be away from my Ubuntu machine) - so I'd be grateful if tou'd keep an eye on this thread.


btw - I remember reading the first Ender Wiggins story in Analog magazine.  It must have been about 25 years ago!

---

### Post by patsissons on 2006-03-03
for anyone still having trouble, i've created a deb file for ffmpeg that includes support for most of the codecs (all required for ipod video).    check this thread for more info (near the bottom):

[http://www.ubuntuforums.org/showthread.php?t=114946&page=14](http://www.ubuntuforums.org/showthread.php?t=114946&page=14)

---

### Post by Edward The Bonobo on 2006-03-03
Thanks for following this up.

Great!  The deb should simplify things for me - that plus endershadow's Vine front-end.

---

### Post by rvrichie on 2006-10-10
> **endersshadow said:**
> In your ffmpeg folder, there's a folder called libavutil.  Inside that folder is a file called common.h.  Use gedit to open that, and past in lines 50-70 here.  On mine, 59 is a commented line (ergo, should not have any error), and 63 is an #endif line...

Also, what gcc version are you using? (gcc --version in the terminal)

This was the code in common.h

65  struct AVOption;
66  #ifdef HAVE_MMX
67  extern const struct AVOption avoptions_common[3 + 5];
68  #else
69  extern const struct AVOption avoptions_common[3];
70  #endif
71  extern const struct AVOption avoptions_workaround_bug[11];
72  
73  #endif /* HAVE_AV_CONFIG_H */

I'm using Fedora Core 4 and I'm sure that this is not the problem with the dist but the gcc. My guess is that I'm using gcc4, but I can check this out when I come home.
I saw on some other forum that the solution is next:
instead of avoptions_common[3+5]; I should put *avoptions_common;
Is this true?!?:-k

---

