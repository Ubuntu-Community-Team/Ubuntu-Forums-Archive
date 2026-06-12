---
title: "Cinepaint troubles !"
date: 2007-05-09
forum: Art &amp; Design
---

### Post by drfalkor on 2007-05-09
I am using Fiesty, with the cinepaint from the repos... but I got to many bugs like it suddenly erase stuff and replace pixels with some other colors.. !.. this is what I get when I try to start cinepaint via the terminal, I dont know if it has something to do with that: 

> falkor@ubuntu:~$ cinepaint
Locale not found in /usr/share/locale
Locale not found in ../po
Locale not found in /usr/share/locale

** WARNING **: Cannot open selected ICC assumed image profile: /usr/share/color/icc/sRGB.icc

** WARNING **: Cannot open selected ICC editing profile: /usr/share/color/icc/LStar-RGB.icc

** WARNING **: Cannot open selected ICC display profile: /usr/share/color/icc/sRGB.icc

** WARNING **: Cannot open selected ICC default proof profile: /usr/share/color/icc/ISOcoated.icc
Searching plug-ins in path: /home/falkor/.cinepaint/plug-ins/:/usr/lib/cinepaint/0.21-2/plug-ins
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/pdbbrowse.py
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/sphere.py
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/cineon
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/gifload
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/bracketing_to_hdr
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/tga
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/rawphoto
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/psd
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/decompose
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/iff
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/dbbrowser
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/sobel
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/minimum
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/script-fu
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/gimpcons.py
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/sgi
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/shadow_bevel.py
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/foggify.py
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/noisify
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/tiff
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/collect
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/bmp
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/unsharp
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/gbr
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/jpeg
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/compose
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/openexr
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/snoise
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/sharpen
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/pic
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/screenshot
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/pdf
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/icc_examin
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/rotate
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/mblur
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/clothify.py
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/hdr
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/png
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/median
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/spread
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/fits
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/gauss_rle
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/pnm
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/dicom
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/blur
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/edge
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/xwd
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/whirlpinch.py
Loading plug-in: /usr/lib/cinepaint/0.21-2/plug-ins/psd_save
plugin count = 49
/usr/lib/cinepaint/0.21-2/plug-ins/pdbbrowse.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/sphere.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/gimpcons.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/shadow_bevel.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/foggify.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/icc_examin
/usr/lib/cinepaint/0.21-2/plug-ins/clothify.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/whirlpinch.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/script-fu
    Incorrect item=84 gimp-bfm-set-dir-dest 0 < 2
    Incorrect item=309 gimp-bfm-set-dir-src 0 < 2
script_fu_find_scripts
home, local_path = /home/falkor, /home/falkor/.cinepaint/scripts:/usr/share/cinepaint/0.21-2/scripts



Help ?:S Cinepaint is the only one painter app I am happy with in linux !! :(

---

### Post by dmn_clown on 2007-05-10
```
/usr/lib/cinepaint/0.21-2/plug-ins/pdbbrowse.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/sphere.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/gimpcons.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/shadow_bevel.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/foggify.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/icc_examin
/usr/lib/cinepaint/0.21-2/plug-ins/clothify.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/whirlpinch.py is a GIMP plug-in and must be run by GIMP to be used
wire_read: unexpected EOF (plug-in crashed?)
/usr/lib/cinepaint/0.21-2/plug-ins/script-fu
Incorrect item=84 gimp-bfm-set-dir-dest 0 < 2
Incorrect item=309 gimp-bfm-set-dir-src 0 < 2
script_fu_find_scripts
```

Remove the python scripts and gimp plugins and it should fire right up.

---

### Post by drfalkor on 2007-05-10
Thank you, but I dont think removing anything will fix my problems.

---

### Post by drfalkor on 2007-05-10
Okay, I think I solved those problems with compiling the newest cinepaint from source with gtk2 enabled... but now I have another problem, like all the other windows is overlapping the main canvas window, and It does not help to set the canvas to "always on top".. how can I fix this ? 

[http://img527.imageshack.us/my.php?image=skjermdumprb8.png](http://img527.imageshack.us/my.php?image=skjermdumprb8.png) (screenshot)

By the way: The toolbox window is working like it should !

---

### Post by drfalkor on 2007-05-11
Okay.. I've uninstalled my compiled version of cinepaint, cause the GTK2 was laggy and slow !.. and installed the ubuntu version of cinepaint.. but now... I get those "old" problems, like stuff get replaces by random four rectangle shapes and destorys all the work, here is a screenshot:

[http://img91.imageshack.us/my.php?image=skjermdumpaf3.png](http://img91.imageshack.us/my.php?image=skjermdumpaf3.png)

And here is error message from the terminal:

> ** CRITICAL **: file paintbrush.c: line 337 (paintbrush_paint_func): assertion `gdisp != NULL' failed.

** CRITICAL **: file paintbrush.c: line 337 (paintbrush_paint_func): assertion `gdisp != NULL' failed.

** CRITICAL **: file paintbrush.c: line 337 (paintbrush_paint_func): assertion `gdisp != NULL' failed.

** CRITICAL **: file paintbrush.c: line 337 (paintbrush_paint_func): assertion `gdisp != NULL' failed.

** CRITICAL **: file paintbrush.c: line 337 (paintbrush_paint_func): assertion `gdisp != NULL' failed.

** CRITICAL **: file paintbrush.c: line 337 (paintbrush_paint_func): assertion `gdisp != NULL' failed.

** CRITICAL **: file paintbrush.c: line 337 (paintbrush_paint_func): assertion `gdisp != NULL' failed.

** CRITICAL **: file paintbrush.c: line 337 (paintbrush_paint_func): assertion `gdisp != NULL' failed.

** CRITICAL **: file paintbrush.c: line 337 (paintbrush_paint_func): assertion `gdisp != NULL' failed.

** CRITICAL **: file paintbrush.c: line 337 (paintbrush_paint_func): assertion `gdisp != NULL' failed.

** CRITICAL **: file paintbrush.c: line 337 (paintbrush_paint_func): assertion `gdisp != NULL' failed.


it spits out hounders of errors like that... 

By the way, I am using a wacom tablet set to screen !

Any idea how to fix this ? anyone else having this problem ?

---

### Post by lyceum on 2007-05-11
If you can move stuff out of the way, I would get a second monitor. Even after you fix the problem, you look a little cramed. (Sorry, I know that is not really helpful :))

---

### Post by drfalkor on 2007-05-11
> **lyceum said:**
> If you can move stuff out of the way, I would get a second monitor. Even after you fix the problem, you look a little cramed. (Sorry, I know that is not really helpful :))

Hi again, tested cinepaint yet ? and what do you think of that app ?;P what do you mean by cramed ?:P

---

### Post by lyceum on 2007-05-11
> **drfalkor said:**
> Hi again, tested cinepaint yet ? and what do you think of that app ?;P what do you mean by cramed ?:P

Not yet, my sister is getting married next week, so every free moment seems to be wrapped up in helping with that. I am hoping to soon though.

As for cramed, I am use to 2 monitors, so GIMP (for example) has the GIMP box and layers box on one screen and my art on the other. It is VERY handy, as I can see everything all at once without skipping around. :)

---

### Post by drfalkor on 2007-05-11
Very nice :D hehe !

---

### Post by magicmike on 2007-06-20
Was there any progress with this? 
I get the same errors on the default cinepaint.
I have a tablet hooked up also, wonder if that's part of the problem?

---

