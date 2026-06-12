---
title: "Un-make?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by jmap82 on 2008-03-09
So, with the exception of a couple system incompatibilities that can usually be looked over after a couple reboots, I'm very excited to be new-born member of the Ubuntu/Linux community.

My problem today, that I can't seem to find and answer for is largely a product of my "Absolute Beginner" status, and the fact that I'm trying to do things that I'm really not equipped to do.

Enough prologue, my problem is this:

At first I wanted Hamachi, from Logmein.com.  They have a Linux compatible version, but unfortunately not a "jmap82" compatible version, but I tried it anyways.  After running the "make install" commands followed by a couple other sudo commands I was instructed to do by the README I realized I was in over my head...

From there I wanted to undo what I had done, but I didn't know how.  Unfortunately there doesn't seem to be an "unmake install" command available in the terminal.

This is were I should have stopped until I found directions, mind you I looked, I just didn't find them.  But as is the case with most trial by fire experiences, I pressed on further than I should have and came across "gHamachi-gtk2".

Using my "Absolute Beginner" rationalization skills I concluded that either the program is different enough that it won't conflict with the Hamachi things I previously installed on my system, or they are similar enough that they might just compliment each other.  And like a moth to the flame, I "make gHamachi"-ed as the README told me, and I actually felt like I was on the right track until I tried to run it and this happend:

```
jmap82@JMAP1:~/Desktop$ cd gHamachi_gtk2
jmap82@JMAP1:~/Desktop/gHamachi_gtk2$ make ghamachi
make: Nothing to be done for `ghamachi'.
jmap82@JMAP1:~/Desktop/gHamachi_gtk2$ dir
ghamachi  README
jmap82@JMAP1:~/Desktop/gHamachi_gtk2$ chmod +x ghamachi
jmap82@JMAP1:~/Desktop/gHamachi_gtk2$ ./ghamachi

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:7043): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:7043): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:7043): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:7043): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:7043): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:7043): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:7043): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:7043): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(ghamachi:7043): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed
*** glibc detected *** ./ghamachi: free(): invalid next size (fast): 0x081c4ff0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7755d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7759800]
./ghamachi[0x805a5d4]
./ghamachi[0x805a313]
======= Memory map: ========
08048000-0805b000 r-xp 00000000 03:01 1008153    /home/jmap82/Desktop/gHamachi_gtk2/ghamachi
0805b000-0806e000 rwxp 00012000 03:01 1008153    /home/jmap82/Desktop/gHamachi_gtk2/ghamachi
0806e000-081ce000 rwxp 0806e000 00:00 0          [heap]
b6200000-b6221000 rwxp b6200000 00:00 0 
b6221000-b6300000 ---p b6221000 00:00 0 
b63b0000-b63ba000 r-xp 00000000 03:01 953507     /lib/libgcc_s.so.1
b63ba000-b63bb000 rwxp 0000a000 03:01 953507     /lib/libgcc_s.so.1
b63bb000-b63dc000 rwxp b63bb000 00:00 0 
b63dc000-b7245000 r-xs 00000000 03:01 420330     /var/lib/anthy/anthy.dic
b7245000-b7287000 rwxp b7245000 00:00 0 
b7287000-b72c2000 r-xp 00000000 03:01 712907     /usr/lib/libanthydic.so.0.1.0
b72c2000-b72c6000 rwxp 0003b000 03:01 712907     /usr/lib/libanthydic.so.0.1.0
b72c6000-b72d4000 r-xp 00000000 03:01 711756     /usr/lib/libanthy.so.0.1.0
b72d4000-b72d5000 rwxp 0000d000 03:01 711756     /usr/lib/libanthy.so.0.1.0
b72e4000-b72fc000 r-xp 00000000 03:01 727700     /usr/lib/gconv/libJIS.so
b72fc000-b72fe000 rwxp 00017000 03:01 727700     /usr/lib/gconv/libJIS.so
b72fe000-b731f000 rwxp b72fe000 00:00 0 
b7321000-b7342000 rwxp b7321000 00:00 0 
b7342000-b7364000 r-xp 00000000 03:01 714223     /usr/lib/libuim.so.5.0.0
b7364000-b7367000 rwxp 00021000 03:01 714223     /usr/lib/libuim.so.5.0.0
b7367000-b7368000 rwxp b7367000 00:00 0 
b736f000-b7371000 r-xp 00000000 03:01 777269     /usr/lib/uim/plugin/libuim-anthy.so
b7371000-b7372000 rwxp 00001000 03:01 777269     /usr/lib/uim/plugin/libuim-anthy.so
b7372000-b7375000 r-xp 00000000 03:01 727528     /usr/lib/gconv/EUC-JP.so
b7375000-b7377000 rwxp 00002000 03:01 727528     /usr/lib/gconv/EUC-JP.so
b7377000-b7387000 r-xp 00000000 03:01 761776     /usr/lib/gtk-2.0/2.10.0/immodules/im-uim.so
b7387000-b7388000 rwxp 00010000 03:01 761776     /usr/lib/gtk-2.0/2.10.0/immodules/im-uim.so
b7388000-b73ab000 r-xp 00000000 03:01 372520     /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
b73ab000-b73ad000 r-xp 00000000 03:01 744659     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b73ad000-b73ae000 rwxp 00001000 03:01 744659     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b73ae000-b73b4000 r-xs 00000000 03:01 312939     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b73b4000-b73b7000 r-xs 00000000 03:01 312977     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b73b7000-b73bb000 r-xs 00000000 03:01 312976     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b73bb000-b73bc000 r-xs 00000000 03:01 312975     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b73bc000-b73bd000 r-xs 00000000 03:01 312974     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b73bd000-b73c0000 r-xs 00000000 03:01 312973     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b73c0000-b73c1000 r-xs 00000000 03:01 312972     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b73c1000-b73c7000 r-xs 00000000 03:01 312971     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b73c7000-b73c9000 r-xs 00000000 03:01 312932     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b73c9000-b73d1000 r-xs 00000000 03:01 312919     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b73d1000-b73d7000 r-xs 00000000 03:01 312901     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b73d7000-b73d8000 r-xs 00000000 03:01 312796     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b73d8000-b73f0000 r-xs 00000000 03:01 312783     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b73f0000-b73f2000 r-xs 00000000 03:01 312776     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b73f2000-b73f5000 r-xs 00000000 03:01 312620     /var/cache/fontconfig/10310103cdb8be96361c454174097f13-x86.cache-2
b73f5000-b73f8000 r-xs 00000000 03:01 312617     /var/cache/fontconfig/74390c08174a57db0ac108af95f71bcb-x86.cache-2
b73f8000-b73fe000 r-xs 00000000 03:01 312566     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b73fe000-b7402000 r-xs 00000000 03:01 307125     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b7402000-b7409000 r-xs 00000000 03:01 309666     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b7409000-b740a000 r-xs 00000000 03:01 313061     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b740a000-b740b000 r-xs 00000000 03:01 313060     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b740b000-b740c000 r-xs 00000000 03:01 313059     /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b740c000-b740f000 r-xs 00000000 03:01 313058     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b740f000-b7412000 r-xs 00000000 03:01 313057     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b7412000-b7419000 r-xs 00000000 03:01 313056     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b7419000-b741b000 r-xs 00000000 03:01 313055     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b741b000-b741c000 r-xs 00000000 03:01 313054     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b741c000-b741d000 r-xs 00000000 03:01 313053     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b741d000-b741e000 r-xs 00000000 03:01 313052     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b741e000-b7423000 r-xs 00000000 03:01 313051     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b7423000-b7428000 r-xs 00000000 03:01 313050     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b7428000-b742a000 r-xs 00000000 03:01 313049     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b742a000-b742d000 r-xs 00000000 03:01 313048     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b742d000-b742e000 r-xs 00000000 03:01 313047     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b742e000-b7433000 r-xs 00000000 03:01 313045     /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b7433000-b7434000 r-xs 00000000 03:01 313043     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b7434000-b7438000 r-xs 00000000 03:01 312997     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b7438000-b743e000 r-xs 00000000 03:01 312996     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b743e000-b743f000 r-xs 00000000 03:01 312995     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b743f000-b7447000 r-xs 00000000 03:01 312994     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b7447000-b744b000 r-xs 00000000 03:01 312992     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b744b000-b744f000 r-xs 00000000 03:01 312991     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b744f000-b745b000 r-xp 00000000 03:01 759915     /usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so
b745b000-b745c000 rwxp 0000b000 03:01 759915     /usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so
b745c000-b7465000 r-xp 00000000 03:01 986644     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7465000-b7467000 rwxp 00008000 03:01 986644     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7467000-b746f000 r-xp 00000000 03:01 986646     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b746f000-b7471000 rwxp 00007000 03:01 986646     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7471000-b7485000 r-xp 00000000 03:01 986641     /lib/tls/i686/cmov/libnsl-2.6.1.so
b7485000-b7487000 rwxp 00013000 03:01 986641     /lib/tls/i686/cmov/libnsl-2.6.1.so
b7487000-b7489000 rwxp b7487000 00:00 0 
b7489000-b7490000 r-xp 00000000 03:01 986642     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7490000-b7492000 rwxp 00006000 03:01 986642     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7493000-b7494000 r-xp 00000000 03:01 714220     /usr/lib/libgcroots.so.0.0.0
b7494000-b7495000 rwxp 00000000 03:01 714220     /usr/lib/libgcroots.so.0.0.0
b7495000-b749a000 r-xs 00000000 03:01 312941     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b749a000-b749c000 r-xp 00000000 03:01 727672     /usr/lib/gconv/ISO8859-15.so
b749c000-b749e000 rwxp 00001000 03:01 727672     /usr/lib/gconv/ISO8859-15.so
b74a1000-b74e0000 r-xp 00000000 03:01 760439     /usr/lib/locale/en_US.utf8/LC_CTYPE
b74e0000-b74e1000 r-xp 00000000 03:01 760444     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b74e1000-b74e2000 r-xp 00000000 03:01 760447     /usr/lib/locale/en_US.utf8/LC_TIME
b74e2000-b75c2000 r-xp 00000000 03:01 760438     /usr/lib/locale/en_US.utf8/LC_COLLATE
b75c2000-b75c5000 rwxp b75c2000 00:00 0 
b75c5000-b75cc000 r-xp 00000000 03:01 986651     /lib/tls/i686/cmov/librt-2.6.1.so
b75cc000-b75ce000 rwxp 00006000 03:01 986651     /lib/tls/i686/cmov/librt-2.6.1.so
b75ce000-b75d2000 r-xp 00000000 03:01 712371     /usr/lib/libXdmcp.so.6.0.0
b75d2000-b75d3000 rwxp 00003000 03:01 712371     /usr/lib/libXdmcp.so.6.0.0
b75d3000-b75f5000 r-xp 00000000 03:01 711143     /usr/lib/libpng12.so.0.15.0
b75f5000-b75f6000 rwxp 00021000 03:01 711143     /usr/lib/libpng12.so.0.15.0
b75f6000-b75f8000 r-xp 00000000 03:01 712360     /usr/lib/libXau.so.6.0.0
b75f8000-b75f9000 rwxp 00001000 03:01 712360     /usr/lib/libXau.so.6.0.0
b75f9000-b7617000 r-xp 00000000 03:01 712562     /usr/lib/libexpat.so.1.0.0
b7617000-b7619000 rwxp 0001e000 03:01 712562     /usr/lib/libexpat.so.1.0.0
b7619000-b761a000 rwxp b7619000 00:00 0 
b761a000-b762e000 r-xp 00000000 03:01 713138     /usr/lib/libz.so.1.2.3.3
b762e000-b762f000 rwxp 00013000 03:01 713138     /usr/lib/libz.so.1.2.3.3
b762f000-b769b000 r-xp 00000000 03:01 712576     /usr/lib/libfreetype.so.6.3.16
b769b000-b769f000 rwxp 0006b000 03:01 712576     /usr/lib/libfreetype.so.6.3.16
b769f000-b76cc000 r-xp 00000000 03:01 711161     /usr/lib/libpangoft2-1.0.so.0.1800.3
b76cc000-b76cd000 rwxp 0002c000 03:01 711161     /usr/lib/libpangoft2-1.0.so.0.1800.3
b76cd000-b76cf000 r-xp 00000000 03:01 712369     /usr/lib/libXdamage.so.1.1.0
b76cf000-b76d0000 rwxp 00001000 03:01 712369     /usr/lib/libXdamage.so.1.1.0
b76d0000-b76d2000 r-xp 00000000 03:01 712365     /usr/lib/libXcomposite.so.1.0.0
b76d2000-b76d3000 rwxp 00001000 03:01 712365     /usr/lib/libXcomposite.so.1.0.0
b76d3000-b76d4000 rwxp b76d3000 00:00 0 
b76d4000-b76e8000 r-xp 00000000 03:01 986649     /lib/tls/i686/cmov/libpthread-2.6.1.so
b76e8000-b76ea000 rwxp 00013000 03:01 986649     /lib/tls/i686/cmov/libpthread-2.6.1.so
b76ea000-b76ec000 rwxp b76ea000 00:00 0 
b76ec000-b7830000 r-xp 00000000 03:01 986635     /lib/tls/i686/cmov/libc-2.6.1.so
b7830000-b7831000 r-xp 00143000 03:01 986635     /lib/tls/i686/cmov/libc-2.6.1.so
b7831000-b7833000 rwxp 00144000 03:01 986635     /lib/tls/i686/cmov/libc-2.6.1.so
b7833000-b7836000 rwxp b7833000 00:00 0 
b7836000-b783a000 r-xp 00000000 03:01 712766     /usr/lib/libgthread-2.0.so.0.1400.1
b783a000-b783b000 rwxp 00003000 03:01 712766     /usr/lib/libgthread-2.0.so.0.1400.1
b783b000-b78f7000 r-xp 00000000 03:01 712654     /usr/lib/libglib-2.0.so.0.1400.1
b78f7000-b78f8000 rwxp 000bc000 03:01 712654     /usr/lib/libglib-2.0.so.0.1400.1
b78f8000-b78fa000 r-xp 00000000 03:01 986638     /lib/tls/i686/cmov/libdl-2.6.1.so
b78fa000-b78fc000 rwxp 00001000 03:01 986638     /lib/tls/i686/cmov/libdl-2.6.1.so
b78fc000-b78ff000 r-xp 00000000 03:01 712664     /usr/lib/libgmodule-2.0.so.0.1400.1
b78ff000-b7900000 rwxp 00002000 03:01 712664     /usr/lib/libgmodule-2.0.so.0.1400.1
b7900000-b7901000 rwxp b7900000 00:00 0 
b7901000-b793b000 r-xp 00000000 03:01 712704     /usr/lib/libgobject-2.0.so.0.1400.1
b793b000-b793c000 rwxp 0003a000 03:01 712704     /usr/lib/libgobject-2.0.so.0.1400.1
b793c000-b7a29000 r-xp 00000000 03:01 712354     /usr/lib/libX11.so.6.2.0
b7a29000-b7a2d000 rwxp 000ed000 03:01 712354     /usr/lib/libX11.so.6.2.0
b7a2d000-b7a34000 r-xp 00000000 03:01 712397     /usr/lib/libXrender.so.1.3.0
b7a34000-b7a35000 rwxp 00006000 03:01 712397     /usr/lib/libXrender.so.1.3.0
b7a35000-b7aaa000 r-xp 00000000 03:01 711147     /usr/lib/libcairo.so.2.11.5
b7aaa000-b7aac000 rwxp 00074000 03:01 711147     /usr/lib/libcairo.so.2.11.5
b7aac000-b7ae7000 r-xp 00000000 03:01 711157     /usr/lib/libpango-1.0.so.0.1800.3
b7ae7000-b7ae9000 rwxp 0003b000 03:01 711157     /usr/lib/libpango-1.0.so.0.1800.3
b7ae9000-b7aed000 r-xp 00000000 03:01 712377     /usr/lib/libXfixes.so.3.1.0
b7aed000-b7aee000 rwxp 00003000 03:01 712377     /usr/lib/libXfixes.so.3.1.0
b7aee000-b7aef000 rwxp b7aee000 00:00 0 
b7aef000-b7af7000 r-xp 00000000 03:01 712367     /usr/lib/libXcursor.so.1.0.2
b7af7000-b7af8000 rwxp 00007000 03:01 712367     /usr/lib/libXcursor.so.1.0.2
b7af8000-b7b05000 r-xp 00000000 03:01 712375     /usr/lib/libXext.so.6.4.0
b7b05000-b7b06000 rwxp 0000d000 03:01 712375     /usr/lib/libXext.so.6.4.0
b7b06000-b7b0b000 r-xp 00000000 03:01 712395     /usr/lib/libXrandr.so.2.1.0
b7b0b000-b7b0c000 rwxp 00005000 03:01 712395     /usr/lib/libXrandr.so.2.1.0
b7b0c000-b7b13000 r-xp 00000000 03:01 712383     /usr/lib/libXi.so.6.0.0
b7b13000-b7b14000 rwxp 00006000 03:01 712383     /usr/lib/libXi.so.6.0.0
b7b14000-b7b16000 r-xp 00000000 03:01 712385     /usr/lib/libXinerama.so.1.0.0
b7b16000-b7b17000 rwxp 00001000 03:01 712385     /usr/lib/libXinerama.so.1.0.0
b7b17000-b7b3a000 r-xp 00000000 03:01 712568     /usr/lib/libfontconfig.so.1.2.0
b7b3a000-b7b42000 rwxp 00023000 03:01 712568     /usr/lib/libfontconfig.so.1.2.0
b7b42000-b7b43000 rwxp b7b42000 00:00 0 
b7b43000-b7b4b000 r-xp 00000000 03:01 711159     /usr/lib/libpangocairo-1.0.so.0.1800.3
b7b4b000-b7b4c000 rwxp 00007000 03:01 711159     /usr/lib/libpangocairo-1.0.so.0.1800.3
b7b4c000-b7b6f000 r-xp 00000000 03:01 986639     /lib/tls/i686/cmov/libm-2.6.1.so
b7b6f000-b7b71000 rwxp 00023000 03:01 986639     /lib/tls/i686/cmov/libm-2.6.1.so
b7b71000-b7b88000 r-xp 00000000 03:01 712616     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b7b88000-b7b89000 rwxp 00016000 03:01 712616     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b7b89000-b7ba2000 r-xp 00000000 03:01 712433     /usr/lib/libatk-1.0.so.0.2009.1
b7ba2000-b7ba4000 rwxp 00018000 03:01 712433     /usr/lib/libatk-1.0.so.0.2009.1
b7ba4000-b7c28000 r-xp 00000000 03:01 712614     /usr/lib/libgdk-x11-2.0.so.0.1200.0
b7c28000-b7c2b000 rwxp 00084000 03:01 712614     /usr/lib/libgdk-x11-2.0.so.0.1200.0
b7c2b000-b7fa8000 r-xp 00000000 03:01 712769     /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7fa8000-b7faf000 rwxp 0037c000 03:01 712769     /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7faf000-b7fb1000 rwxp b7faf000 00:00 0 
b7fb1000-b7fb2000 r-xp 00000000 03:01 760442     /usr/lib/locale/en_US.utf8/LC_MONETARY
b7fb2000-b7fb3000 r-xp 00000000 03:01 775695     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fb3000-b7fb4000 r-xp 00000000 03:01 760445     /usr/lib/locale/en_US.utf8/LC_PAPER
b7fb4000-b7fb5000 r-xp 00000000 03:01 760443     /usr/lib/locale/en_US.utf8/LC_NAME
b7fb5000-b7fb6000 r-xp 00000000 03:01 760437     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fb6000-b7fb7000 r-xp 00000000 03:01 760446     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7fb7000-b7fb8000 r-xp 00000000 03:01 760441     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7fb8000-b7fbf000 r-xs 00000000 03:01 646401     /usr/lib/gconv/gconv-modules.cache
b7fbf000-b7fc0000 r-xp 00000000 03:01 760440     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fc0000-b7fc1000 rwxp b7fc0000 00:00 0 
b7fc1000-b7fdb000 r-xp 00000000 03:01 953453     /lib/ld-2.6.1.so
b7fdb000-b7fdd000 rwxp 00019000 03:01 953453     /lib/ld-2.6.1.so
bfc23000-bfc39000 rwxp bfc23000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
jmap82@JMAP1:~/Desktop/gHamachi_gtk2$ 
```

And then I got scared and ran to the only place I could think of where milk flows like honey and the women flock like the salmon of Capistrano... I'm talking about a little place called "ubuntuforums.org"

So here I am wondering if there is a way that I can get all the Hamachi stuff off my computer so I can go break it again with something else.

---

### Post by glennric on 2008-03-09
The typical way to uninstall software installed with "make install" is "make uninstall".  However, not all source code is properly designed.  It depends on if the Makefile has the uninstall method in it or not.  If it does that will work.  Otherwise it can be more difficult to uninstall.  Try it and hope it works.

---

### Post by szymon_g on 2008-03-09
you can always install software (if you have to install it from sources) using checkinstall - it will create a debian (or red hat, or slackware) package from source- so you will be able to uninstall it via apt-get/aptitude

---

### Post by jmap82 on 2008-03-09
Wow!  That was quick!  Thanks!

Here's what I tried:

For the original Hamachi "uninstall":

```
 jmap82@JMAP1:~$ cd Desktop
jmap82@JMAP1:~/Desktop$ cd hamachi-0.9.9.9-20-lnx
jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ dir
CHANGES  LICENSE          LICENSE.openssl  Makefile  tuncfg
hamachi  LICENSE.openssh  LICENSE.tuncfg   README
jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ make unMakefile
make: *** No rule to make target `unMakefile'.  Stop.
jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ 
```


And for the gHamachi "uninstall":
```

 jmap82@JMAP1:~/Desktop/gHamachi_gtk2$ dir
ghamachi  README
jmap82@JMAP1:~/Desktop/gHamachi_gtk2$ make unghamachi
make: *** No rule to make target `unghamachi'.  Stop.
jmap82@JMAP1:~/Desktop/gHamachi_gtk2$ 
```


With that in mind, what are my other options?

---

### Post by glennric on 2008-03-09
Did you try what I said before.  For both literally type
```
sudo make uninstall
```

---

### Post by jmap82 on 2008-03-09
> **szymon_g said:**
> you can always install software (if you have to install it from sources) using checkinstall - it will create a debian (or red hat, or slackware) package from source- so you will be able to uninstall it via apt-get/aptitude

That sounds great! And exactly like what I will want to do from now on. Could you elaborate on the "checkinstall" command for me so I know how to use it in the future?

---

### Post by glennric on 2008-03-09
For checkinstall, all you have to do is instead of using
```
./configure
make
make install
```
to install the software type
```
./configure
make
checkinstall
```
Then follow the prompts.

---

### Post by jmap82 on 2008-03-09
> **glennric said:**
> Did you try what I said before.  For both literally type
```
sudo make uninstall
```

Oh, sorry, I guess I'm not very good at following directions, I was trying to be intuitive and apparently I missed the point...

Unfortunately that didn't seem to work either, but thank you!  

Here's what I did:

```

jmap82@JMAP1:~/Desktop/gHamachi_gtk2$ make uninstall
make: *** No rule to make target `uninstall'.  Stop.
jmap82@JMAP1:~/Desktop/gHamachi_gtk2$ 

```

```

jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ make uninstall
make: *** No rule to make target `uninstall'.  Stop.
jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ 

```

---

### Post by jmap82 on 2008-03-09
> **glennric said:**
> For checkinstall, all you have to do is instead of using
```
./configure
make
make install
```
to install the software type
```
./configure
make
checkinstall
```
Then follow the prompts.

Sorry to be so dense... but what is "./configure"?  I really appreciate all the help!

---

### Post by glennric on 2008-03-09
Unfortunately the Makefiles for hamachi are not well designed then.  That makes it rather difficult to uninstall.  You will have to figure out exactly what it installed and delete it all.  You might also be able to install with checkinstall and then remove it that way.  When checkinstall installs, it should overwrite the original installation and keep track of everything it installs.

---

### Post by glennric on 2008-03-09
By the way "./configure" runs the configure script in the source directory.  This sets a bunch of variables that are specific to your system.  Basically it tries to guess all the correct places to install everything and find the libraries that it needs to compile.

---

### Post by jmap82 on 2008-03-09
> **glennric said:**
> Unfortunately the Makefiles for hamachi are not well designed then.  That makes it rather difficult to uninstall.  You will have to figure out exactly what it installed and delete it all.  You might also be able to install with checkinstall and then remove it that way.  When checkinstall installs, it should overwrite the original installation and keep track of everything it installs.

OK!  I like that idea :)

I hate do be a baby, but can you spoon feed me the checkinstall code?

---

### Post by glennric on 2008-03-09
I am not sure what you mean by the checkinstall code?  Do you mean tell you how to follow the prompts?

---

### Post by jmap82 on 2008-03-09
> **glennric said:**
> By the way "./configure" runs the configure script in the source directory.  This sets a bunch of variables that are specific to your system.  Basically it tries to guess all the correct places to install everything and find the libraries that it needs to compile.

Oh.  Since I never ran that before, thats probably why my installs didn't work so well, huh?

This has been a very informative thread for me.  Thank you!

---

### Post by glennric on 2008-03-09
Yeah, if you didn't run the configure script it won't install right.  I would be surprised if it installed at all.  It most likely would have ended with an error before it actually installed anything.  By the way I did a google search and found this
[http://ubuntuforums.org/showthread.php?t=135036]("http://ubuntuforums.org/showthread.php?t=135036")
That link is a little old, but may still work.  You should search the forums and see if you can find any other more recent info.  Particularly look in the Tips and Tricks section of the forum.

---

### Post by jmap82 on 2008-03-09
> **glennric said:**
> I am not sure what you mean by the checkinstall code?  Do you mean tell you how to follow the prompts?

I guess I'm just a bit insecure in the terminal, so I wanted to make sure I input everything correctly.  This is what I would do at this point:

```

#inside the appropriate folder of course
./configure #then press enter
make MakeFile #then press enter
checkinstall #then press enter

```

Will that work?

---

### Post by glennric on 2008-03-09
Yes, except it is just
```
./configure #press enter
make #press enter (don't add anything about a makefile unless the software has a nonstandard name for its makefile
checkinstall #press enter
```

---

### Post by jmap82 on 2008-03-09
> **glennric said:**
> Yeah, if you didn't run the configure script it won't install right.  I would be surprised if it installed at all.  It most likely would have ended with an error before it actually installed anything.  By the way I did a google search and found this
[http://ubuntuforums.org/showthread.php?t=135036]("http://ubuntuforums.org/showthread.php?t=135036")
That link is a little old, but may still work.  You should search the forums and see if you can find any other more recent info.  Particularly look in the Tips and Tricks section of the forum.

Haha, thats funny, because that was actually the thread I was looking at when I got side tracked by gHamachi.  I got an error at like step two, and so I tried something else, which I admittedly shouldn't have done.  But even in that how-to doesn't mention ./configure or checkinstall.  I wish it had, I'm sure what I'm learning now will save me a lot of flack later on.

Thanks again!

---

### Post by jmap82 on 2008-03-09
> **glennric said:**
> Yes, except it is just
```
./configure #press enter
make #press enter (don't add anything about a makefile unless the software has a nonstandard name for its makefile
checkinstall #press enter
```

Sorry, I feel so lame.  I can't even get past step one :(

```

jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ ./configure
bash: ./configure: No such file or directory
jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ 

```

---

### Post by glennric on 2008-03-09
That tutorial is actually to setup Hamachi with VNC.  It has a link to a page to install Hamachi.  It is
[http://forums.hamachi.cc/viewtopic.php?t=3523]("http://forums.hamachi.cc/viewtopic.php?t=3523")
Although, you probably saw that.  I notice that it doesn't say anything about a configure script either.  It is possible that there isn't one.  Not all software needs that step.  

I should note at this point that what you are trying to do is a rather advanced procedure.  If you have not experience compiling and installing software you may want to stop now.  Although, I won't discourage you from proceeding and learning.  Just expect that many things won't go as planned, and there will be much to figure out.  You may need to do some research.  Search the forums and google.  In other words, I think this is something that does not belong in the "Absolute Beginner Talk" section of the forums.

---

### Post by glennric on 2008-03-09
Looking at the source code for Hamachi, I see that there is no configure script.  All you should need to do to install it is 
"sudo checkinstall"
I probably forgot to tell you to add sudo to the beginning before, but you will need to have root access to install it.

---

### Post by jmap82 on 2008-03-09
> **glennric said:**
> That tutorial is actually to setup Hamachi with VNC.  It has a link to a page to install Hamachi.  It is
[http://forums.hamachi.cc/viewtopic.php?t=3523]("http://forums.hamachi.cc/viewtopic.php?t=3523")
Although, you probably saw that.  I notice that it doesn't say anything about a configure script either.  It is possible that there isn't one.  Not all software needs that step.  

I should note at this point that what you are trying to do is a rather advanced procedure.  If you have not experience compiling and installing software you may want to stop now.  Although, I won't discourage you from proceeding and learning.  Just expect that many things won't go as planned, and there will be much to figure out.  You may need to do some research.  Search the forums and google.  In other words, I think this is something that does not belong in the "Absolute Beginner Talk" section of the forums.

Cool, I agree.  I should probably call it quits for now until I start to feel a bit more comfortable at the terminal (and its 1am in Japan right now, so rest wouldn't hurt either)

Thanks again for all your help!  I really appreciate it!

---

### Post by szymon_g on 2008-03-09
> **jmap82 said:**
> 
```

#inside the appropriate folder of course
./configure #then press enter
make MakeFile #then press enter
checkinstall #then press enter

```

Will that work?

sudo ./configure
sudo make
sudo checkinstall -d

than answer some simple meta-questions (like: name of contributor, email etc).


//////////
ah, i forgot: i dont remember that it will install package automaticly or only makes .deb
in this second case, you can install it by

sudo dpkg -i name_of_package.deb

---

### Post by jmap82 on 2008-03-09
> **glennric said:**
> Looking at the source code for Hamachi, I see that there is no configure script.  All you should need to do to install it is 
"sudo checkinstall"
I probably forgot to tell you to add sudo to the beginning before, but you will need to have root access to install it.

Hmmm, like this?

```

jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ sudo checkinstall
[sudo] password for jmap82:
sudo: checkinstall: command not found

```

What am I missing?

---

### Post by glennric on 2008-03-09
> **szymon_g said:**
> sudo ./configure
sudo make
sudo checkinstall -d

than answer some simple meta-questions (like: name of contributor, email etc).


//////////
ah, i forgot: i dont remember that it will install package automaticly or only makes .deb
in this second case, you can install it by

sudo dpkg -i name_of_package.deb

You don't need sudo to run the configure script, or to make the software.  You only need it for the install step.  Also, in this case there is no configure script and the binary is precompiled.  It is not truly a source package.  So all that is needed is the "sudo make install" or better "sudo checkinstall" step.  You should look back at the rest of the thread before trying to jump in and help with redundant information.

---

### Post by jmap82 on 2008-03-09
> **szymon_g said:**
> sudo ./configure
sudo make
sudo checkinstall -d

than answer some simple meta-questions (like: name of contributor, email etc).


//////////
ah, i forgot: i dont remember that it will install package automaticly or only makes .deb
in this second case, you can install it by

sudo dpkg -i name_of_package.deb

oh "-d"... I hadn't heard that one yet.  Let me give it a whirl.

---

### Post by jmap82 on 2008-03-09
Hmmm, well it did something, but the checkinstall still didn't work.

```

jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ sudo ./configure
sudo: ./configure: command not found
jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ sudo make

Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Compiling tuncfg ..
Copying tuncfg into /sbin ..

Hamachi is installed. See README for what to do next.
jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ sudo checkinstall -d
sudo: checkinstall: command not found

```

---

### Post by szymon_g on 2008-03-09
> **glennric said:**
> You don't need sudo to run the configure script, or to make the software.  You only need it for the install step.  Also, in this case there is no configure script and the binary is precompiled.  It is not truly a source package.  So all that is needed is the "sudo make install" or better "sudo checkinstall" step.  You should look back at the rest of the thread before trying to jump in and help with redundant information.

mea culpa

---

### Post by glennric on 2008-03-09
Seriously jmap82, ignore what szymon_g said.  His post is largely improper.  The "-d" flag to checkinstall is to set the debug level and by itself will not work.  It also requires a number (0,1, or 2) after it.  I think what he meant is "-D", which tells checkinstall to create a deb.  However, that is the default for checkinstall in Ubuntu anyway.

---

### Post by szymon_g on 2008-03-09
> **jmap82 said:**
> Hmmm, well it did something, but the checkinstall still didn't work.

```

jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ sudo ./configure
sudo: ./configure: command not found
jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ sudo make

Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Compiling tuncfg ..
Copying tuncfg into /sbin ..

Hamachi is installed. See README for what to do next.
jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ sudo checkinstall -d
sudo: checkinstall: command not found

```

hm... did you installed checkinstall :?

sudo aptitude install checkinstall 

xD

---

### Post by jmap82 on 2008-03-09
> **szymon_g said:**
> hm... did you installed checkinstall :?

sudo aptitude install checkinstall 

xD

Haha!  Now that you mention it, I'm 99% sure that is my problem!  Boy, what a night!

Thank you!

---

### Post by jmap82 on 2008-03-09
While I'm quite sure that this has grown into a completely different monster, I'm really excited to be learning all this new stuff.

No, I didn't have checkinstall installed, so installing it cleared up that.

Here's what I did for the checkinstall, but it came back with an error:

```

jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> Installs Hamachi-0.9.9.9-20-lnx EOF
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@JMAP1 ]
1 -  Summary: [ Installs Hamachi-0.9.9.9-20-lnx EOF ]
2 -  Name:    [ hamachi-0.9.9.9-20 ]
3 -  Version: [ lnx ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ hamachi-0.9.9.9-20-lnx ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 1
Enter new summary: 
>> Installs Hamachi-0.9.9.9-20-lnx

This package will be built according to these values: 

0 -  Maintainer: [ root@JMAP1 ]
1 -  Summary: [ Installs Hamachi-0.9.9.9-20-lnx ]
2 -  Name:    [ hamachi-0.9.9.9-20 ]
3 -  Version: [ lnx ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ hamachi-0.9.9.9-20-lnx ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================

Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Compiling tuncfg ..
Copying tuncfg into /sbin ..

Hamachi is installed. See README for what to do next.

======================== Installation successful ==========================

Copying documentation directory...
./
./CHANGES
./LICENSE
./README
grep: /var/tmp/MEPgQHXhgCjXDrTrjXikV/newfile: No such file or directory

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]: y

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK

jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ 

```

And the log showed me this:

```


dpkg-deb - error: (upstream) version (`lnx') doesn't contain any digits
dpkg-deb: 1 errors in control file


```

---

### Post by jmap82 on 2008-03-09
Yay!  I did it!

```

jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@JMAP1 ]
1 -  Summary: [ Installs Hamachi-0.9.9.9-20-lnx EOF ]
2 -  Name:    [ hamachi-0.9.9.9-20 ]
3 -  Version: [ lnx ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ hamachi-0.9.9.9-20-lnx ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 1
Enter new summary: 
>> Installs Hamachi-0.9.9.9-20-lnx

This package will be built according to these values: 

0 -  Maintainer: [ root@JMAP1 ]
1 -  Summary: [ Installs Hamachi-0.9.9.9-20-lnx ]
2 -  Name:    [ hamachi-0.9.9.9-20 ]
3 -  Version: [ lnx ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ hamachi-0.9.9.9-20-lnx ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 2
Enter new name: 
>> Hamachi

*** Warning: The package name "Hamachi" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values: 

0 -  Maintainer: [ root@JMAP1 ]
1 -  Summary: [ Installs Hamachi-0.9.9.9-20-lnx ]
2 -  Name:    [ hamachi ]
3 -  Version: [ lnx ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ hamachi-0.9.9.9-20-lnx ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 3
Enter new version: 
>> 0.9.9.9-20

This package will be built according to these values: 

0 -  Maintainer: [ root@JMAP1 ]
1 -  Summary: [ Installs Hamachi-0.9.9.9-20-lnx ]
2 -  Name:    [ hamachi ]
3 -  Version: [ 0.9.9.9-20 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ hamachi-0.9.9.9-20-lnx ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================

Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Compiling tuncfg ..
Copying tuncfg into /sbin ..

Hamachi is installed. See README for what to do next.

======================== Installation successful ==========================

Copying documentation directory...
./
./CHANGES
./LICENSE
./README
grep: /var/tmp/VkHoIRSqWbTkJIaNjFrOC/newfile: No such file or directory

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/jmap82/Desktop/hamachi-0.9.9.9-20-lnx/hamachi_0.9.9.9-20-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r hamachi

**********************************************************************

jmap82@JMAP1:~/Desktop/hamachi-0.9.9.9-20-lnx$ 

```

So now I can uninstall it, right?

---

### Post by jmap82 on 2008-03-09
Well it worked for the original Hamachi, but since there isn't a Makefile with gHamachi, it didn't work with that.  Oh, well.

Thanks again for your help!  I'll be more careful next time :)

---

### Post by glennric on 2008-03-09
Congratulations. You can uninstall it with
```
sudo apt-get remove hamachi
```
As to gHamachi, there is a good change that will have a configure script.  I would have to look at the source, the link to the Howto in the forums should have something about that though.  The configure script creates the Makefile.

---

### Post by unutbu on 2008-03-09
> 
jmap82@JMAP1:~/Desktop$ cd gHamachi_gtk2
jmap82@JMAP1:~/Desktop/gHamachi_gtk2$ make ghamachi
make: Nothing to be done for `ghamachi'.
jmap82@JMAP1:~/Desktop/gHamachi_gtk2$ dir
ghamachi  README


It looks to me like nothing really has been installed. To get rid of ghamachi, just
```

/bin/rm -rf ~/Desktop/gHamachi_gtk2

```

---

### Post by glennric on 2008-03-09
There is no configure script or Makefile for gHamachi.  Follow the directions on 
[http://ubuntuforums.org/showthread.php?t=135036]("http://ubuntuforums.org/showthread.php?t=135036")
to install it.  You won't need "make install" or "checkinstall".

---

