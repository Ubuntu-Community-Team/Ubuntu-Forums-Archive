---
title: "So much for a step-by-step..."
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by Kasanax on 2005-12-27
I've been reading through "Linux for Non-Geeks" (Okay, maybe I *am* a geek, but the book still helps! :smile: ) - I'm trying to compile xMahjongg, with the help of the chapter on tarballs, and I'm having some trouble.

At first, I was missing a compiler, so I had to go back and install 'build-essential'. This solved the first problem, but now I'm getting a new set of issues. When I enter the 'make' command, I get the following output:

```
make  all-recursive
make[1]: Entering directory `/home/mike/Desktop/xmahjongg-3.7'
Making all in liblcdf
make[2]: Entering directory `/home/mike/Desktop/xmahjongg-3.7/liblcdf'
if gcc -Wall -DHAVE_CONFIG_H -I. -I. -I..  -I../include    -g -O2 -MT gifx.o -MD  -MP -MF ".deps/gifx.Tpo" -c -o gifx.o gifx.c; \
then mv -f ".deps/gifx.Tpo" ".deps/gifx.Po"; else rm -f ".deps/gifx.Tpo"; exit 1 ; fi
In file included from gifx.c:18:
../include/lcdfgif/gifx.h:22:22: error: X11/Xlib.h: No such file or directory
In file included from gifx.c:18:
../include/lcdfgif/gifx.h:32: error: syntax error before ‘Display’
../include/lcdfgif/gifx.h:32: warning: no semicolon at end of struct or union
../include/lcdfgif/gifx.h:34: error: syntax error before ‘drawable’
../include/lcdfgif/gifx.h:34: warning: type defaults to ‘int’ in declaration of ‘drawable’
../include/lcdfgif/gifx.h:34: warning: data definition has no type or storage cl ass
../include/lcdfgif/gifx.h:35: error: syntax error before ‘*’ token
../include/lcdfgif/gifx.h:35: warning: type defaults to ‘int’ in declaration of ‘visual’
../include/lcdfgif/gifx.h:35: warning: data definition has no type or storage cl ass
../include/lcdfgif/gifx.h:38: error: syntax error before ‘colormap’
../include/lcdfgif/gifx.h:38: warning: type defaults to ‘int’ in declaration of ‘colormap’
../include/lcdfgif/gifx.h:38: warning: data definition has no type or storage cl ass
../include/lcdfgif/gifx.h:46: error: syntax error before ‘image_gc’
../include/lcdfgif/gifx.h:46: warning: type defaults to ‘int’ in declaration of ‘image_gc’
../include/lcdfgif/gifx.h:46: warning: data definition has no type or storage cl ass
../include/lcdfgif/gifx.h:47: error: syntax error before ‘mask_gc’
../include/lcdfgif/gifx.h:47: warning: type defaults to ‘int’ in declaration of ‘mask_gc’
../include/lcdfgif/gifx.h:47: warning: data definition has no type or storage cl ass
../include/lcdfgif/gifx.h:53: error: syntax error before ‘}’ token
../include/lcdfgif/gifx.h:56: error: syntax error before ‘*’ token
../include/lcdfgif/gifx.h:57: error: syntax error before ‘*’ token
../include/lcdfgif/gifx.h:61: error: syntax error before ‘Gif_XImage’
../include/lcdfgif/gifx.h:61: warning: type defaults to ‘int’ in declaration of ‘Gif_XImage’
../include/lcdfgif/gifx.h:61: warning: data definition has no type or storage cl ass
../include/lcdfgif/gifx.h:62: error: syntax error before ‘Gif_XImageColormap’
../include/lcdfgif/gifx.h:63: warning: type defaults to ‘int’ in declaration of ‘Gif_XImageColormap’
../include/lcdfgif/gifx.h:63: warning: data definition has no type or storage cl ass
../include/lcdfgif/gifx.h:64: error: syntax error before ‘Gif_XSubImage’
../include/lcdfgif/gifx.h:65: warning: type defaults to ‘int’ in declaration of ‘Gif_XSubImage’
../include/lcdfgif/gifx.h:65: warning: data definition has no type or storage cl ass
../include/lcdfgif/gifx.h:66: error: syntax error before ‘Gif_XSubImageColormap’
../include/lcdfgif/gifx.h:67: warning: type defaults to ‘int’ in declaration of ‘Gif_XSubImageColormap’
../include/lcdfgif/gifx.h:67: warning: data definition has no type or storage cl ass
../include/lcdfgif/gifx.h:69: error: syntax error before ‘Gif_XMask’
../include/lcdfgif/gifx.h:69: warning: type defaults to ‘int’ in declaration of ‘Gif_XMask’
../include/lcdfgif/gifx.h:69: warning: data definition has no type or storage cl ass
../include/lcdfgif/gifx.h:70: error: syntax error before ‘Gif_XSubMask’
../include/lcdfgif/gifx.h:71: warning: type defaults to ‘int’ in declaration of ‘Gif_XSubMask’
../include/lcdfgif/gifx.h:71: warning: data definition has no type or storage cl ass
../include/lcdfgif/gifx.h:73: error: syntax error before ‘Gif_XNextImage’
../include/lcdfgif/gifx.h:73: error: syntax error before ‘Pixmap’
../include/lcdfgif/gifx.h:74: warning: type defaults to ‘int’ in declaration of ‘Gif_XNextImage’
../include/lcdfgif/gifx.h:74: warning: data definition has no type or storage cl ass
gifx.c:19:23: error: X11/Xutil.h: No such file or directory
gifx.c: In function ‘load_closest’:
gifx.c:48: error: ‘XColor’ undeclared (first use in this function)
gifx.c:48: error: (Each undeclared identifier is reported only once
gifx.c:48: error: for each function it appears in.)
gifx.c:48: error: ‘color’ undeclared (first use in this function)
gifx.c:53: error: dereferencing pointer to incomplete type
gifx.c:55: error: dereferencing pointer to incomplete type
gifx.c:57: error: syntax error before ‘)’ token
gifx.c:57: error: syntax error before ‘)’ token
gifx.c:65: warning: implicit declaration of function ‘XQueryColors’
gifx.c:65: error: dereferencing pointer to incomplete type
gifx.c:65: error: dereferencing pointer to incomplete type
gifx.c:67: error: dereferencing pointer to incomplete type
gifx.c:69: error: dereferencing pointer to incomplete type
gifx.c:76: error: dereferencing pointer to incomplete type
gifx.c: In function ‘allocate_closest’:
gifx.c:92: error: dereferencing pointer to incomplete type
gifx.c:92: warning: value computed is not used
gifx.c:92: error: dereferencing pointer to incomplete type
gifx.c:105: error: ‘XColor’ undeclared (first use in this function)
gifx.c:105: error: syntax error before ‘xcol’
gifx.c:106: error: ‘xcol’ undeclared (first use in this function)
gifx.c:109: warning: implicit declaration of function ‘XAllocColor’
gifx.c:109: error: dereferencing pointer to incomplete type
gifx.c:109: error: dereferencing pointer to incomplete type
gifx.c:111: error: dereferencing pointer to incomplete type
gifx.c:111: error: dereferencing pointer to incomplete type
gifx.c:112: error: dereferencing pointer to incomplete type
gifx.c: In function ‘allocate_colors’:
gifx.c:130: error: ‘XColor’ undeclared (first use in this function)
gifx.c:130: error: syntax error before ‘xcol’
gifx.c:135: error: ‘xcol’ undeclared (first use in this function)
gifx.c:138: error: dereferencing pointer to incomplete type
gifx.c:138: error: dereferencing pointer to incomplete type
gifx.c: In function ‘deallocate_colors’:
gifx.c:153: warning: implicit declaration of function ‘XFreeColors’
gifx.c:153: error: dereferencing pointer to incomplete type
gifx.c:153: error: dereferencing pointer to incomplete type
gifx.c: In function ‘create_x_colormap_extension’:
gifx.c:173: error: dereferencing pointer to incomplete type
gifx.c:174: error: dereferencing pointer to incomplete type
gifx.c: In function ‘find_x_colormap_extension’:
gifx.c:186: error: dereferencing pointer to incomplete type
gifx.c: At top level:
gifx.c:270: error: syntax error before ‘Pixmap’
gifx.c: In function ‘put_sub_image_colormap’:
gifx.c:272: error: ‘XImage’ undeclared (first use in this function)
gifx.c:272: error: ‘ximage’ undeclared (first use in this function)
gifx.c:284: error: ‘gfi’ undeclared (first use in this function)
gifx.c:285: error: ‘gfx’ undeclared (first use in this function)
gifx.c:286: warning: implicit declaration of function ‘XCreateGC’
gifx.c:286: error: ‘pixmap’ undeclared (first use in this function)
gifx.c:297: error: ‘width’ undeclared (first use in this function)
gifx.c:297: error: ‘height’ undeclared (first use in this function)
gifx.c:297: error: ‘left’ undeclared (first use in this function)
gifx.c:297: error: ‘top’ undeclared (first use in this function)
gifx.c:304: error: ‘gfcm’ undeclared (first use in this function)
gifx.c:325: warning: implicit declaration of function ‘XCreateImage’
gifx.c:326: error: ‘XYBitmap’ undeclared (first use in this function)
gifx.c:326: error: ‘ZPixmap’ undeclared (first use in this function)
gifx.c:329: error: ‘LSBFirst’ undeclared (first use in this function)
gifx.c:392: warning: implicit declaration of function ‘XPutImage’
gifx.c:393: error: ‘pixmap_x’ undeclared (first use in this function)
gifx.c:393: error: ‘pixmap_y’ undeclared (first use in this function)
gifx.c:397: warning: implicit declaration of function ‘XDestroyImage’
gifx.c: At top level:
gifx.c:407: error: syntax error before ‘Gif_XSubImageColormap’
gifx.c:409: warning: return type defaults to ‘int’
gifx.c: In function ‘Gif_XSubImageColormap’:
gifx.c:410: error: ‘Pixmap’ undeclared (first use in this function)
gifx.c:410: error: syntax error before ‘pixmap’
gifx.c:412: error: ‘pixmap’ undeclared (first use in this function)
gifx.c:417: warning: implicit declaration of function ‘XFreePixmap’
gifx.c:417: error: dereferencing pointer to incomplete type
gifx.c:419: error: ‘None’ undeclared (first use in this function)
gifx.c: At top level:
gifx.c:423: error: syntax error before ‘Gif_XImage’
gifx.c:424: warning: return type defaults to ‘int’
gifx.c: In function ‘Gif_XImage’:
gifx.c:427: error: ‘None’ undeclared (first use in this function)
gifx.c: At top level:
gifx.c:435: error: syntax error before ‘Gif_XImageColormap’
gifx.c:437: warning: return type defaults to ‘int’
gifx.c: In function ‘Gif_XImageColormap’:
gifx.c:439: error: ‘None’ undeclared (first use in this function)
gifx.c: At top level:
gifx.c:445: error: syntax error before ‘Gif_XSubImage’
gifx.c:447: warning: return type defaults to ‘int’
gifx.c: In function ‘Gif_XSubImage’:
gifx.c:450: error: ‘None’ undeclared (first use in this function)
gifx.c: At top level:
gifx.c:459: error: syntax error before ‘Gif_XSubMask’
gifx.c:461: warning: return type defaults to ‘int’
gifx.c: In function ‘Gif_XSubMask’:
gifx.c:462: error: ‘Pixmap’ undeclared (first use in this function)
gifx.c:462: error: syntax error before ‘pixmap’
gifx.c:463: error: ‘XImage’ undeclared (first use in this function)
gifx.c:463: error: ‘ximage’ undeclared (first use in this function)
gifx.c:472: error: ‘None’ undeclared (first use in this function)
gifx.c:488: error: dereferencing pointer to incomplete type
gifx.c:488: error: dereferencing pointer to incomplete type
gifx.c:489: error: ‘XYBitmap’ undeclared (first use in this function)
gifx.c:493: error: ‘LSBFirst’ undeclared (first use in this function)
gifx.c:523: error: ‘pixmap’ undeclared (first use in this function)
gifx.c:524: warning: implicit declaration of function ‘XCreatePixmap’
gifx.c:524: error: dereferencing pointer to incomplete type
gifx.c:524: error: dereferencing pointer to incomplete type
gifx.c:525: error: dereferencing pointer to incomplete type
gifx.c:526: error: dereferencing pointer to incomplete type
gifx.c:526: error: dereferencing pointer to incomplete type
gifx.c:528: error: dereferencing pointer to incomplete type
gifx.c:529: error: dereferencing pointer to incomplete type
gifx.c:529: error: dereferencing pointer to incomplete type
gifx.c: At top level:
gifx.c:544: error: syntax error before ‘Gif_XMask’
gifx.c:545: warning: return type defaults to ‘int’
gifx.c: In function ‘Gif_XMask’:
gifx.c:547: error: ‘None’ undeclared (first use in this function)
gifx.c: At top level:
gifx.c:553: error: syntax error before ‘Gif_XNextImage’
gifx.c:553: error: syntax error before ‘Pixmap’
gifx.c:555: warning: return type defaults to ‘int’
gifx.c: In function ‘Gif_XNextImage’:
gifx.c:556: error: ‘Pixmap’ undeclared (first use in this function)
gifx.c:556: error: syntax error before ‘pixmap’
gifx.c:557: error: ‘gfs’ undeclared (first use in this function)
gifx.c:557: error: ‘n’ undeclared (first use in this function)
gifx.c:561: error: ‘gfx’ undeclared (first use in this function)
gifx.c:564: error: ‘None’ undeclared (first use in this function)
gifx.c:571: error: ‘pixmap’ undeclared (first use in this function)
gifx.c:576: error: ‘last’ undeclared (first use in this function)
gifx.c:592: warning: implicit declaration of function ‘XSetForeground’
gifx.c:602: warning: implicit declaration of function ‘XFillRectangle’
gifx.c:611: warning: implicit declaration of function ‘XCopyArea’
gifx.c:613: error: ‘last_last’ undeclared (first use in this function)
gifx.c:628: error: ‘image’ undeclared (first use in this function)
gifx.c:629: error: ‘mask’ undeclared (first use in this function)
gifx.c:631: warning: implicit declaration of function ‘XSetClipMask’
gifx.c:632: warning: implicit declaration of function ‘XSetClipOrigin’
gifx.c: In function ‘delete_xcolormap’:
gifx.c:658: error: dereferencing pointer to incomplete type
gifx.c:663: error: dereferencing pointer to incomplete type
gifx.c:668: error: dereferencing pointer to incomplete type
gifx.c: In function ‘delete_colormap_hook’:
gifx.c:680: error: dereferencing pointer to incomplete type
gifx.c: At top level:
gifx.c:689: error: syntax error before ‘*’ token
gifx.c: In function ‘Gif_NewXContextFromVisual’:
gifx.c:694: error: invalid application of ‘sizeof’ to incomplete type ‘Gif_XCont ext’
gifx.c:695: error: dereferencing pointer to incomplete type
gifx.c:695: error: ‘display’ undeclared (first use in this function)
gifx.c:696: error: dereferencing pointer to incomplete type
gifx.c:697: error: dereferencing pointer to incomplete type
gifx.c:697: warning: implicit declaration of function ‘RootWindow’
gifx.c:699: error: dereferencing pointer to incomplete type
gifx.c:700: error: dereferencing pointer to incomplete type
gifx.c:701: error: dereferencing pointer to incomplete type
gifx.c:701: error: request for member ‘map_entries’ in something not a structure  or union
gifx.c:702: error: dereferencing pointer to incomplete type
gifx.c:704: error: dereferencing pointer to incomplete type
gifx.c:705: error: dereferencing pointer to incomplete type
gifx.c:707: error: dereferencing pointer to incomplete type
gifx.c:708: error: dereferencing pointer to incomplete type
gifx.c:710: error: dereferencing pointer to incomplete type
gifx.c:710: error: ‘None’ undeclared (first use in this function)
gifx.c:711: error: dereferencing pointer to incomplete type
gifx.c:713: error: dereferencing pointer to incomplete type
gifx.c:714: error: dereferencing pointer to incomplete type
gifx.c:715: error: dereferencing pointer to incomplete type
gifx.c: At top level:
gifx.c:723: error: syntax error before ‘*’ token
gifx.c: In function ‘Gif_NewXContext’:
gifx.c:725: error: ‘XWindowAttributes’ undeclared (first use in this function)
gifx.c:725: error: syntax error before ‘attr’
gifx.c:726: warning: implicit declaration of function ‘XGetWindowAttributes’
gifx.c:726: error: ‘display’ undeclared (first use in this function)
gifx.c:726: error: ‘window’ undeclared (first use in this function)
gifx.c:726: error: ‘attr’ undeclared (first use in this function)
gifx.c:727: warning: implicit declaration of function ‘XScreenNumberOfScreen’
gifx.c: In function ‘Gif_DeleteXContext’:
gifx.c:736: error: dereferencing pointer to incomplete type
gifx.c:737: error: dereferencing pointer to incomplete type
gifx.c:738: error: dereferencing pointer to incomplete type
gifx.c:739: error: dereferencing pointer to incomplete type
gifx.c:740: warning: implicit declaration of function ‘XFreeGC’
gifx.c:740: error: dereferencing pointer to incomplete type
gifx.c:740: error: dereferencing pointer to incomplete type
gifx.c:741: error: dereferencing pointer to incomplete type
gifx.c:742: error: dereferencing pointer to incomplete type
gifx.c:742: error: dereferencing pointer to incomplete type
gifx.c:743: error: dereferencing pointer to incomplete type
make[2]: *** [gifx.o] Error 1
make[2]: Leaving directory `/home/mike/Desktop/xmahjongg-3.7/liblcdf'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mike/Desktop/xmahjongg-3.7'
make: *** [all] Error 2

```


I'm a newbie (hence the book), so the info I've found on the problem (similar errors from others trying to compile other programs) didn't make all that much sense... maybe I'm missing a library or two?:confused: 

Any help would be greatly appreciated!!:D

---

### Post by John.Michael.Kane on 2005-12-27
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)
also you may need build-essential

---

### Post by Kasanax on 2005-12-27
Actually, I had to install build-essential to fix an earlier issue (the configuration step was telling me that it couldn't find a compiler, but this was fixed when I installed build-essential).

Any other suggestions?

---

### Post by cwaldbieser on 2005-12-28
[QUOTE=Kasanax]Actually, I had to install build-essential to fix an earlier issue (the configuration step was telling me that it couldn't find a compiler, but this was fixed when I installed build-essential).

Any other suggestions?[/QUOTE]
You may need the development headers for the library you are linking against.  Try getting the package "libx11-dev".

---

### Post by aysiu on 2005-12-28
Any reason you want to compile it from source?
See the first link in my sig.
Then ```
sudo apt-get update
sudo apt-get install xmahjongg
```

---

### Post by Kasanax on 2005-12-28
I'm new to all this, and I think the best way to learn is by doing. That's why I'm trying to compile it from the source!:smile:

---

### Post by Kasanax on 2005-12-28
I installed libx11-dev, and it worked!

Thanks to everyone, especially cwaldbieser!

---

