---
title: "[SOLVED] Obconf Error"
date: 2008-06-24
forum: Arch and derivatives
---

### Post by Dr Small on 2008-06-24
I tried to open a theme archive that was a .bz2 archive format (knowing little about openbox) and it spit out an error and crashed obconf. Now Openbox is crashing at random times, and obconf won't open. Here is the weird error I am getting when opening obconf:
```
[drsmall@darkghost ~]$ obconf

(obconf:20761): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed

(obconf:20761): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(obconf:20761): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(obconf:20761): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed

(obconf:20761): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(obconf:20761): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed
*** glibc detected *** obconf: malloc(): memory corruption: 0x08241270 ***
======= Backtrace: =========
/lib/libc.so.6[0xb7500a44]
/lib/libc.so.6[0xb7503110]
/lib/libc.so.6(__libc_malloc+0x9c)[0xb7504bfc]
/usr/lib/libglib-2.0.so.0(g_malloc+0x34)[0xb7adf1f4]
/usr/lib/libobrender.so.21[0xb7f24a94]
/usr/lib/libobrender.so.21(RrPaintPixmap+0x2bf)[0xb7f24e0f]
obconf[0x805236e]
obconf[0x80526b7]
obconf(preview_theme+0x878)[0x8053498]
obconf[0x8053851]
/usr/lib/libglib-2.0.so.0[0xb7ad5081]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb7ad6f88]
/usr/lib/libglib-2.0.so.0[0xb7ada4eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb7ada9ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7861e59]
obconf(main+0x609)[0x80516f9]
/lib/libc.so.6(__libc_start_main+0xe5)[0xb74ab5c5]
obconf[0x804d471]
======= Memory map: ========
08048000-08056000 r-xp 00000000 08:03 391018     /usr/bin/obconf
08056000-08057000 rwxp 0000e000 08:03 391018     /usr/bin/obconf
08057000-08401000 rwxp 08057000 00:00 0          [heap]
b7100000-b7121000 rwxp b7100000 00:00 0 
b7121000-b7200000 ---p b7121000 00:00 0 
b7241000-b724d000 r-xp 00000000 08:03 880457     /usr/lib/libgcc_s.so.1
b724d000-b724e000 rwxp 0000b000 08:03 880457     /usr/lib/libgcc_s.so.1
b725e000-b728e000 rwxs 00000000 00:08 1410138115  /SYSV00000000 (deleted)
b728e000-b729f000 r-xp 00000000 08:03 32654      /usr/share/fonts/TTF/Vera.ttf
b729f000-b72b0000 r-xp 00000000 08:03 32654      /usr/share/fonts/TTF/Vera.ttf
b72b0000-b72b2000 r-xp 00000000 08:03 362857     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b72b2000-b72b3000 rwxp 00001000 08:03 362857     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b72b3000-b72c3000 r-xs 00000000 08:03 163326     /var/cache/fontconfig/8d4af663993b81a124ee82e610bb31f9-x86.cache-2
b72c3000-b72c9000 r-xs 00000000 08:03 163004     /var/cache/fontconfig/d62e99ef547d1d24cdb1bd22ec1a2976-x86.cache-2
b72c9000-b72e4000 r-xs 00000000 08:03 163323     /var/cache/fontconfig/f6b893a7224233d96cb72fd88691c0b4-x86.cache-2
b72e4000-b732a000 r-xs 00000000 08:03 163322     /var/cache/fontconfig/17090aa38d5c6f09fb8c5c354938f1d7-x86.cache-2
b732a000-b7370000 r-xs 00000000 08:03 163320     /var/cache/fontconfig/df311e82a1a24c41a75c2c930223552e-x86.cache-2
b7370000-b7379000 r-xp 00000000 08:03 765578     /lib/libnss_files-2.8.so
b7379000-b737b000 rwxp 00008000 08:03 765578     /lib/libnss_files-2.8.so
b737b000-b737d000 rwxp b737b000 00:00 0 
b737d000-b7381000 r-xp 00000000 08:03 889189     /usr/lib/libXdmcp.so.6.0.0
b7381000-b7382000 rwxp 00003000 08:03 889189     /usr/lib/libXdmcp.so.6.0.0
b7382000-b7384000 r-xp 00000000 08:03 889187     /usr/lib/libXau.so.6.0.0
b7384000-b7385000 rwxp 00001000 08:03 889187     /usr/lib/libXau.so.6.0.0
b7385000-b7386000 rwxp b7385000 00:00 0 
b7386000-b73ae000 r-xp 00000000 08:03 889970     /usr/lib/libpixman-1.so.0.10.0
b73ae000-b73af000 rwxp 00028000 08:03 889970     /usr/lib/libpixman-1.so.0.10.0
b73af000-b73b7000 r-xp 00000000 08:03 890043     /usr/lib/libXcursor.so.1.0.2
b73b7000-b73b8000 rwxp 00007000 08:03 890043     /usr/lib/libXcursor.so.1.0.2
b73b8000-b73bd000 r-xp 00000000 08:03 889804     /usr/lib/libXrandr.so.2.1.0
b73bd000-b73be000 rwxp 00005000 08:03 889804     /usr/lib/libXrandr.so.2.1.0
b73be000-b73c5000 r-xp 00000000 08:03 889780     /usr/lib/libXi.so.6.0.0
b73c5000-b73c6000 rwxp 00006000 08:03 889780     /usr/lib/libXi.so.6.0.0
b73c6000-b73c7000 rwxp b73c6000 00:00 0 
b73c7000-b73c9000 r-xp 00000000 08:03 889904     /usr/lib/libXinerama.so.1.0.0
b73c9000-b73ca000 rwxp 00001000 08:03 889904     /usr/lib/libXinerama.so.1.0.0
b73ca000-b73d7000 r-xp 00000000 08:03 889291     /usr/lib/libXext.so.6.4.0
b73d7000-b73d8000 rwxp 0000c000 08:03 889291     /usr/lib/libXext.so.6.4.0
b73d8000-b73fe000 r-xp 00000000 08:03 890049     /usr/lib/libpng12.so.0.28.0
b73fe000-b73ff000 rwxp 00025000 08:03 890049     /usr/lib/libpng12.so.0.28.0
b73ff000-b7403000 r-xp 00000000 08:03 889972     /usr/lib/libXfixes.so.3.1.0
b7403000-b7404000 rwxp 00003000 08:03 889972     /usr/lib/libXfixes.so.3.1.0
b7404000-b7406000 r-xp 00000000 08:03 889977     /usr/lib/libXdamage.so.1.1.0
b7406000-b7407000 rwxp 00001000 08:03 889977     /usr/lib/libXdamage.so.1.1.0
b7407000-b7408000 rwxp b7407000 00:00 0 
b7408000-b740a000 r-xp 00000000 08:03 890502     /usr/lib/libXcomposite.so.1.0.0
b740a000-b740b000 rwxp 00001000 08:03 890502     /usr/lib/libXcomposite.so.1.0.0
b740b000-b7433000 r-xp 00000000 08:03 765677     /lib/libpcre.so.0.0.1
b7433000-b7434000 rwxp 00027000 08:03 765677     /lib/libpcre.so.0.0.1
b7434000-b744b000 r-xp 00000000 08:03 889280     /usr/lib/libxcb.so.1.0.0
b744b000-b744c000 rwxp 00016000 08:03 889280     /usr/lib/libxcb.so.1.0.0
b744c000-b744d000 r-xp 00000000 08:03 889230     /usr/lib/libxcb-xlib.so.0.0.0
b744d000-b744e000 rwxp 00000000 08:03 889230     /usr/lib/libxcb-xlib.so.0.0.0
b744e000-b746c000 r-xp 00000000 08:03 888986     /usr/lib/libexpat.so.1.5.2
b746c000-b746e000 rwxp 0001e000 08:03 888986     /usr/lib/libexpat.so.1.5.2
b746e000-b746f000 rwxp b746e000 00:00 0 
b746f000-b7493000 r-xp 00000000 08:03 765575     /lib/libm-2.8.so
b7493000-b7495000 rwxp 00023000 08:03 765575     /lib/libm-2.8.so
b7495000-b75d1000 r-xp 00000000 08:03 765576     /lib/libc-2.8.so
b75d1000-b75d2000 r-xp 0013c000 08:03 765576     /lib/libc-2.8.so
b75d2000-b75d4000 rwxp 0013d000 08:03 765576     /lib/libc-2.8.so
b75d4000-b75d7000 rwxp b75d4000 00:00 0 
b75d7000-b75ee000 r-xp 00000000 08:03 890679     /usr/lib/libglade-2.0.so.0.0.7
b75ee000-b75ef000 rwxp 00016000 08:03 890679     /usr/lib/libglade-2.0.so.0.0.7
b75ef000-b7650000 r-xp 00000000 08:03 890419     /usr/lib/libcairo.so.2.17.5
b7650000-b7652000 rwxp 00061000 08:03 890419     /usr/lib/libcairo.so.2.17.5
b7652000-b765a000 r-xp 00000000 08:03 553965     /usr/lib/libpangocairo-1.0.so.0.2002.1
b765a000-b765b000 rwxp 00008000 08:03 553965     /usr/lib/libpangocairo-1.0.so.0.2002.1
b765b000-b765c000 rwxp b765b000 00:00 0 
b765c000-b7675000 r-xp 00000000 08:03 890585     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.10
b7675000-b7676000 rwxp 00019000 08:03 890585     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.10
b7676000-b768e000 r-xp 00000000 08:03 890418     /usr/lib/libatk-1.0.so.0.2209.1
b768e000-b7690000 rwxp 00018000 08:03 890418     /usr/lib/libatk-1.0.so.0.2209.1
b7690000-b7713000 r-xp 00000000 08:03 890582     /usr/lib/libgdk-x11-2.0.so.0.1200.10
b7713000-b7716000 rwxp 00082000 08:03 890582     /usr/lib/libgdk-x11-2.0.so.0.1200.10
b7716000-b7a8e000 r-xp 00000000 08:03 890581     /usr/lib/libgtk-x11-2.0.so.0.1200.10
b7a8e000-b7a94000 rwxp 00377000 08:03 890581     /usr/lib/libgtk-x11-2.0.so.0.1200.10
b7a94000-b7a95000 rwxp b7a94000 00:00 0 
b7a95000-b7a9c000 r-xp 00000000 08:03 879570     /usr/lib/libstartup-notification-1.so.0.0.0
b7a9c000-b7a9d000 rwxp 00006000 08:03 879570     /usr/lib/libstartup-notification-1.so.0.0.0
b7a9d000-b7a9e000 rwxp b7a9d000 00:00 0 
b7a9e000-b7b51000 r-xp 00000000 08:03 890373     /usr/lib/libglib-2.0.so.0.1600.3
b7b51000-b7b52000 rwxp 000b2000 08:03 890373     /usr/lib/libglib-2.0.so.0.1600.3
b7b52000-b7c84000 r-xp 00000000 08:03 890670     /usr/lib/libxml2.so.2.6.32
b7c84000-b7c89000 rwxp 00131000 08:03 890670     /usr/lib/libxml2.so.2.6.32
b7c89000-b7c8a000 rwxp b7c89000 00:00 0 
b7c8a000-b7c8d000 r-xp 00000000 08:03 553953     /usr/lib/libobparser.so.21.0.2
b7c8d000-b7c8e000 rwxp 00002000 08:03 553953     /usr/lib/libobparser.so.21.0.2
b7c8e000-b7d79000 r-xp 00000000 08:03 889286     /usr/lib/libX11.so.6.2.0
b7d79000-b7d7d000 rwxp 000ea000 08:03 889286     /usr/lib/libX11.so.6.2.0
b7d7d000-b7d8e000 r-xp 00000000 08:03 765673     /lib/libz.so.1.2.3
b7d8e000-b7d8f000 rwxp 00010000 08:03 765673     /lib/libz.so.1.2.3
b7d8f000-b7e06000 r-xp 00000000 08:03 888962     /usr/lib/libfreetype.so.6.3.16
b7e06000-b7e0a000 rwxp 00077000 08:03 888962     /usr/lib/libfreetype.so.6.3.16
b7e0a000-b7e0b000 rwxp b7e0a000 00:00 0 
b7e0b000-b7e33000 r-xp 00000000 08:03 888998     /usr/lib/libfontconfig.so.1.3.0
b7e33000-b7e34000 rwxp 00028000 08:03 888998     /usr/lib/libfontconfig.so.1.3.0
b7e34000-b7e3b000 r-xp 00000000 08:03 889673     /usr/lib/libXrender.so.1.3.0
b7e3b000-b7e3c000 rwxp 00007000 08:03 889673     /usr/lib/libXrender.so.1.3.0
b7e3c000-b7e3e000 r-xp 00000000 08:03 765545     /lib/libdl-2.8.so
b7e3e000-b7e40000 rwxp 00001000 08:03 765545     /lib/libdl-2.8.so
b7e40000-b7e42000 r-xp 00000000 08:03 890374     /usr/lib/libgmodule-2.0.so.0.1600.3
b7e42000-b7e43000 rwxp 00002000 08:03 890374     /usr/lib/libgmodule-2.0.so.0.1600.3
b7e43000-b7e7b000 r-xp 00000000 08:03 890384     /usr/lib/libgobject-2.0.so.0.1600.3
b7e7b000-b7e7c000 rwxp 00038000 08:03 890384     /usr/lib/libgobject-2.0.so.0.1600.3
b7e7c000-b7eb8000 r-xp 00000000 08:03 553961     /usr/lib/libpango-1.0.so.0.2002.1
b7eb8000-b7eba000 rwxp 0003c000 08:03 553961     /usr/lib/libpango-1.0.so.0.2002.1
b7eba000-b7ebb000 rwxp b7eba000 00:00 0 
b7ebb000-b7ecc000 r-xp 00000000 08:03 889938     /usr/lib/libXAborted

```


Yet, if I run this:
```
obconf 2&> out
```

Obconf opens, but it has an error box behind it. I can not click on anything in obconf, but here is what the error says:
```
Unable to extract the file "2".
Please ensure that "/home/drsmall/.themes" is writable and that the file is a valid Openbox theme archive.
The following errors were reported:
tar: 2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: */openbox-3: Not found in archive
tar: Error exit delayed from previous errors
```


Anyone have any suggestions? I have tried reinstalling both openbox and obconf. This problem is just causing X to restart at odd times, now. And I was so beginning to like openbox.. :(

---

### Post by Barrucadu on 2008-06-25
What theme was it? Are you sure it *was* a valid theme? Sometimes I have downloaded a theme only to find the author decided to make it a gzipped tarball inside a bzipped tarball for some reason...

---

### Post by Dr Small on 2008-06-25
Well, it was either Glider or SlickBoxBlue that I tried, as those were the only ones I downloaded, but I did extract both of them in .themes and it was the actual files in it.

It seems to me, that obconf is keeping a setting or something somewhere, as to attempt to keep opening that theme. Now it won't open and is giving me all the errors.

Dr Small

---

### Post by urukrama on 2008-06-25
I just tried both themes, and it seems SlickBoxBlue is the culprit. It pulls my Openbox and X down if I set it as the Openbox theme.

If you select another theme (do so via a console with *nano .config/openbox/rc.xml*) Openbox and Obconf should load fine; you can't use obconf or any text editor in Openbox as that will pull X down again.

Does everything work normally without this theme?

---

### Post by Dr Small on 2008-06-25
Ok. I just changed to the Onyx theme, and openbox isn't crashing anymore. But obconf still won't open, unless I use sudo. But at least openbox isn't crashing.

As long as I understand how to use openbox, I guess obconf isn't needed, but I just thought it would have been nice. But since it works as root, and not as drsmall, I am still led to believe that it is some obconf setting in my home folder that is causing it to crash.

Thanks for the help, urukrama. By the way, nathangrubb pointed me to your Openbox article on your blog last night :D

Dr Small

---

### Post by urukrama on 2008-06-25
It might also mean you have an error in your openbox configuration file (rc.xml), which prevents obconf from loading.

To check this, try temporarily removing your openbox rc.xml file from ~/.config/openbox/ (or rename it to something else, and reconfigure or restart Openbox. If Obconf loads fine, you have an error in your rc.xml file.

Which version of Openbox and Obconf are you using, btw?

---

### Post by Dr Small on 2008-06-25
Just tried renaming rc.xml and it didn't have any effect on it. But I am running obconf 2.0.3-2 and openbox 3.4.7.2-1

---

### Post by urukrama on 2008-06-25
What error message do you get when running Obconf without sudo? 

I suppose it is not the same as what you posted in the first message, since I got that message *only* when I was using the SlickBoxBlue theme.

---

### Post by Dr Small on 2008-06-25
It looks pretty near the same, if you ask me:
```
[drsmall@darkghost ~]$ obconf

(obconf:7526): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed

(obconf:7526): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(obconf:7526): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(obconf:7526): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed

(obconf:7526): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(obconf:7526): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed
*** glibc detected *** obconf: malloc(): memory corruption: 0x08241270 ***
======= Backtrace: =========
/lib/libc.so.6[0xb759da44]
/lib/libc.so.6[0xb75a0110]
/lib/libc.so.6(__libc_malloc+0x9c)[0xb75a1bfc]
/usr/lib/libglib-2.0.so.0(g_malloc+0x34)[0xb7b7c1f4]
/usr/lib/libobrender.so.21[0xb7fc1a94]
/usr/lib/libobrender.so.21(RrPaintPixmap+0x2bf)[0xb7fc1e0f]
obconf[0x805236e]
obconf[0x80526b7]
obconf(preview_theme+0x878)[0x8053498]
obconf[0x8053851]
/usr/lib/libglib-2.0.so.0[0xb7b72081]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb7b73f88]
/usr/lib/libglib-2.0.so.0[0xb7b774eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb7b779ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb78fee59]
obconf(main+0x609)[0x80516f9]
/lib/libc.so.6(__libc_start_main+0xe5)[0xb75485c5]
obconf[0x804d471]
======= Memory map: ========
08048000-08056000 r-xp 00000000 08:03 391018     /usr/bin/obconf
08056000-08057000 rwxp 0000e000 08:03 391018     /usr/bin/obconf
08057000-08401000 rwxp 08057000 00:00 0          [heap]
b7100000-b7121000 rwxp b7100000 00:00 0 
b7121000-b7200000 ---p b7121000 00:00 0 
b72de000-b72ea000 r-xp 00000000 08:03 880457     /usr/lib/libgcc_s.so.1
b72ea000-b72eb000 rwxp 0000b000 08:03 880457     /usr/lib/libgcc_s.so.1
b72fb000-b732b000 rwxs 00000000 00:08 103874563  /SYSV00000000 (deleted)
b732b000-b733c000 r-xp 00000000 08:03 32654      /usr/share/fonts/TTF/Vera.ttf
b733c000-b734d000 r-xp 00000000 08:03 32654      /usr/share/fonts/TTF/Vera.ttf
b734d000-b734f000 r-xp 00000000 08:03 362857     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b734f000-b7350000 rwxp 00001000 08:03 362857     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b7350000-b7360000 r-xs 00000000 08:03 163326     /var/cache/fontconfig/8d4af663993b81a124ee82e610bb31f9-x86.cache-2
b7360000-b7366000 r-xs 00000000 08:03 163004     /var/cache/fontconfig/d62e99ef547d1d24cdb1bd22ec1a2976-x86.cache-2
b7366000-b7381000 r-xs 00000000 08:03 163323     /var/cache/fontconfig/f6b893a7224233d96cb72fd88691c0b4-x86.cache-2
b7381000-b73c7000 r-xs 00000000 08:03 163322     /var/cache/fontconfig/17090aa38d5c6f09fb8c5c354938f1d7-x86.cache-2
b73c7000-b740d000 r-xs 00000000 08:03 163320     /var/cache/fontconfig/df311e82a1a24c41a75c2c930223552e-x86.cache-2
b740d000-b7416000 r-xp 00000000 08:03 765578     /lib/libnss_files-2.8.so
b7416000-b7418000 rwxp 00008000 08:03 765578     /lib/libnss_files-2.8.so
b7418000-b741a000 rwxp b7418000 00:00 0 
b741a000-b741e000 r-xp 00000000 08:03 889189     /usr/lib/libXdmcp.so.6.0.0
b741e000-b741f000 rwxp 00003000 08:03 889189     /usr/lib/libXdmcp.so.6.0.0
b741f000-b7421000 r-xp 00000000 08:03 889187     /usr/lib/libXau.so.6.0.0
b7421000-b7422000 rwxp 00001000 08:03 889187     /usr/lib/libXau.so.6.0.0
b7422000-b7423000 rwxp b7422000 00:00 0 
b7423000-b744b000 r-xp 00000000 08:03 889970     /usr/lib/libpixman-1.so.0.10.0
b744b000-b744c000 rwxp 00028000 08:03 889970     /usr/lib/libpixman-1.so.0.10.0
b744c000-b7454000 r-xp 00000000 08:03 890043     /usr/lib/libXcursor.so.1.0.2
b7454000-b7455000 rwxp 00007000 08:03 890043     /usr/lib/libXcursor.so.1.0.2
b7455000-b745a000 r-xp 00000000 08:03 889804     /usr/lib/libXrandr.so.2.1.0
b745a000-b745b000 rwxp 00005000 08:03 889804     /usr/lib/libXrandr.so.2.1.0
b745b000-b7462000 r-xp 00000000 08:03 889780     /usr/lib/libXi.so.6.0.0
b7462000-b7463000 rwxp 00006000 08:03 889780     /usr/lib/libXi.so.6.0.0
b7463000-b7464000 rwxp b7463000 00:00 0 
b7464000-b7466000 r-xp 00000000 08:03 889904     /usr/lib/libXinerama.so.1.0.0
b7466000-b7467000 rwxp 00001000 08:03 889904     /usr/lib/libXinerama.so.1.0.0
b7467000-b7474000 r-xp 00000000 08:03 889291     /usr/lib/libXext.so.6.4.0
b7474000-b7475000 rwxp 0000c000 08:03 889291     /usr/lib/libXext.so.6.4.0
b7475000-b749b000 r-xp 00000000 08:03 890049     /usr/lib/libpng12.so.0.28.0
b749b000-b749c000 rwxp 00025000 08:03 890049     /usr/lib/libpng12.so.0.28.0
b749c000-b74a0000 r-xp 00000000 08:03 889972     /usr/lib/libXfixes.so.3.1.0
b74a0000-b74a1000 rwxp 00003000 08:03 889972     /usr/lib/libXfixes.so.3.1.0
b74a1000-b74a3000 r-xp 00000000 08:03 889977     /usr/lib/libXdamage.so.1.1.0
b74a3000-b74a4000 rwxp 00001000 08:03 889977     /usr/lib/libXdamage.so.1.1.0
b74a4000-b74a5000 rwxp b74a4000 00:00 0 
b74a5000-b74a7000 r-xp 00000000 08:03 890502     /usr/lib/libXcomposite.so.1.0.0
b74a7000-b74a8000 rwxp 00001000 08:03 890502     /usr/lib/libXcomposite.so.1.0.0
b74a8000-b74d0000 r-xp 00000000 08:03 765677     /lib/libpcre.so.0.0.1
b74d0000-b74d1000 rwxp 00027000 08:03 765677     /lib/libpcre.so.0.0.1
b74d1000-b74e8000 r-xp 00000000 08:03 889280     /usr/lib/libxcb.so.1.0.0
b74e8000-b74e9000 rwxp 00016000 08:03 889280     /usr/lib/libxcb.so.1.0.0
b74e9000-b74ea000 r-xp 00000000 08:03 889230     /usr/lib/libxcb-xlib.so.0.0.0
b74ea000-b74eb000 rwxp 00000000 08:03 889230     /usr/lib/libxcb-xlib.so.0.0.0
b74eb000-b7509000 r-xp 00000000 08:03 888986     /usr/lib/libexpat.so.1.5.2
b7509000-b750b000 rwxp 0001e000 08:03 888986     /usr/lib/libexpat.so.1.5.2
b750b000-b750c000 rwxp b750b000 00:00 0 
b750c000-b7530000 r-xp 00000000 08:03 765575     /lib/libm-2.8.so
b7530000-b7532000 rwxp 00023000 08:03 765575     /lib/libm-2.8.so
b7532000-b766e000 r-xp 00000000 08:03 765576     /lib/libc-2.8.so
b766e000-b766f000 r-xp 0013c000 08:03 765576     /lib/libc-2.8.so
b766f000-b7671000 rwxp 0013d000 08:03 765576     /lib/libc-2.8.so
b7671000-b7674000 rwxp b7671000 00:00 0 
b7674000-b768b000 r-xp 00000000 08:03 890679     /usr/lib/libglade-2.0.so.0.0.7
b768b000-b768c000 rwxp 00016000 08:03 890679     /usr/lib/libglade-2.0.so.0.0.7
b768c000-b76ed000 r-xp 00000000 08:03 890419     /usr/lib/libcairo.so.2.17.5
b76ed000-b76ef000 rwxp 00061000 08:03 890419     /usr/lib/libcairo.so.2.17.5
b76ef000-b76f7000 r-xp 00000000 08:03 553965     /usr/lib/libpangocairo-1.0.so.0.2002.1
b76f7000-b76f8000 rwxp 00008000 08:03 553965     /usr/lib/libpangocairo-1.0.so.0.2002.1
b76f8000-b76f9000 rwxp b76f8000 00:00 0 
b76f9000-b7712000 r-xp 00000000 08:03 890585     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.10
b7712000-b7713000 rwxp 00019000 08:03 890585     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.10
b7713000-b772b000 r-xp 00000000 08:03 890418     /usr/lib/libatk-1.0.so.0.2209.1
b772b000-b772d000 rwxp 00018000 08:03 890418     /usr/lib/libatk-1.0.so.0.2209.1
b772d000-b77b0000 r-xp 00000000 08:03 890582     /usr/lib/libgdk-x11-2.0.so.0.1200.10
b77b0000-b77b3000 rwxp 00082000 08:03 890582     /usr/lib/libgdk-x11-2.0.so.0.1200.10
b77b3000-b7b2b000 r-xp 00000000 08:03 890581     /usr/lib/libgtk-x11-2.0.so.0.1200.10
b7b2b000-b7b31000 rwxp 00377000 08:03 890581     /usr/lib/libgtk-x11-2.0.so.0.1200.10
b7b31000-b7b32000 rwxp b7b31000 00:00 0 
b7b32000-b7b39000 r-xp 00000000 08:03 879570     /usr/lib/libstartup-notification-1.so.0.0.0
b7b39000-b7b3a000 rwxp 00006000 08:03 879570     /usr/lib/libstartup-notification-1.so.0.0.0
b7b3a000-b7b3b000 rwxp b7b3a000 00:00 0 
b7b3b000-b7bee000 r-xp 00000000 08:03 890373     /usr/lib/libglib-2.0.so.0.1600.3
b7bee000-b7bef000 rwxp 000b2000 08:03 890373     /usr/lib/libglib-2.0.so.0.1600.3
b7bef000-b7d21000 r-xp 00000000 08:03 890670     /usr/lib/libxml2.so.2.6.32
b7d21000-b7d26000 rwxp 00131000 08:03 890670     /usr/lib/libxml2.so.2.6.32
b7d26000-b7d27000 rwxp b7d26000 00:00 0 
b7d27000-b7d2a000 r-xp 00000000 08:03 553953     /usr/lib/libobparser.so.21.0.2
b7d2a000-b7d2b000 rwxp 00002000 08:03 553953     /usr/lib/libobparser.so.21.0.2
b7d2b000-b7e16000 r-xp 00000000 08:03 889286     /usr/lib/libX11.so.6.2.0
b7e16000-b7e1a000 rwxp 000ea000 08:03 889286     /usr/lib/libX11.so.6.2.0
b7e1a000-b7e2b000 r-xp 00000000 08:03 765673     /lib/libz.so.1.2.3
b7e2b000-b7e2c000 rwxp 00010000 08:03 765673     /lib/libz.so.1.2.3
b7e2c000-b7ea3000 r-xp 00000000 08:03 888962     /usr/lib/libfreetype.so.6.3.16
b7ea3000-b7ea7000 rwxp 00077000 08:03 888962     /usr/lib/libfreetype.so.6.3.16
b7ea7000-b7ea8000 rwxp b7ea7000 00:00 0 
b7ea8000-b7ed0000 r-xp 00000000 08:03 888998     /usr/lib/libfontconfig.so.1.3.0
b7ed0000-b7ed1000 rwxp 00028000 08:03 888998     /usr/lib/libfontconfig.so.1.3.0
b7ed1000-b7ed8000 r-xp 00000000 08:03 889673     /usr/lib/libXrender.so.1.3.0
b7ed8000-b7ed9000 rwxp 00007000 08:03 889673     /usr/lib/libXrender.so.1.3.0
b7ed9000-b7edb000 r-xp 00000000 08:03 765545     /lib/libdl-2.8.so
b7edb000-b7edd000 rwxp 00001000 08:03 765545     /lib/libdl-2.8.so
b7edd000-b7edf000 r-xp 00000000 08:03 890374     /usr/lib/libgmodule-2.0.so.0.1600.3
b7edf000-b7ee0000 rwxp 00002000 08:03 890374     /usr/lib/libgmodule-2.0.so.0.1600.3
b7ee0000-b7f18000 r-xp 00000000 08:03 890384     /usr/lib/libgobject-2.0.so.0.1600.3
b7f18000-b7f19000 rwxp 00038000 08:03 890384     /usr/lib/libgobject-2.0.so.0.1600.3
b7f19000-b7f55000 r-xp 00000000 08:03 553961     /usr/lib/libpango-1.0.so.0.2002.1
b7f55000-b7f57000 rwxp 0003c000 08:03 553961     /usr/lib/libpango-1.0.so.0.2002.1
b7f57000-b7f58000 rwxp b7f57000 00:00 0 
b7f58000-b7f69000 r-xp 00000000 08:03 889938     /usr/lib/libXfAborted

```

---

### Post by Dr Small on 2008-06-25
I solved it. I went into .themes and removed SlickBoxBlue, and the obconf now works. I didn't realize it was trying to import that theme in, I guess, and it was messing up obconf.

Thanks for all your help urukrama. I really do appreciate it. Now I can live happily in Openbox! Another Openbox convert! :D

Dr Small

---

### Post by urukrama on 2008-06-25
> **Dr Small said:**
> I solved it. I went into .themes and removed SlickBoxBlue, and the obconf now works. I didn't realize it was trying to import that theme in, I guess, and it was messing up obconf.

Oh, I'm sorry, I thought you did that already.

I'm not sure what the problem with that theme is. I'm trying to figure out what is wrong with it, but it is a bit annoying to have to restart Openbox and X everytime it crashes :(

I'm glad the problem is solved. I hope you enjoy Openbox :)

---

