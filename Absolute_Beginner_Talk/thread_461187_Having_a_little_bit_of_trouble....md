---
title: "Having a little bit of trouble..."
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by sukhoi on 2007-06-01
Hey guys, I'm having some issues compiling/installing drivers for my Unichrome S3 Intergrated Graphics card. The specific card ID I've found to be the VN800 series and I've been following the OpenChrome Wiki for instructions to get everything up and running. The first thing I found truely amazing was the lack of package binaries that used to be the site that every keeps referring to. Those aren't there anymore, and haven't been for almost a year. Anyway. I make it all the way down to compiling the 2d drivers of the card and I'm supposed to input the command

Make

And I'm greeted with this error message 



sukhoi@sukhoi-laptop:~/openchrome$ make
make  all-recursive
make[1]: Entering directory `/home/sukhoi/openchrome'
Making all in unichrome
make[2]: Entering directory `/home/sukhoi/openchrome/unichrome'
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..   -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg -I/usr/include/drm   -I/usr/include/drm -I/usr/include/X11/dri   -g -O2 -MT via_accel.lo -MD -MP -MF ".deps/via_accel.Tpo" -c -o via_accel.lo via_accel.c; \
        then mv -f ".deps/via_accel.Tpo" ".deps/via_accel.Plo"; else rm -f ".deps/via_accel.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg -I/usr/include/drm -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT via_accel.lo -MD -MP -MF .deps/via_accel.Tpo -c via_accel.c  -fPIC -DPIC -o .libs/via_accel.o
In file included from via.h:31,
                 from via_accel.c:44:
/usr/include/string.h:293: error: conflicting types for 'xf86memmove'
/usr/include/string.h:44: error: previous declaration of 'xf86memmove' was here
/usr/include/string.h:296: error: conflicting types for 'xf86bzero'
/usr/include/xorg/xf86_ansic.h:294: error: previous declaration of 'xf86bzero' was here
In file included from via.h:32,
                 from via_accel.c:44:
/usr/include/stdio.h:46: error: conflicting types for 'XF86FILE'
/usr/include/xorg/xf86_libc.h:66: error: previous declaration of 'XF86FILE' was here
In file included from via.h:32,
                 from via_accel.c:44:
/usr/include/stdio.h:88: error: conflicting types for 'XF86fpos_t'
/usr/include/xorg/xf86_libc.h:71: error: previous declaration of 'XF86fpos_t' was here
In file included from via.h:32,
                 from via_accel.c:44:
/usr/include/stdio.h:142: error: conflicting types for 'xf86stdin'
/usr/include/xorg/xf86_libc.h:67: error: previous declaration of 'xf86stdin' was here
/usr/include/stdio.h:143: error: conflicting types for 'xf86stdout'
/usr/include/xorg/xf86_libc.h:68: error: previous declaration of 'xf86stdout' was here
/usr/include/stdio.h:144: error: conflicting types for 'xf86stderr'
/usr/include/xorg/xf86_libc.h:69: error: previous declaration of 'xf86stderr' was here
In file included from via.h:32,
                 from via_accel.c:44:
/usr/include/stdio.h:164:27: error: macro "tmpfile" passed 1 arguments, but takes just 0
/usr/include/stdio.h:206: error: conflicting types for 'xf86fclose'
/usr/include/xorg/xf86_ansic.h:163: error: previous declaration of 'xf86fclose' was here
/usr/include/stdio.h:211: error: conflicting types for 'xf86fflush'
/usr/include/xorg/xf86_ansic.h:166: error: previous declaration of 'xf86fflush' was here
/usr/include/stdio.h:241: error: conflicting types for 'xf86fopen'
/usr/include/xorg/xf86_ansic.h:174: error: previous declaration of 'xf86fopen' was here
/usr/include/stdio.h:247: error: conflicting types for 'xf86freopen'
/usr/include/xorg/xf86_ansic.h:182: error: previous declaration of 'xf86freopen' was here
/usr/include/stdio.h:297: error: conflicting types for 'xf86setbuf'
/usr/include/xorg/xf86_ansic.h:224: error: previous declaration of 'xf86setbuf' was here
/usr/include/stdio.h:301: error: conflicting types for 'xf86setvbuf'
/usr/include/xorg/xf86_ansic.h:225: error: previous declaration of 'xf86setvbuf' was here
/usr/include/stdio.h:322: error: conflicting types for 'xf86fprintf'
/usr/include/xorg/xf86_ansic.h:177: error: previous declaration of 'xf86fprintf' was here
/usr/include/stdio.h:336: error: conflicting types for 'xf86vfprintf'
/usr/include/xorg/xf86_ansic.h:264: error: previous declaration of 'xf86vfprintf' was here
/usr/include/stdio.h:394: error: conflicting types for 'xf86fscanf'
/usr/include/xorg/xf86_ansic.h:184: error: previous declaration of 'xf86fscanf' was here
/usr/include/stdio.h:402: error: conflicting types for 'xf86sscanf'
/usr/include/xorg/xf86_ansic.h:231: error: previous declaration of 'xf86sscanf' was here
/usr/include/stdio.h:435: error: conflicting types for 'xf86fgetc'
/usr/include/xorg/xf86_ansic.h:167: error: previous declaration of 'xf86fgetc' was here
/usr/include/stdio.h:436: error: conflicting types for 'xf86getc'
/usr/include/xorg/xf86_ansic.h:168: error: previous declaration of 'xf86getc' was here
/usr/include/stdio.h:477: error: conflicting types for 'xf86fputc'
/usr/include/xorg/xf86_ansic.h:178: error: previous declaration of 'xf86fputc' was here
/usr/include/stdio.h:484: error: syntax error before 'xf86stdout'
/usr/include/stdio.h:526: error: conflicting types for 'xf86fgets'
/usr/include/xorg/xf86_ansic.h:170: error: previous declaration of 'xf86fgets' was here
/usr/include/stdio.h:583: error: conflicting types for 'xf86fputs'
/usr/include/xorg/xf86_ansic.h:179: error: previous declaration of 'xf86fputs' was here
/usr/include/stdio.h:589: error: syntax error before 'xf86stdout'
/usr/include/stdio.h:596: error: conflicting types for 'xf86ungetc'
/usr/include/xorg/xf86_ansic.h:263: error: previous declaration of 'xf86ungetc' was here
/usr/include/stdio.h:603: error: conflicting types for 'xf86fread'
/usr/include/xorg/xf86_ansic.h:180: error: previous declaration of 'xf86fread' was here
/usr/include/stdio.h:609: error: conflicting types for 'xf86fwrite'
/usr/include/xorg/xf86_ansic.h:192: error: previous declaration of 'xf86fwrite' was here
/usr/include/stdio.h:643: error: conflicting types for 'xf86fseek'
/usr/include/xorg/xf86_ansic.h:189: error: previous declaration of 'xf86fseek' was here
/usr/include/stdio.h:648: error: conflicting types for 'xf86ftell'
/usr/include/xorg/xf86_ansic.h:191: error: previous declaration of 'xf86ftell' was here
/usr/include/stdio.h:653: error: conflicting types for 'xf86rewind'
/usr/include/xorg/xf86_ansic.h:223: error: previous declaration of 'xf86rewind' was here
/usr/include/stdio.h:692: error: conflicting types for 'xf86fgetpos'
/usr/include/xorg/xf86_ansic.h:169: error: previous declaration of 'xf86fgetpos' was here
/usr/include/stdio.h:697: error: conflicting types for 'xf86fsetpos'
/usr/include/xorg/xf86_ansic.h:190: error: previous declaration of 'xf86fsetpos' was here
/usr/include/stdio.h:720: error: conflicting types for 'xf86clearerr'
/usr/include/xorg/xf86_ansic.h:158: error: previous declaration of 'xf86clearerr' was here
/usr/include/stdio.h:722: error: conflicting types for 'xf86feof'
/usr/include/xorg/xf86_ansic.h:164: error: previous declaration of 'xf86feof' was here
/usr/include/stdio.h:724: error: conflicting types for 'xf86ferror'
/usr/include/xorg/xf86_ansic.h:165: error: previous declaration of 'xf86ferror' was here
In file included from /usr/include/stdio.h:828,
                 from via.h:32,
                 from via_accel.c:44:
/usr/include/bits/stdio.h: In function 'vprintf':
/usr/include/bits/stdio.h:36: error: 'stdout' undeclared (first use in this function)
/usr/include/bits/stdio.h:36: error: (Each undeclared identifier is reported only once
/usr/include/bits/stdio.h:36: error: for each function it appears in.)
/usr/include/bits/stdio.h: In function 'getchar':
/usr/include/bits/stdio.h:43: error: 'stdin' undeclared (first use in this function)
/usr/include/bits/stdio.h: In function 'getchar_unlocked':
/usr/include/bits/stdio.h:59: error: 'stdin' undeclared (first use in this function)
/usr/include/bits/stdio.h: At top level:
/usr/include/bits/stdio.h:66: error: syntax error before 'xf86stdout'
/usr/include/bits/stdio.h:67: error: conflicting types for 'xf86fputc'
/usr/include/xorg/xf86_ansic.h:178: error: previous declaration of 'xf86fputc' was here
/usr/include/bits/stdio.h: In function 'xf86fputc':
/usr/include/bits/stdio.h:67: error: number of arguments doesn't match prototype/usr/include/xorg/xf86_ansic.h:178: error: prototype declaration
/usr/include/bits/stdio.h:68: error: '__c' undeclared (first use in this function)
/usr/include/bits/stdio.h:68: error: 'stdout' undeclared (first use in this function)
/usr/include/bits/stdio.h: In function 'putchar_unlocked':
/usr/include/bits/stdio.h:94: error: 'stdout' undeclared (first use in this function)
via_accel.c: In function 'viaAccelTextureBlit':
via_accel.c:2641: warning: passing argument 2 of 'viaOrder' from incompatible pointer type
via_accel.c:2642: warning: passing argument 2 of 'viaOrder' from incompatible pointer type
make[2]: *** [via_accel.lo] Error 1
make[2]: Leaving directory `/home/sukhoi/openchrome/unichrome'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sukhoi/openchrome'
make: *** [all] Error 2


I'm not entireley sure what any of that means, but I know for certain that EVERYTHING else I've done before this step went pefectly fine. I'm at a loss of what to do here because no one on these forums that I've search over (pages and pages and pages worth) can form a coherent sentence to retell their breakthrough of magically finding how to get this card to do anything. 

Now I know my issue is probably something as simple as a typo, but any help would be really appreciated. As long as I'm not led in circles to year old forums posts and to website that are dead with no support or troubleshooting page.

Thanks in advance,
Sukhoi

---

### Post by sukhoi on 2007-06-01
Bump. >_< hope I wasn't too mean. All of this is so fusturating..

---

