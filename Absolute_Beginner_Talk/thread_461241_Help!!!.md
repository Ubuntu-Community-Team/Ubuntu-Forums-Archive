---
title: "Help!!!"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-06-01
SOLVED

i installed a program to change the splash screen (gnome-splashscreen-manager version 0.2-5, used it before, had to clean install because of a totally unrelated problem, just now re-installed it) and now whenever i start up ubuntu, after the log in screen, i get this...

> 
Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.


here's the details...

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "link"
SESSION_MANAGER=local/aperturescience:/tmp/.ICE-unix/13049
Initializing gnome-mount extension

** (gsynaptics-init:13134): WARNING **: Using synclient
*** glibc detected *** /usr/bin/gnome-session: malloc(): memory corruption (fast): 0x08247db8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb767e6fc]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb767f60e]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb77952c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb7b2adb0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb7b2c1e9]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_maybe_recurse+0x10d)[0xb7b2ff2d]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_region+0x40)[0xb7b301c0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_rect+0xaf)[0xb7b3027f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_draw_area+0x150)[0xb7de5440]
/usr/bin/gnome-session[0x805ce05]
/usr/lib/libglib-2.0.so.0[0xb778e3c6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb778ddf2]
/usr/lib/libglib-2.0.so.0[0xb7790dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7791179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7cc5044]
/usr/bin/gnome-session(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb762bebc]
/usr/bin/gnome-session[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:05 3654084    /usr/bin/gnome-session
08068000-08069000 rwxp 00020000 08:05 3654084    /usr/bin/gnome-session
08069000-08286000 rwxp 08069000 00:00 0          [heap]
b4600000-b4621000 rwxp b4600000 00:00 0 
b4621000-b4700000 ---p b4621000 00:00 0 
b47eb000-b47f6000 r-xp 00000000 08:05 15587      /lib/libgcc_s.so.1
b47f6000-b47f7000 rwxp 0000a000 08:05 15587      /lib/libgcc_s.so.1
b4805000-b4806000 ---p b4805000 00:00 0 
b4806000-b5006000 rwxp b4806000 00:00 0 
b5006000-b5083000 r-xp 00000000 08:05 3866880    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5083000-b5085000 r-xp 00000000 08:05 3719655    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5085000-b5086000 rwxp 00001000 08:05 3719655    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5086000-b508c000 r-xs 00000000 08:05 2588751    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b508c000-b508d000 r-xs 00000000 08:05 2589457    /var/cache/fontconfig/e3ce6b6f4283a185adf7834ae8b616de-x86.cache-2
b508d000-b508e000 r-xs 00000000 08:05 2588779    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b508e000-b5091000 r-xs 00000000 08:05 2588767    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b5091000-b5092000 r-xs 00000000 08:05 2588773    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b5092000-b5093000 r-xs 00000000 08:05 2588754    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b5093000-b5097000 r-xs 00000000 08:05 2588748    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b5097000-b5098000 r-xs 00000000 08:05 2588736    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5098000-b509a000 r-xs 00000000 08:05 2588741    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b509a000-b509c000 r-xs 00000000 08:05 2588729    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b509c000-b509d000 r-xs 00000000 08:05 2588744    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b509d000-b509f000 r-xs 00000000 08:05 2588752    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b509f000-b50a5000 r-xs 00000000 08:05 2588742    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b50a5000-b50a7000 r-xs 00000000 08:05 2588768    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b50a7000-b50a9000 r-xs 00000000 08:05 2588765    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b50a9000-b50b1000 r-xs 00000000 08:05 2588771    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b50b1000-b50b7000 r-xs 00000000 08:05 2588725    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b50b7000-b50b8000 r-xs 00000000 08:05 2589498    /var/cache/fontconfig/36022b263b29ef8f99086b28047e51ea-x86.cache-2
b50b8000-b50bb000 r-xs 00000000 08:05 2589497    /var/cache/fontconfig/b18d637dee8b4314eefef8e862256e99-x86.cache-2
b50bb000-b50bc000 r-xs 00000000 08:05 2589496    /var/cache/fontconfig/3cfdf41e5e54ad171b392b3b27150081-x86.cache-2
b50bc000-b50be000 r-xs 00000000 08:05 2589226    /var/cache/fontconfig/f54963046c5edd59fad6ee6e7bbea641-x86.cache-2
b50be000-b50bf000 r-xs 00000000 08:05 2589495    /var/cache/fontconfig/06f730fc5cbfa2ccf44533f0b84d6e2c-x86.cache-2
b50bf000-b50c0000 r-xs 00000000 08:05 2588734    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b50c0000-b50d7000 r-xs 00000000 08:05 2588778    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b50d7000-b50db000 r-xs 00000000 08:05 2589494    /var/cache/fontconfig/ca37dee8d6057f2a069c1b3d05990269-x86.cache-2
b50db000-b50dc000 r-xs 00000000 08:05 2589492    /var/cache/fontconfig/56cf4f4769d0f4abc89a4895d7bd3ae1-x86.cache-2
b50dc000-b50de000 r-xs 00000000 08:05 2588769    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b50de000-b50e0000 r-xs 00000000 08:05 2589491    /var/cache/fontconfig/589d07de58c31da87070309ffafe75ca-x86.cache-2
b50e0000-b50e1000 r-xs 00000000 08:05 2589565    /var/cache/fontconfig/fd21259e7a8837d76591e5385fa8ca76-x86.cache-2
b50e1000-b50e2000 r-xs 00000000 08:05 2589618    /var/cache/fontconfig/ab75f83bc370fedea59714e09fb2ad76-x86.cache-2
b50e2000-b50e4000 r-xs 00000000 08:05 2589490    /var/cache/fontconfig/b3eee92713a92e6bcbcb964d5cfc6ce4-x86.cache-2
b50e4000-b50e5000 r-xs 00000000 08:05 2589489    /var/cache/fontconfig/4b14b093aebc79c320de5e86ae1d3314-x86.cache-2
b50e5000-b50eb000 r-xs 00000000 08:05 2588763    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b50eb000-b50ed000 r-xs 00000000 08:05 2589488    /var/cache/fontconfig/234d4d9e8dfc2082f3673b8c72fb5bb9-x86.cache-2
b50ed000-b50f3000 r-xs 00000000 08:05 2589487    /var/cache/fontconfig/d589a48862398ed80a3d6066f4f56f4c-x86.cache-2
b50f3000-b50f4000 r-xs 00000000 08:05 2589553    /var/cache/fontconfig/39ac85a58e7b391aebd70df719ce846a-x86.cache-2
b50f4000-b50f6000 r-xs 00000000 08:05 2589486    /var/cache/fontconfig/d558a05a367274878ce7bd73af69cbb2-x86.cache-2
b50f6000-b50f8000 r-xs 00000000 08:05 2589485    /var/cache/fontconfig/7fedfe30b49f8b32cdfedf90fb7d53fb-x86.cache-2
b50f8000-b50fb000 r-xs 00000000 08:05 2588740    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b50fb000-b50ff000 r-xs 00000000 08:05 2588723    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b50ff000-b5107000 r-xs 00000000 08:05 2589480    /var/cache/fontconfig/05b8dbf7b0156f2752c290cb098c5d20-x86.cache-2
b5107000-b510e000 r-xs 00000000 08:05 2589619    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b510e000-b510f000 r-xs 00000000 08:05 2588777    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b510f000-b5110000 r-xs 00000000 08:05 2588774    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b5110000-b5111000 r-xs 00000000 08:05 2588759    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b5111000-b5112000 r-xs 00000000 08:05 2588730    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b5112000-b5113000 r-xs 00000000 08:05 2589539    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b5113000-b5116000 r-xs 00000000 08:05 2588756    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b5116000-b511b000 r-xs 00000000 08:05 2589538    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b511b000-b511d000 r-xs 00000000 08:05 2588722    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b511d000-b511e000 r-xs 00000000 08:05 2588775    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b511e000-b5120000 r-xs 00000000 08:05 2588727    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b5120000-b5121000 r-xs 00000000 08:05 2588753    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b5121000-b5126000 r-xs 00000000 08:05 2588747    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b5126000-b512a000 r-xs 00000000 08:05 2588724    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b512a000-b512c000 r-xs 00000000 08:05 2588745    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b512c000-b512f000 r-xs 00000000 08:05 2588737    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b512f000-b5130000 r-xs 00000000 08:05 2588770    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b5130000-b5132000 r-xs 00000000 08:05 2588732    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b5132000-b5136000 r-xs 00000000 08:05 2589536    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b5136000-b513c000 r-xs 00000000 08:05 2588726    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b513c000-b5144000 r-xs 00000000 08:05 2588755    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b5144000-b5146000 r-xs 00000000 08:05 2589535    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b5146000-b5149000 r-xs 00000000 08:05 2588757    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b5149000-b514b000 r-xs 00000000 08:05 2589533    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b514b000-b5370000 r-xp 00000000 08:05 3968824    /usr/share/icons/hicolor/icon-theme.cache
b5370000-b6458000 r-xp 00000000 08:05 4034714    /usr/share/icons/crystalsvg/icon-theme.cache
b6458000-b6aff000 r-xp 00000000 08:05 3968816    /usr/share/icons/gnome/icon-theme.cache
b6aff000-b6d56000 r-xp 00000000 08:05 3968813    /usr/share/icons/Tango/icon-theme.cache
b6d56000-b6d72000 r-xp 00000000 08:05 3703193    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6d72000-b6d73000 rwxp 0001b000 08:05 3703193    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6d73000-b6dd3000 rwxs 00000000 00:08 5177348    /SYSV00000000 (deleted)
b6dd3000-b6dfc000 rwxp b6dd3000 00:00 0 
b6dfc000-b6e03000 r-xp 00000000 08:05 3655106    /usr/lib/libfam.so.0.0.0
b6e03000-b6e04000 rwxp 00006000 08:05 3655106    /usr/lib/libfam.so.0.0.0
b6e04000-b6e0a000 r-xp 00000000 08:05 15552      /lib/libacl.so.1.1.0
b6e0a000-b6e0b000 rwxp 00005000 08:05 15552      /lib/libacl.so.1.1.0
b6e0b000-b6e0e000 r-xp 00000000 08:05 15556      /lib/libattr.so.1.1.0
b6e0e000-b6e0f000 rwxp 00002000 08:05 15556      /lib/libattr.so.1.1.0
b6e10000-b6e17000 r-xs 00000000 08:05 2589573    /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6e17000-b6e1b000 r-xp 00000000 08:05 3703228    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6e1b000-b6e1c000 rwxp 00003000 08:05 3703228    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6e1c000-b6e1d000 r-xs 00000000 08:05 2588749    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b6e1d000-b6e29000 r-xp 00000000 08:05 3703151    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6e29000-b6e2a000 rwxp 0000b000 08:05 3703151    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6e2a000-b6e2b000 r-xp 00000000 08:05 18929      /usr/lib/gconv/ISO8859-1.so
b6e2b000-b6e2d000 rwxp 00000000 08:05 18929      /usr/lib/gconv/ISO8859-1.so
b6e2d000-b6e68000 r-xp 00000000 08:05 3704144    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6e68000-b6e69000 r-xp 00000000 08:05 3704149    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b6e69000-b6e6a000 r-xp 00000000 08:05 3704152    /usr/lib/locale/en_US.utf8/LC_TIME
b6e6a000-b6f41000 r-xp 00000000 08:05 3704143    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6f41000-b6f42000 r-xp 00000000 08:05 3704147    /usr/lib/locale/en_US.utf8/LC_MONETARY
b6f42000-b6f4b000 r-xp 00000000 08:05 18602      /lib/tls/i686/cmov/libnss_files-2.5.so
b6f4b000-b6f4d000 rwxp 00008000 08:05 18602      /lib/tls/i686/cmov/libnss_files-2.5.so
b6f4d000-b6f55000 r-xp 00000000 08:05 18606      /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f55000-b6f57000 rwxp 00007000 08:05 18606      /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f57000-b6f5e000 r-xp 00000000 08:05 18598      /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f5e000-b6f60000 rwxp 00006000 08:05 18598      /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f60000-b6f63000 rwxp b6f60000 00:00 0 
b6f63000-b6f99000 r-xp 00000000 08:05 15639      /lib/libsepol.so.1
b6f99000-b6f9a000 rwxp 00035000 08:05 15639      /lib/libsepol.so.1
b6f9a000-b6fa4000 rwxp b6f9a000 00:00 0 
b6fa4000-b6fa7000 r-xp 00000000 08:05 3655259    /usr/lib/libgpg-error.so.0.3.0
b6fa7000-b6fa8000 rwxp 00002000 08:05 3655259    /usr/lib/libgpg-error.so.0.3.0
b6fa8000-b6ff7000 r-xp 00000000 08:05 3655147    /usr/lib/libgcrypt.so.11.2.2
b6ff7000-b6ff9000 rwxp 0004e000 08:05 3655147    /usr/lib/libgcrypt.so.11.2.2
b6ff9000-b6ffa000 rwxp b6ff9000 00:00 0 
b6ffa000-b700e000 r-xp 00000000 08:05 3655603    /usr/lib/libtasn1.so.3.0.6
b700e000-b700f000 rwxp 00013000 08:05 3655603    /usr/lib/libtasn1.so.3.0.6
b700f000-b7011000 r-xp 00000000 08:05 18619      /lib/tls/i686/cmov/libutil-2.5.so
b7011000-b7013000 rwxp 00001000 08:05 18619      /lib/tls/i686/cmov/libutil-2.5.so
b7013000-b7027000 r-xp 00000000 08:05 15638      /lib/libselinux.so.1
b7027000-b7029000 rwxp 00013000 08:05 15638      /lib/libselinux.so.1
b7029000-b7038000 r-xp 00000000 08:05 18613      /lib/tls/i686/cmov/libresolv-2.5.so
b7038000-b703a000 rwxp 0000f000 08:05 18613      /lib/tls/i686/cmov/libresolv-2.5.so
b703a000-b703c000 rwxp b703a000 00:00 0 
b703c000-b704a000 r-xp 00000000 08:05 3654985    /usr/lib/libavahi-client.so.3.2.2
b704a000-b704b000 rwxp 0000e000 08:05 3654985    /usr/lib/libavahi-client.so.3.2.2
b704b000-b704c000 rwxp b704b000 00:00 0 
b704c000-b7056000 r-xp 00000000 08:05 3654987    /usr/lib/libavahi-common.so.3.4.3
b7056000-b7057000 rwxp 00009000 08:05 3654987    /usr/lib/libavahi-common.so.3.4.3
b7057000-b7059000 r-xp 00000000 08:05 3654991    /usr/lib/libavahi-glib.so.1.0.1
b7059000-b705a000 rwxp 00001000 08:05 3654991    /usr/lib/libavahi-glib.so.1.0.1
b705a000-b70c4000 r-xp 00000000 08:05 3655255    /usr/lib/libgnutls.so.13.0.9
b70c4000-b70ca000 rwxp 0006a000 08:05 3655255    /usr/lib/libgnutls.so.13.0.9
b70ca000-b70ec000 r-xp 00000000 08:05 3655515    /usr/lib/libpng12.so.0.15.0
b70ec000-b70ed000 rwxp 00021000 08:05 3655515    /usr/lib/libpng12.so.0.15.0
b70ed000-b710b000 r-xp 00000000 08:05 3655102    /usr/lib/libexpat.so.1.0.0
b710b000-b710d000 rwxp 0001d000 08:05 3655102    /usr/lib/libexpat.so.1.0.0
b710d000-b710e000 rwxp b710d000 00:00 0 
b710e000-b7176000 r-xp 00000000 08:05 3656034    /usr/lib/libfreetype.so.6.3.10
b7176000-b7179000 rwxp 00068000 08:05 3656034    /usr/lib/libfreetype.so.6.3.10
b7179000-b718c000 r-xp 00000000 08:05 3655661    /usr/lib/libz.so.1.2.3
b718c000-b718d000 rwxp 00012000 08:05 3655661    /usr/lib/libz.so.1.2.3
b718d000-b71a0000 r-xp 00000000 08:05 18596      /lib/tls/i686/cmov/libnsl-2.5.so
b71a0000-b71a2000 rwxp 00012000 08:05 18596      /lib/tls/i686/cmov/libnsl-2.5.so
b71a2000-b71a4000 rwxp b71a2000 00:00 0 
b71a4000-b71a8000 r-xp 00000000 08:05 3654892    /usr/lib/libORBitCosNaming-2.so.0.1.0
b71a8000-b71a9000 rwxp 00003000 08:05 3654892    /usr/lib/libORBitCosNaming-2.so.0.1.0
b71a9000-b71aa000 rwxp b71a9000 00:00 0 
b71aa000-b71ae000 r-xp 00000000 08:05 3654917    /usr/lib/libXdmcp.so.6.0.0
b71ae000-b71af000 rwxp 00003000 08:05 3654917    /usr/lib/libXdmcp.so.6.0.0
b71af000-b71cd000 r-xp 00000000 08:05 3655384    /usr/lib/libjpeg.so.62.0.0
b71cd000-b71ce000 rwxp 0001d000 08:05 3655384    /usr/lib/libjpeg.so.62.0.0
b71ce000-b71d6000 r-xp 00000000 08:05 3655593    /usr/lib/libstartup-notification-1.so.0.0.0
b71d6000-b71d7000 rwxp 00007000 08:05 3655593    /usr/lib/libstartup-notification-1.so.0.0.0
b71d7000-b71d8000 rwxp b71d7000 00:00 0 
b71d8000-b71df000 r-xp 00000000 08:05 18615      /lib/tls/i686/cmov/librt-2.5.so
b71df000-b71e1000 rwxp 00006000 08:05 18615      /lib/tls/i686/cmov/librt-2.5.so
b71e1000-b71e5000 r-xp 00000000 08:05 3655311    /usr/lib/libgthread-2.0.so.0.1200.11
b71e5000-b71e6000 rwxp 00003000 08:05 3655311    /usr/lib/libgthread-2.0.so.0.1200.11
b71e6000-b71e8000 r-xp 00000000 08:05 18591      /lib/tls/i686/cmov/libdl-2.5.so
b71e8000-b71ea000 rwxp 00001000 08:05 18591      /lib/tls/i686/cmov/libdl-2.5.so
b71ea000-b71ec000 r-xp 00000000 08:05 3655213    /usr/lib/libgmodule-2.0.so.0.1200.11
b71ec000-b71ed000 rwxp 00002000 08:05 3655213    /usr/lib/libgmodule-2.0.so.0.1200.11
b71ed000-b7243000 r-xp 00000000 08:05 3655247    /usr/lib/libgnomevfs-2.so.0.1800.1
b7243000-b7246000 rwxp 00055000 08:05 3655247    /usr/lib/libgnomevfs-2.so.0.1800.1
b7246000-b72b4000 r-xp 00000000 08:05 3655010    /usr/lib/libcairo.so.2.11.1
b72b4000-b72b6000 rwxp 0006d000 08:05 3655010    /usr/lib/libcairo.so.2.11.1
b72b6000-b72b7000 rwxp b72b6000 00:00 0 
b72b7000-b72bb000 r-xp 00000000 08:05 3654923    /usr/lib/libXfixes.so.3.1.0
b72bb000-b72bc000 rwxp 00003000 08:05 3654923    /usr/lib/libXfixes.so.3.1.0
b72bc000-b72c4000 r-xp 00000000 08:05 3654913    /usr/lib/libXcursor.so.1.0.2
b72c4000-b72c5000 rwxp 00007000 08:05 3654913    /usr/lib/libXcursor.so.1.0.2
b72c5000-b72cc000 r-xp 00000000 08:05 3654929    /usr/lib/libXi.so.6.0.0
b72cc000-b72cd000 rwxp 00006000 08:05 3654929    /usr/lib/libXi.so.6.0.0
b72cd000-b72cf000 r-xp 00000000 08:05 3654931    /usr/lib/libXinerama.so.1.0.0
b72cf000-b72d0000 rwxp 00001000 08:05 3654931    /usr/lib/libXinerama.so.1.0.0
b72d0000-b72d7000 r-xp 00000000 08:05 3654943    /usr/lib/libXrender.so.1.3.0
b72d7000-b72d8000 rwxp 00006000 08:05 3654943    /usr/lib/libXrender.so.1.3.0
b72d8000-b72e5000 r-xp 00000000 08:05 3654921    /usr/lib/libXext.so.6.4.0
b72e5000-b72e6000 rwxp 0000d000 08:05 3654921    /usr/lib/libXext.so.6.4.0
b72e6000-b72e7000 rwxp b72e6000 00:00 0 
b72e7000-b730a000 r-xp 00000000 08:05 3655108    /usr/lib/libfontconfig.so.1.2.0
b730a000-b7312000 rwxp 00023000 08:05 3655108    /usr/lib/libfontconfig.so.1.2.0
b7312000-b7319000 r-xp 00000000 08:05 3655492    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7319000-b731a000 rwxp 00007000 08:05 3655492    /usr/lib/libpangocairo-1.0.so.0.1600.2
b731a000-b7344000 r-xp 00000000 08:05 3655494    /usr/lib/libpangoft2-1.0.so.0.1600.2
b7344000-b7345000 rwxp 0002a000 08:05 3655494    /usr/lib/libpangoft2-1.0.so.0.1600.2
b7345000-b7359000 r-xp 00000000 08:05 3654969    /usr/lib/libart_lgpl_2.so.2.3.17
b7359000-b735a000 rwxp 00013000 08:05 3654969    /usr/lib/libart_lgpl_2.so.2.3.17
b735a000-b7361000 r-xp 00000000 08:05 15628      /lib/libpopt.so.0.0.0
b7361000-b7362000 rwxp 00006000 08:05 15628      /lib/libpopt.so.0.0.0
b7362000-b738b000 r-xp 00000000 08:05 3655229    /usr/lib/libgnomecanvas-2.so.0.1400.0
b738b000-b738c000 rwxp 00029000 08:05 3655229    /usr/lib/libgnomecanvas-2.so.0.1400.0
b738c000-b738d000 rwxp b738c000 00:00 0 
b738d000-b73e8000 r-xp 00000000 08:05 3655006    /usr/lib/libbonoboui-2.so.0.0.0
b73e8000-b73eb000 rwxp 0005a000 08:05 3655006    /usr/lib/libbonoboui-2.so.0.0.0
b73eb000-b7502000 r-xp 00000000 08:05 3655655    /usr/lib/libxml2.so.2.6.27
b7502000-b7508000 rwxp 00116000 08:05 3655655    /usr/lib/libxml2.so.2.6.27
b7508000-b75c8000 r-xp 00000000 08:05 3654971    /usr/lib/libasound.so.2.0.0
b75c8000-b75cd000 rwxp 000bf000 08:05 3654971    /usr/lib/libasound.so.2.0.0
b75cd000-b75f2000 r-xp 00000000 08:05 18593      /lib/tls/i686/cmov/libm-2.5.so
b75f2000-b75f4000 rwxp 00024000 08:05 18593      /lib/tls/i686/cmov/libm-2.5.so
b75f4000-b7614000 r-xp 00000000 08:05 3654983    /usr/lib/libaudiofile.so.0.0.2
b7614000-b7616000 rwxp 00020000 08:05 3654983    /usr/lib/libaudiofile.so.0.0.2
b7616000-b7751000 r-xp 00000000 08:05 18585      /lib/tls/i686/cmov/libc-2.5.so
b7751000-b7752000 r-xp 0013b000 08:05 18585      /lib/tls/i686/cmov/libc-2.5.so
b7752000-b7754000 rwxp 0013c000 08:05 18585      /lib/tls/i686/cmov/libc-2.5.so
b7754000-b7758000 rwxp b7754000 00:00 0 
b7758000-b775f000 r-xp 00000000 08:05 15659      /lib/libwrap.so.0.7.6
b775f000-b7760000 rwxp 00007000 08:05 15659      /lib/libwrap.so.0.7.6
b7760000-b77f4000 r-xp 00000000 08:05 3655203    /usr/lib/libglib-2.0.so.0.1200.11
b77f4000-b77f5000 rwxp 00093000 08:05 3655203    /usr/lib/libglib-2.0.so.0.1200.11
b77f5000-b7801000 r-xp 00000000 08:05 3655219    /usr/lib/libgnome-keyring.so.0.0.1
b7801000-b7802000 rwxp 0000b000 08:05 3655219    /usr/lib/libgnome-keyring.so.0.0.1
b7802000-b783b000 r-xp 00000000 08:05 3655257    /usr/lib/libgobject-2.0.so.0.1200.11
b783b000-b783c000 rwxp 00039000 08:05 3655257    /usr/lib/libgobject-2.0.so.0.1200.11
b783c000-b786d000 r-xp 00000000 08:05 3655044    /usr/lib/libdbus-1.so.3.2.0
b786d000-b786e000 rwxp 00031000 08:05 3655044    /usr/lib/libdbus-1.so.3.2.0
b786e000-b7888000 r-xp 00000000 08:05 3655046    /usr/lib/libdbus-glib-1.so.2.1.0
b7888000-b7889000 rwxp 0001a000 08:05 3655046    /usr/lib/libdbus-glib-1.so.2.1.0
b7889000-b788a000 rwxp b7889000 00:00 0 
b788a000-b789d000 r-xp 00000000 08:05 18611      /lib/tls/i686/cmov/libpthread-2.5.so
b789d000-b789f000 rwxp 00013000 08:05 18611      /lib/tls/i686/cmov/libpthread-2.5.so
b789f000-b78a1000 rwxp b789f000 00:00 0 
b78a1000-b78ea000 r-xp 00000000 08:05 3654888    /usr/lib/libORBit-2.so.0.1.0
b78ea000-b78f4000 rwxp 00048000 08:05 3654888    /usr/lib/libORBit-2.so.0.1.0
b78f4000-b7923000 r-xp 00000000 08:05 3655145    /usr/lib/libgconf-2.so.4.1.2
b7923000-b7926000 rwxp 0002e000 08:05 3655145    /usr/lib/libgconf-2.so.4.1.2
b7926000-b7939000 r-xp 00000000 08:05 3655004    /usr/lib/libbonobo-activation.so.4.0.0
b7939000-b793b000 rwxp 00013000 08:05 3655004    /usr/lib/libbonobo-activation.so.4.0.0
b793b000-b798d000 r-xp 00000000 08:05 3655002    /usr/lib/libbonobo-2.so.0.0.0
b798d000-b7997000 rwxp 00051000 08:05 3655002    /usr/lib/libbonobo-2.so.0.0.0
b7997000-b7998000 rwxp b7997000 00:00 0 
b7998000-b7a85000 r-xp 00000000 08:05 3654900    /usr/lib/libX11.so.6.2.0
b7a85000-b7a89000 rwxp 000ed000 08:05 3654900    /usr/lib/libX11.so.6.2.0
b7a89000-b7ac5000 r-xp 00000000 08:05 3655490    /usr/lib/libpango-1.0.so.0.1600.2
b7ac5000-b7ac7000 rwxp 0003b000 08:05 3655490    /usr/lib/libpango-1.0.so.0.1600.2
b7ac7000-b7acc000 r-xp 00000000 08:05 3654941    /usr/lib/libXrandr.so.2.1.0
b7acc000-b7acd000 rwxp 00005000 08:05 3654941    /usr/lib/libXrandr.so.2.1.0
b7acd000-b7ae3000 r-xp 00000000 08:05 3655167    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7ae3000-b7ae4000 rwxp 00015000 08:05 3655167    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7ae4000-b7afd000 r-xp 00000000 08:05 3654977    /usr/lib/libatk-1.0.so.0.1809.1
b7afd000-b7aff000 rwxp 00018000 08:05 3654977    /usr/lib/libatk-1.0.so.0.1809.1
b7aff000-b7b82000 r-xp 00000000 08:05 3655165    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b82000-b7b85000 rwxp 00083000 08:05 3655165    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b85000-b7b86000 rwxp b7b85000 00:00 0 
b7b86000-b7ed7000 r-xp 00000000 08:05 3655314    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7ed7000-b7edd000 rwxp 00351000 08:05 3655314    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7edd000-b7ede000 rwxp b7edd000 00:00 0 
b7ede000-b7ef2000 r-xp 00000000 08:05 3655215    /usr/lib/libgnome-2.so.0.1800.0
b7ef2000-b7ef3000 rwxp 00014000 08:05 3655215    /usr/lib/libgnome-2.so.0.1800.0
b7ef3000-b7f08000 r-xp 00000000 08:05 3654878    /usr/lib/libICE.so.6.3.0
b7f08000-b7f0a000 rwxp 00014000 08:05 3654878    /usr/lib/libICE.so.6.3.0
b7f0a000-b7f0b000 rwxp b7f0a000 00:00 0 
b7f0b000-b7f13000 r-xp 00000000 08:05 3654896    /usr/lib/libSM.so.6.0.0
b7f13000-b7f14000 rwxp 00007000 08:05 3654896    /usr/lib/libSM.so.6.0.0
b7f14000-b7f9e000 r-xp 00000000 08:05 3655245    /usr/lib/libgnomeui-2.so.0.1788.4
b7f9e000-b7fa2000 rwxp 00089000 08:05 3655245    /usr/lib/libgnomeui-2.so.0.1788.4
b7fa2000-b7fb6000 r-xp 00000000 08:05 3655217    /usr/lib/libgnome-desktop-2.so.2.3.5
b7fb6000-b7fb7000 rwxp 00014000 08:05 3655217    /usr/lib/libgnome-desktop-2.so.2.3.5
b7fb7000-b7fb8000 rwxp b7fb7000 00:00 0 
b7fb8000-b7fc1000 r-xp 00000000 08:05 3655093    /usr/lib/libesd.so.0.2.36
b7fc1000-b7fc2000 rwxp 00009000 08:05 3655093    /usr/lib/libesd.so.0.2.36
b7fc2000-b7fc4000 r-xp 00000000 08:05 3654906    /usr/lib/libXau.so.6.0.0
b7fc4000-b7fc5000 rwxp 00001000 08:05 3654906    /usr/lib/libXau.so.6.0.0
b7fc5000-b7fc6000 r-xp 00000000 08:05 3719224    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fc6000-b7fc7000 r-xp 00000000 08:05 3704150    /usr/lib/locale/en_US.utf8/LC_PAPER
b7fc7000-b7fc8000 r-xp 00000000 08:05 3704148    /usr/lib/locale/en_US.utf8/LC_NAME
b7fc8000-b7fc9000 r-xp 00000000 08:05 3704142    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fc9000-b7fca000 r-xp 00000000 08:05 3704151    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7fca000-b7fcb000 r-xp 00000000 08:05 3704146    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7fcb000-b7fd2000 r-xs 00000000 08:05 18982      /usr/lib/gconv/gconv-modules.cache
b7fd2000-b7fd3000 r-xp 00000000 08:05 3704145    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fd3000-b7fd5000 rwxp b7fd3000 00:00 0 
b7fd5000-b7fee000 r-xp 00000000 08:05 15546      /lib/ld-2.5.so
b7fee000-b7ff0000 rwxp 00019000 08:05 15546      /lib/ld-2.5.so
bf9f7000-bfa0c000 rw-p bf9f7000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
./notifier.py:9: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  from egg.trayicon import TrayIcon

```

any ideas?  i need this fixed because when i click ok, it logs me out and i have to log back in to do anything.

---

### Post by lamalex on 2007-06-01
can you log in via command line?

---

### Post by locke.dragon on 2007-06-01
i can do anything i want on my computer as long as i don't hit ok on the message.

---

### Post by locke.dragon on 2007-06-01
if someone could tell me the name of EVERY extra thing that program installs, i can uninstall it and the other programs and put my computer back to the way it was before.  and THIS is where ubuntu system restore (similar to windoze system restore) would come in handy!

---

### Post by locke.dragon on 2007-06-01
solved.  just fiddled with gnome-splashscreen-manager for a minute.  cheers!

---

### Post by lambros on 2007-06-01
Edit: Glad you've solved your problem already, so you won't need my reply below! :-)

Lambros


On my system, the gnome-splashscreen-manager package depends on these packages:
ruby, libglade2-ruby, libgconf2-ruby

I can't really see how these packages could break your logon session in this way.  It seems more likely that gnome-splashscreen-manager has written something to the files controlling the behaviour of gnome-session.  In any case, you've stumbled into a nasty bug! :o

Could you try creating a new user-account, then log in as that new user, and see if this problem still happens?

That should indicate whether this is a system-wide problem, or whether it just affects your own user account.  If it just affects your own user account, then you could play the fun game of: "Copy files from the broken account into the working account, and see when it breaks!"

Another thing to try is, disable some of your session startup programs (go to System -> Preferences -> Sessions) - maybe one of those is the culprit?

Or maybe you have a saved session that is corrupt?

Sorry I can't be more help - at least there are a few things to try.  I guess you've already tried uninstalling gnome-splashscreen-manager?

Lambros

---

### Post by ran_foru on 2007-06-21
> **locke.dragon said:**
> SOLVED

i installed a program to change the splash screen (gnome-splashscreen-manager version 0.2-5, used it before, had to clean install because of a totally unrelated problem, just now re-installed it) and now whenever i start up ubuntu, after the log in screen, i get this...



here's the details...

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "link"
SESSION_MANAGER=local/aperturescience:/tmp/.ICE-unix/13049
Initializing gnome-mount extension

** (gsynaptics-init:13134): WARNING **: Using synclient
*** glibc detected *** /usr/bin/gnome-session: malloc(): memory corruption (fast): 0x08247db8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb767e6fc]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb767f60e]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb77952c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb7b2adb0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb7b2c1e9]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_maybe_recurse+0x10d)[0xb7b2ff2d]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_region+0x40)[0xb7b301c0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_rect+0xaf)[0xb7b3027f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_draw_area+0x150)[0xb7de5440]
/usr/bin/gnome-session[0x805ce05]
/usr/lib/libglib-2.0.so.0[0xb778e3c6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb778ddf2]
/usr/lib/libglib-2.0.so.0[0xb7790dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7791179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7cc5044]
/usr/bin/gnome-session(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb762bebc]
/usr/bin/gnome-session[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:05 3654084    /usr/bin/gnome-session
08068000-08069000 rwxp 00020000 08:05 3654084    /usr/bin/gnome-session
08069000-08286000 rwxp 08069000 00:00 0          [heap]
b4600000-b4621000 rwxp b4600000 00:00 0 
b4621000-b4700000 ---p b4621000 00:00 0 
b47eb000-b47f6000 r-xp 00000000 08:05 15587      /lib/libgcc_s.so.1
b47f6000-b47f7000 rwxp 0000a000 08:05 15587      /lib/libgcc_s.so.1
b4805000-b4806000 ---p b4805000 00:00 0 
b4806000-b5006000 rwxp b4806000 00:00 0 
b5006000-b5083000 r-xp 00000000 08:05 3866880    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5083000-b5085000 r-xp 00000000 08:05 3719655    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5085000-b5086000 rwxp 00001000 08:05 3719655    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5086000-b508c000 r-xs 00000000 08:05 2588751    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b508c000-b508d000 r-xs 00000000 08:05 2589457    /var/cache/fontconfig/e3ce6b6f4283a185adf7834ae8b616de-x86.cache-2
b508d000-b508e000 r-xs 00000000 08:05 2588779    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b508e000-b5091000 r-xs 00000000 08:05 2588767    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b5091000-b5092000 r-xs 00000000 08:05 2588773    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b5092000-b5093000 r-xs 00000000 08:05 2588754    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b5093000-b5097000 r-xs 00000000 08:05 2588748    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b5097000-b5098000 r-xs 00000000 08:05 2588736    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5098000-b509a000 r-xs 00000000 08:05 2588741    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b509a000-b509c000 r-xs 00000000 08:05 2588729    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b509c000-b509d000 r-xs 00000000 08:05 2588744    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b509d000-b509f000 r-xs 00000000 08:05 2588752    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b509f000-b50a5000 r-xs 00000000 08:05 2588742    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b50a5000-b50a7000 r-xs 00000000 08:05 2588768    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b50a7000-b50a9000 r-xs 00000000 08:05 2588765    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b50a9000-b50b1000 r-xs 00000000 08:05 2588771    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b50b1000-b50b7000 r-xs 00000000 08:05 2588725    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b50b7000-b50b8000 r-xs 00000000 08:05 2589498    /var/cache/fontconfig/36022b263b29ef8f99086b28047e51ea-x86.cache-2
b50b8000-b50bb000 r-xs 00000000 08:05 2589497    /var/cache/fontconfig/b18d637dee8b4314eefef8e862256e99-x86.cache-2
b50bb000-b50bc000 r-xs 00000000 08:05 2589496    /var/cache/fontconfig/3cfdf41e5e54ad171b392b3b27150081-x86.cache-2
b50bc000-b50be000 r-xs 00000000 08:05 2589226    /var/cache/fontconfig/f54963046c5edd59fad6ee6e7bbea641-x86.cache-2
b50be000-b50bf000 r-xs 00000000 08:05 2589495    /var/cache/fontconfig/06f730fc5cbfa2ccf44533f0b84d6e2c-x86.cache-2
b50bf000-b50c0000 r-xs 00000000 08:05 2588734    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b50c0000-b50d7000 r-xs 00000000 08:05 2588778    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b50d7000-b50db000 r-xs 00000000 08:05 2589494    /var/cache/fontconfig/ca37dee8d6057f2a069c1b3d05990269-x86.cache-2
b50db000-b50dc000 r-xs 00000000 08:05 2589492    /var/cache/fontconfig/56cf4f4769d0f4abc89a4895d7bd3ae1-x86.cache-2
b50dc000-b50de000 r-xs 00000000 08:05 2588769    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b50de000-b50e0000 r-xs 00000000 08:05 2589491    /var/cache/fontconfig/589d07de58c31da87070309ffafe75ca-x86.cache-2
b50e0000-b50e1000 r-xs 00000000 08:05 2589565    /var/cache/fontconfig/fd21259e7a8837d76591e5385fa8ca76-x86.cache-2
b50e1000-b50e2000 r-xs 00000000 08:05 2589618    /var/cache/fontconfig/ab75f83bc370fedea59714e09fb2ad76-x86.cache-2
b50e2000-b50e4000 r-xs 00000000 08:05 2589490    /var/cache/fontconfig/b3eee92713a92e6bcbcb964d5cfc6ce4-x86.cache-2
b50e4000-b50e5000 r-xs 00000000 08:05 2589489    /var/cache/fontconfig/4b14b093aebc79c320de5e86ae1d3314-x86.cache-2
b50e5000-b50eb000 r-xs 00000000 08:05 2588763    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b50eb000-b50ed000 r-xs 00000000 08:05 2589488    /var/cache/fontconfig/234d4d9e8dfc2082f3673b8c72fb5bb9-x86.cache-2
b50ed000-b50f3000 r-xs 00000000 08:05 2589487    /var/cache/fontconfig/d589a48862398ed80a3d6066f4f56f4c-x86.cache-2
b50f3000-b50f4000 r-xs 00000000 08:05 2589553    /var/cache/fontconfig/39ac85a58e7b391aebd70df719ce846a-x86.cache-2
b50f4000-b50f6000 r-xs 00000000 08:05 2589486    /var/cache/fontconfig/d558a05a367274878ce7bd73af69cbb2-x86.cache-2
b50f6000-b50f8000 r-xs 00000000 08:05 2589485    /var/cache/fontconfig/7fedfe30b49f8b32cdfedf90fb7d53fb-x86.cache-2
b50f8000-b50fb000 r-xs 00000000 08:05 2588740    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b50fb000-b50ff000 r-xs 00000000 08:05 2588723    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b50ff000-b5107000 r-xs 00000000 08:05 2589480    /var/cache/fontconfig/05b8dbf7b0156f2752c290cb098c5d20-x86.cache-2
b5107000-b510e000 r-xs 00000000 08:05 2589619    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b510e000-b510f000 r-xs 00000000 08:05 2588777    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b510f000-b5110000 r-xs 00000000 08:05 2588774    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b5110000-b5111000 r-xs 00000000 08:05 2588759    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b5111000-b5112000 r-xs 00000000 08:05 2588730    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b5112000-b5113000 r-xs 00000000 08:05 2589539    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b5113000-b5116000 r-xs 00000000 08:05 2588756    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b5116000-b511b000 r-xs 00000000 08:05 2589538    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b511b000-b511d000 r-xs 00000000 08:05 2588722    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b511d000-b511e000 r-xs 00000000 08:05 2588775    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b511e000-b5120000 r-xs 00000000 08:05 2588727    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b5120000-b5121000 r-xs 00000000 08:05 2588753    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b5121000-b5126000 r-xs 00000000 08:05 2588747    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b5126000-b512a000 r-xs 00000000 08:05 2588724    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b512a000-b512c000 r-xs 00000000 08:05 2588745    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b512c000-b512f000 r-xs 00000000 08:05 2588737    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b512f000-b5130000 r-xs 00000000 08:05 2588770    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b5130000-b5132000 r-xs 00000000 08:05 2588732    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b5132000-b5136000 r-xs 00000000 08:05 2589536    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b5136000-b513c000 r-xs 00000000 08:05 2588726    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b513c000-b5144000 r-xs 00000000 08:05 2588755    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b5144000-b5146000 r-xs 00000000 08:05 2589535    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b5146000-b5149000 r-xs 00000000 08:05 2588757    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b5149000-b514b000 r-xs 00000000 08:05 2589533    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b514b000-b5370000 r-xp 00000000 08:05 3968824    /usr/share/icons/hicolor/icon-theme.cache
b5370000-b6458000 r-xp 00000000 08:05 4034714    /usr/share/icons/crystalsvg/icon-theme.cache
b6458000-b6aff000 r-xp 00000000 08:05 3968816    /usr/share/icons/gnome/icon-theme.cache
b6aff000-b6d56000 r-xp 00000000 08:05 3968813    /usr/share/icons/Tango/icon-theme.cache
b6d56000-b6d72000 r-xp 00000000 08:05 3703193    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6d72000-b6d73000 rwxp 0001b000 08:05 3703193    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6d73000-b6dd3000 rwxs 00000000 00:08 5177348    /SYSV00000000 (deleted)
b6dd3000-b6dfc000 rwxp b6dd3000 00:00 0 
b6dfc000-b6e03000 r-xp 00000000 08:05 3655106    /usr/lib/libfam.so.0.0.0
b6e03000-b6e04000 rwxp 00006000 08:05 3655106    /usr/lib/libfam.so.0.0.0
b6e04000-b6e0a000 r-xp 00000000 08:05 15552      /lib/libacl.so.1.1.0
b6e0a000-b6e0b000 rwxp 00005000 08:05 15552      /lib/libacl.so.1.1.0
b6e0b000-b6e0e000 r-xp 00000000 08:05 15556      /lib/libattr.so.1.1.0
b6e0e000-b6e0f000 rwxp 00002000 08:05 15556      /lib/libattr.so.1.1.0
b6e10000-b6e17000 r-xs 00000000 08:05 2589573    /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6e17000-b6e1b000 r-xp 00000000 08:05 3703228    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6e1b000-b6e1c000 rwxp 00003000 08:05 3703228    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6e1c000-b6e1d000 r-xs 00000000 08:05 2588749    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b6e1d000-b6e29000 r-xp 00000000 08:05 3703151    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6e29000-b6e2a000 rwxp 0000b000 08:05 3703151    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6e2a000-b6e2b000 r-xp 00000000 08:05 18929      /usr/lib/gconv/ISO8859-1.so
b6e2b000-b6e2d000 rwxp 00000000 08:05 18929      /usr/lib/gconv/ISO8859-1.so
b6e2d000-b6e68000 r-xp 00000000 08:05 3704144    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6e68000-b6e69000 r-xp 00000000 08:05 3704149    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b6e69000-b6e6a000 r-xp 00000000 08:05 3704152    /usr/lib/locale/en_US.utf8/LC_TIME
b6e6a000-b6f41000 r-xp 00000000 08:05 3704143    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6f41000-b6f42000 r-xp 00000000 08:05 3704147    /usr/lib/locale/en_US.utf8/LC_MONETARY
b6f42000-b6f4b000 r-xp 00000000 08:05 18602      /lib/tls/i686/cmov/libnss_files-2.5.so
b6f4b000-b6f4d000 rwxp 00008000 08:05 18602      /lib/tls/i686/cmov/libnss_files-2.5.so
b6f4d000-b6f55000 r-xp 00000000 08:05 18606      /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f55000-b6f57000 rwxp 00007000 08:05 18606      /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f57000-b6f5e000 r-xp 00000000 08:05 18598      /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f5e000-b6f60000 rwxp 00006000 08:05 18598      /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f60000-b6f63000 rwxp b6f60000 00:00 0 
b6f63000-b6f99000 r-xp 00000000 08:05 15639      /lib/libsepol.so.1
b6f99000-b6f9a000 rwxp 00035000 08:05 15639      /lib/libsepol.so.1
b6f9a000-b6fa4000 rwxp b6f9a000 00:00 0 
b6fa4000-b6fa7000 r-xp 00000000 08:05 3655259    /usr/lib/libgpg-error.so.0.3.0
b6fa7000-b6fa8000 rwxp 00002000 08:05 3655259    /usr/lib/libgpg-error.so.0.3.0
b6fa8000-b6ff7000 r-xp 00000000 08:05 3655147    /usr/lib/libgcrypt.so.11.2.2
b6ff7000-b6ff9000 rwxp 0004e000 08:05 3655147    /usr/lib/libgcrypt.so.11.2.2
b6ff9000-b6ffa000 rwxp b6ff9000 00:00 0 
b6ffa000-b700e000 r-xp 00000000 08:05 3655603    /usr/lib/libtasn1.so.3.0.6
b700e000-b700f000 rwxp 00013000 08:05 3655603    /usr/lib/libtasn1.so.3.0.6
b700f000-b7011000 r-xp 00000000 08:05 18619      /lib/tls/i686/cmov/libutil-2.5.so
b7011000-b7013000 rwxp 00001000 08:05 18619      /lib/tls/i686/cmov/libutil-2.5.so
b7013000-b7027000 r-xp 00000000 08:05 15638      /lib/libselinux.so.1
b7027000-b7029000 rwxp 00013000 08:05 15638      /lib/libselinux.so.1
b7029000-b7038000 r-xp 00000000 08:05 18613      /lib/tls/i686/cmov/libresolv-2.5.so
b7038000-b703a000 rwxp 0000f000 08:05 18613      /lib/tls/i686/cmov/libresolv-2.5.so
b703a000-b703c000 rwxp b703a000 00:00 0 
b703c000-b704a000 r-xp 00000000 08:05 3654985    /usr/lib/libavahi-client.so.3.2.2
b704a000-b704b000 rwxp 0000e000 08:05 3654985    /usr/lib/libavahi-client.so.3.2.2
b704b000-b704c000 rwxp b704b000 00:00 0 
b704c000-b7056000 r-xp 00000000 08:05 3654987    /usr/lib/libavahi-common.so.3.4.3
b7056000-b7057000 rwxp 00009000 08:05 3654987    /usr/lib/libavahi-common.so.3.4.3
b7057000-b7059000 r-xp 00000000 08:05 3654991    /usr/lib/libavahi-glib.so.1.0.1
b7059000-b705a000 rwxp 00001000 08:05 3654991    /usr/lib/libavahi-glib.so.1.0.1
b705a000-b70c4000 r-xp 00000000 08:05 3655255    /usr/lib/libgnutls.so.13.0.9
b70c4000-b70ca000 rwxp 0006a000 08:05 3655255    /usr/lib/libgnutls.so.13.0.9
b70ca000-b70ec000 r-xp 00000000 08:05 3655515    /usr/lib/libpng12.so.0.15.0
b70ec000-b70ed000 rwxp 00021000 08:05 3655515    /usr/lib/libpng12.so.0.15.0
b70ed000-b710b000 r-xp 00000000 08:05 3655102    /usr/lib/libexpat.so.1.0.0
b710b000-b710d000 rwxp 0001d000 08:05 3655102    /usr/lib/libexpat.so.1.0.0
b710d000-b710e000 rwxp b710d000 00:00 0 
b710e000-b7176000 r-xp 00000000 08:05 3656034    /usr/lib/libfreetype.so.6.3.10
b7176000-b7179000 rwxp 00068000 08:05 3656034    /usr/lib/libfreetype.so.6.3.10
b7179000-b718c000 r-xp 00000000 08:05 3655661    /usr/lib/libz.so.1.2.3
b718c000-b718d000 rwxp 00012000 08:05 3655661    /usr/lib/libz.so.1.2.3
b718d000-b71a0000 r-xp 00000000 08:05 18596      /lib/tls/i686/cmov/libnsl-2.5.so
b71a0000-b71a2000 rwxp 00012000 08:05 18596      /lib/tls/i686/cmov/libnsl-2.5.so
b71a2000-b71a4000 rwxp b71a2000 00:00 0 
b71a4000-b71a8000 r-xp 00000000 08:05 3654892    /usr/lib/libORBitCosNaming-2.so.0.1.0
b71a8000-b71a9000 rwxp 00003000 08:05 3654892    /usr/lib/libORBitCosNaming-2.so.0.1.0
b71a9000-b71aa000 rwxp b71a9000 00:00 0 
b71aa000-b71ae000 r-xp 00000000 08:05 3654917    /usr/lib/libXdmcp.so.6.0.0
b71ae000-b71af000 rwxp 00003000 08:05 3654917    /usr/lib/libXdmcp.so.6.0.0
b71af000-b71cd000 r-xp 00000000 08:05 3655384    /usr/lib/libjpeg.so.62.0.0
b71cd000-b71ce000 rwxp 0001d000 08:05 3655384    /usr/lib/libjpeg.so.62.0.0
b71ce000-b71d6000 r-xp 00000000 08:05 3655593    /usr/lib/libstartup-notification-1.so.0.0.0
b71d6000-b71d7000 rwxp 00007000 08:05 3655593    /usr/lib/libstartup-notification-1.so.0.0.0
b71d7000-b71d8000 rwxp b71d7000 00:00 0 
b71d8000-b71df000 r-xp 00000000 08:05 18615      /lib/tls/i686/cmov/librt-2.5.so
b71df000-b71e1000 rwxp 00006000 08:05 18615      /lib/tls/i686/cmov/librt-2.5.so
b71e1000-b71e5000 r-xp 00000000 08:05 3655311    /usr/lib/libgthread-2.0.so.0.1200.11
b71e5000-b71e6000 rwxp 00003000 08:05 3655311    /usr/lib/libgthread-2.0.so.0.1200.11
b71e6000-b71e8000 r-xp 00000000 08:05 18591      /lib/tls/i686/cmov/libdl-2.5.so
b71e8000-b71ea000 rwxp 00001000 08:05 18591      /lib/tls/i686/cmov/libdl-2.5.so
b71ea000-b71ec000 r-xp 00000000 08:05 3655213    /usr/lib/libgmodule-2.0.so.0.1200.11
b71ec000-b71ed000 rwxp 00002000 08:05 3655213    /usr/lib/libgmodule-2.0.so.0.1200.11
b71ed000-b7243000 r-xp 00000000 08:05 3655247    /usr/lib/libgnomevfs-2.so.0.1800.1
b7243000-b7246000 rwxp 00055000 08:05 3655247    /usr/lib/libgnomevfs-2.so.0.1800.1
b7246000-b72b4000 r-xp 00000000 08:05 3655010    /usr/lib/libcairo.so.2.11.1
b72b4000-b72b6000 rwxp 0006d000 08:05 3655010    /usr/lib/libcairo.so.2.11.1
b72b6000-b72b7000 rwxp b72b6000 00:00 0 
b72b7000-b72bb000 r-xp 00000000 08:05 3654923    /usr/lib/libXfixes.so.3.1.0
b72bb000-b72bc000 rwxp 00003000 08:05 3654923    /usr/lib/libXfixes.so.3.1.0
b72bc000-b72c4000 r-xp 00000000 08:05 3654913    /usr/lib/libXcursor.so.1.0.2
b72c4000-b72c5000 rwxp 00007000 08:05 3654913    /usr/lib/libXcursor.so.1.0.2
b72c5000-b72cc000 r-xp 00000000 08:05 3654929    /usr/lib/libXi.so.6.0.0
b72cc000-b72cd000 rwxp 00006000 08:05 3654929    /usr/lib/libXi.so.6.0.0
b72cd000-b72cf000 r-xp 00000000 08:05 3654931    /usr/lib/libXinerama.so.1.0.0
b72cf000-b72d0000 rwxp 00001000 08:05 3654931    /usr/lib/libXinerama.so.1.0.0
b72d0000-b72d7000 r-xp 00000000 08:05 3654943    /usr/lib/libXrender.so.1.3.0
b72d7000-b72d8000 rwxp 00006000 08:05 3654943    /usr/lib/libXrender.so.1.3.0
b72d8000-b72e5000 r-xp 00000000 08:05 3654921    /usr/lib/libXext.so.6.4.0
b72e5000-b72e6000 rwxp 0000d000 08:05 3654921    /usr/lib/libXext.so.6.4.0
b72e6000-b72e7000 rwxp b72e6000 00:00 0 
b72e7000-b730a000 r-xp 00000000 08:05 3655108    /usr/lib/libfontconfig.so.1.2.0
b730a000-b7312000 rwxp 00023000 08:05 3655108    /usr/lib/libfontconfig.so.1.2.0
b7312000-b7319000 r-xp 00000000 08:05 3655492    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7319000-b731a000 rwxp 00007000 08:05 3655492    /usr/lib/libpangocairo-1.0.so.0.1600.2
b731a000-b7344000 r-xp 00000000 08:05 3655494    /usr/lib/libpangoft2-1.0.so.0.1600.2
b7344000-b7345000 rwxp 0002a000 08:05 3655494    /usr/lib/libpangoft2-1.0.so.0.1600.2
b7345000-b7359000 r-xp 00000000 08:05 3654969    /usr/lib/libart_lgpl_2.so.2.3.17
b7359000-b735a000 rwxp 00013000 08:05 3654969    /usr/lib/libart_lgpl_2.so.2.3.17
b735a000-b7361000 r-xp 00000000 08:05 15628      /lib/libpopt.so.0.0.0
b7361000-b7362000 rwxp 00006000 08:05 15628      /lib/libpopt.so.0.0.0
b7362000-b738b000 r-xp 00000000 08:05 3655229    /usr/lib/libgnomecanvas-2.so.0.1400.0
b738b000-b738c000 rwxp 00029000 08:05 3655229    /usr/lib/libgnomecanvas-2.so.0.1400.0
b738c000-b738d000 rwxp b738c000 00:00 0 
b738d000-b73e8000 r-xp 00000000 08:05 3655006    /usr/lib/libbonoboui-2.so.0.0.0
b73e8000-b73eb000 rwxp 0005a000 08:05 3655006    /usr/lib/libbonoboui-2.so.0.0.0
b73eb000-b7502000 r-xp 00000000 08:05 3655655    /usr/lib/libxml2.so.2.6.27
b7502000-b7508000 rwxp 00116000 08:05 3655655    /usr/lib/libxml2.so.2.6.27
b7508000-b75c8000 r-xp 00000000 08:05 3654971    /usr/lib/libasound.so.2.0.0
b75c8000-b75cd000 rwxp 000bf000 08:05 3654971    /usr/lib/libasound.so.2.0.0
b75cd000-b75f2000 r-xp 00000000 08:05 18593      /lib/tls/i686/cmov/libm-2.5.so
b75f2000-b75f4000 rwxp 00024000 08:05 18593      /lib/tls/i686/cmov/libm-2.5.so
b75f4000-b7614000 r-xp 00000000 08:05 3654983    /usr/lib/libaudiofile.so.0.0.2
b7614000-b7616000 rwxp 00020000 08:05 3654983    /usr/lib/libaudiofile.so.0.0.2
b7616000-b7751000 r-xp 00000000 08:05 18585      /lib/tls/i686/cmov/libc-2.5.so
b7751000-b7752000 r-xp 0013b000 08:05 18585      /lib/tls/i686/cmov/libc-2.5.so
b7752000-b7754000 rwxp 0013c000 08:05 18585      /lib/tls/i686/cmov/libc-2.5.so
b7754000-b7758000 rwxp b7754000 00:00 0 
b7758000-b775f000 r-xp 00000000 08:05 15659      /lib/libwrap.so.0.7.6
b775f000-b7760000 rwxp 00007000 08:05 15659      /lib/libwrap.so.0.7.6
b7760000-b77f4000 r-xp 00000000 08:05 3655203    /usr/lib/libglib-2.0.so.0.1200.11
b77f4000-b77f5000 rwxp 00093000 08:05 3655203    /usr/lib/libglib-2.0.so.0.1200.11
b77f5000-b7801000 r-xp 00000000 08:05 3655219    /usr/lib/libgnome-keyring.so.0.0.1
b7801000-b7802000 rwxp 0000b000 08:05 3655219    /usr/lib/libgnome-keyring.so.0.0.1
b7802000-b783b000 r-xp 00000000 08:05 3655257    /usr/lib/libgobject-2.0.so.0.1200.11
b783b000-b783c000 rwxp 00039000 08:05 3655257    /usr/lib/libgobject-2.0.so.0.1200.11
b783c000-b786d000 r-xp 00000000 08:05 3655044    /usr/lib/libdbus-1.so.3.2.0
b786d000-b786e000 rwxp 00031000 08:05 3655044    /usr/lib/libdbus-1.so.3.2.0
b786e000-b7888000 r-xp 00000000 08:05 3655046    /usr/lib/libdbus-glib-1.so.2.1.0
b7888000-b7889000 rwxp 0001a000 08:05 3655046    /usr/lib/libdbus-glib-1.so.2.1.0
b7889000-b788a000 rwxp b7889000 00:00 0 
b788a000-b789d000 r-xp 00000000 08:05 18611      /lib/tls/i686/cmov/libpthread-2.5.so
b789d000-b789f000 rwxp 00013000 08:05 18611      /lib/tls/i686/cmov/libpthread-2.5.so
b789f000-b78a1000 rwxp b789f000 00:00 0 
b78a1000-b78ea000 r-xp 00000000 08:05 3654888    /usr/lib/libORBit-2.so.0.1.0
b78ea000-b78f4000 rwxp 00048000 08:05 3654888    /usr/lib/libORBit-2.so.0.1.0
b78f4000-b7923000 r-xp 00000000 08:05 3655145    /usr/lib/libgconf-2.so.4.1.2
b7923000-b7926000 rwxp 0002e000 08:05 3655145    /usr/lib/libgconf-2.so.4.1.2
b7926000-b7939000 r-xp 00000000 08:05 3655004    /usr/lib/libbonobo-activation.so.4.0.0
b7939000-b793b000 rwxp 00013000 08:05 3655004    /usr/lib/libbonobo-activation.so.4.0.0
b793b000-b798d000 r-xp 00000000 08:05 3655002    /usr/lib/libbonobo-2.so.0.0.0
b798d000-b7997000 rwxp 00051000 08:05 3655002    /usr/lib/libbonobo-2.so.0.0.0
b7997000-b7998000 rwxp b7997000 00:00 0 
b7998000-b7a85000 r-xp 00000000 08:05 3654900    /usr/lib/libX11.so.6.2.0
b7a85000-b7a89000 rwxp 000ed000 08:05 3654900    /usr/lib/libX11.so.6.2.0
b7a89000-b7ac5000 r-xp 00000000 08:05 3655490    /usr/lib/libpango-1.0.so.0.1600.2
b7ac5000-b7ac7000 rwxp 0003b000 08:05 3655490    /usr/lib/libpango-1.0.so.0.1600.2
b7ac7000-b7acc000 r-xp 00000000 08:05 3654941    /usr/lib/libXrandr.so.2.1.0
b7acc000-b7acd000 rwxp 00005000 08:05 3654941    /usr/lib/libXrandr.so.2.1.0
b7acd000-b7ae3000 r-xp 00000000 08:05 3655167    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7ae3000-b7ae4000 rwxp 00015000 08:05 3655167    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7ae4000-b7afd000 r-xp 00000000 08:05 3654977    /usr/lib/libatk-1.0.so.0.1809.1
b7afd000-b7aff000 rwxp 00018000 08:05 3654977    /usr/lib/libatk-1.0.so.0.1809.1
b7aff000-b7b82000 r-xp 00000000 08:05 3655165    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b82000-b7b85000 rwxp 00083000 08:05 3655165    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b85000-b7b86000 rwxp b7b85000 00:00 0 
b7b86000-b7ed7000 r-xp 00000000 08:05 3655314    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7ed7000-b7edd000 rwxp 00351000 08:05 3655314    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7edd000-b7ede000 rwxp b7edd000 00:00 0 
b7ede000-b7ef2000 r-xp 00000000 08:05 3655215    /usr/lib/libgnome-2.so.0.1800.0
b7ef2000-b7ef3000 rwxp 00014000 08:05 3655215    /usr/lib/libgnome-2.so.0.1800.0
b7ef3000-b7f08000 r-xp 00000000 08:05 3654878    /usr/lib/libICE.so.6.3.0
b7f08000-b7f0a000 rwxp 00014000 08:05 3654878    /usr/lib/libICE.so.6.3.0
b7f0a000-b7f0b000 rwxp b7f0a000 00:00 0 
b7f0b000-b7f13000 r-xp 00000000 08:05 3654896    /usr/lib/libSM.so.6.0.0
b7f13000-b7f14000 rwxp 00007000 08:05 3654896    /usr/lib/libSM.so.6.0.0
b7f14000-b7f9e000 r-xp 00000000 08:05 3655245    /usr/lib/libgnomeui-2.so.0.1788.4
b7f9e000-b7fa2000 rwxp 00089000 08:05 3655245    /usr/lib/libgnomeui-2.so.0.1788.4
b7fa2000-b7fb6000 r-xp 00000000 08:05 3655217    /usr/lib/libgnome-desktop-2.so.2.3.5
b7fb6000-b7fb7000 rwxp 00014000 08:05 3655217    /usr/lib/libgnome-desktop-2.so.2.3.5
b7fb7000-b7fb8000 rwxp b7fb7000 00:00 0 
b7fb8000-b7fc1000 r-xp 00000000 08:05 3655093    /usr/lib/libesd.so.0.2.36
b7fc1000-b7fc2000 rwxp 00009000 08:05 3655093    /usr/lib/libesd.so.0.2.36
b7fc2000-b7fc4000 r-xp 00000000 08:05 3654906    /usr/lib/libXau.so.6.0.0
b7fc4000-b7fc5000 rwxp 00001000 08:05 3654906    /usr/lib/libXau.so.6.0.0
b7fc5000-b7fc6000 r-xp 00000000 08:05 3719224    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fc6000-b7fc7000 r-xp 00000000 08:05 3704150    /usr/lib/locale/en_US.utf8/LC_PAPER
b7fc7000-b7fc8000 r-xp 00000000 08:05 3704148    /usr/lib/locale/en_US.utf8/LC_NAME
b7fc8000-b7fc9000 r-xp 00000000 08:05 3704142    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fc9000-b7fca000 r-xp 00000000 08:05 3704151    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7fca000-b7fcb000 r-xp 00000000 08:05 3704146    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7fcb000-b7fd2000 r-xs 00000000 08:05 18982      /usr/lib/gconv/gconv-modules.cache
b7fd2000-b7fd3000 r-xp 00000000 08:05 3704145    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fd3000-b7fd5000 rwxp b7fd3000 00:00 0 
b7fd5000-b7fee000 r-xp 00000000 08:05 15546      /lib/ld-2.5.so
b7fee000-b7ff0000 rwxp 00019000 08:05 15546      /lib/ld-2.5.so
bf9f7000-bfa0c000 rw-p bf9f7000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
./notifier.py:9: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  from egg.trayicon import TrayIcon

```

any ideas?  i need this fixed because when i click ok, it logs me out and i have to log back in to do anything.




Hey 

Exactly same problem i m facing same errors

Can u explain how u fix this problem

Thx

---

