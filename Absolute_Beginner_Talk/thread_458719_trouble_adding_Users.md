---
title: "trouble adding Users"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-05-29
ok this is the 2nd time i tried adding a user, each time, logging in works, until i change the desktop or anything else for that matter, then it fives me the that 10 second logging off prompt. My main account works fine, as well as my second account, it is my 3rd account i am having troubles with, here is the xsessions-error log

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "properties"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/treehouse:/tmp/.ICE-unix/27467
*** glibc detected *** x-session-manager: malloc(): memory corruption (fast): 0x0826edf8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76136fc]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb761460e]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb772a2c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb7abfdb0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb7ac11e9]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_maybe_recurse+0x10d)[0xb7ac4f2d]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_region+0x40)[0xb7ac51c0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_rect+0xaf)[0xb7ac527f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_draw_area+0x150)[0xb7d7a440]
x-session-manager[0x805ce05]
/usr/lib/libglib-2.0.so.0[0xb77233c6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7722df2]
/usr/lib/libglib-2.0.so.0[0xb7725dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7726179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c5a044]
x-session-manager(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75c0ebc]
x-session-manager[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 03:41 23003588   /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 03:41 23003588   /usr/bin/gnome-session
08069000-082ab000 rw-p 08069000 00:00 0          [heap]
b4300000-b4321000 rw-p b4300000 00:00 0 
b4321000-b4400000 ---p b4321000 00:00 0 
b44f2000-b44fd000 r-xp 00000000 03:41 22609984   /lib/libgcc_s.so.1
b44fd000-b44fe000 rw-p 0000a000 03:41 22609984   /lib/libgcc_s.so.1
b4510000-b4511000 ---p b4510000 00:00 0 
b4511000-b4d11000 rw-p b4511000 00:00 0 
b4d11000-b4d8e000 r--p 00000000 03:41 23249046   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4d8e000-b4d90000 r-xp 00000000 03:41 23135419   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4d90000-b4d91000 rw-p 00001000 03:41 23135419   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4d91000-b4d97000 r--s 00000000 03:41 26968143   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b4d97000-b4d98000 r--s 00000000 03:41 26968171   /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b4d98000-b4d9b000 r--s 00000000 03:41 26968159   /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b4d9b000-b4d9c000 r--s 00000000 03:41 26968165   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b4d9c000-b4d9d000 r--s 00000000 03:41 26968146   /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b4d9d000-b4da1000 r--s 00000000 03:41 26968140   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b4da1000-b4da4000 r--s 00000000 03:41 26970344   /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86.cache-2
b4da4000-b4da5000 r--s 00000000 03:41 26968128   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b4da5000-b4da7000 r--s 00000000 03:41 26968133   /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b4da7000-b4da9000 r--s 00000000 03:41 26968121   /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b4da9000-b4daa000 r--s 00000000 03:41 26968136   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b4daa000-b4dac000 r--s 00000000 03:41 26968144   /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b4dac000-b4db2000 r--s 00000000 03:41 26968134   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4db2000-b4db4000 r--s 00000000 03:41 26968160   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4db4000-b4db6000 r--s 00000000 03:41 26968157   /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b4db6000-b4dbe000 r--s 00000000 03:41 26968163   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b4dbe000-b4dc4000 r--s 00000000 03:41 26968117   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b4dc4000-b4dc5000 r--s 00000000 03:41 26968126   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4dc5000-b4ddc000 r--s 00000000 03:41 26969122   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b4ddc000-b4dde000 r--s 00000000 03:41 26968161   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b4dde000-b4de4000 r--s 00000000 03:41 26968155   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b4de4000-b4de8000 r--s 00000000 03:41 26971616   /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b4de8000-b4deb000 r--s 00000000 03:41 26968132   /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b4deb000-b4def000 r--s 00000000 03:41 26968115   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4def000-b4df6000 r--s 00000000 03:41 26970342   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b4df6000-b4df7000 r--s 00000000 03:41 26968169   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b4df7000-b4df8000 r--s 00000000 03:41 26968166   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b4df8000-b4df9000 r--s 00000000 03:41 26968151   /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b4df9000-b4dfa000 r--s 00000000 03:41 26968122   /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b4dfa000-b4dfb000 r--s 00000000 03:41 26975048   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b4dfb000-b4dfc000 r--s 00000000 03:41 26974561   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b4dfc000-b4dff000 r--s 00000000 03:41 26968148   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b4dff000-b4e04000 r--s 00000000 03:41 26974556   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b4e04000-b4e06000 r--s 00000000 03:41 26975047   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b4e06000-b4e07000 r--s 00000000 03:41 26968167   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b4e07000-b4e09000 r--s 00000000 03:41 26975046   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b4e09000-b4e0a000 r--s 00000000 03:41 26968145   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b4e0a000-b4e0f000 r--s 00000000 03:41 26968139   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b4e0f000-b4e13000 r--s 00000000 03:41 26975045   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b4e13000-b4e18000 r--s 00000000 03:41 26971004   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b4e18000-b4e1b000 r--s 00000000 03:41 26968129   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b4e1b000-b4e1c000 r--s 00000000 03:41 26975044   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b4e1c000-b4e1d000 r--s 00000000 03:41 26975043   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b4e1d000-b4e1f000 r--s 00000000 03:41 26968124   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b4e1f000-b4e23000 r--s 00000000 03:41 26974559   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b4e23000-b4e29000 r--s 00000000 03:41 26968118   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b4e29000-b4e32000 r--s 00000000 03:41 26975041   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b4e32000-b4e36000 r--s 00000000 03:41 26975039   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b4e36000-b4e3a000 r-xp 00000000 03:41 23068722   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b4e3a000-b4e3b000 rw-p 00003000 03:41 23068722   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b4e3c000-b5116000 r--p 00000000 03:41 23384801   /usr/share/icons/hicolor/icon-theme.cache
b5116000-b6216000 r--p 00000000 03:41 23481533   /usr/share/icons/crystalsvg/icon-theme.cache
b6216000-b68bf000 r--p 00000000 03:41 23384803   /usr/share/icons/gnome/icon-theme.cache
b68bf000-b6b16000 r--p 00000000 03:41 23383096   /usr/share/icons/Tango/icon-theme.cache
b6b16000-b6bb7000 r--p 00000000 03:41 23381899   /usr/share/icons/Tangerine/icon-theme.cache
b6bb7000-b6d1d000 r--p 00000000 03:41 23380353   /usr/share/icons/Human/icon-theme.cache
b6d1d000-b6d2f000 r-xp 00000000 03:41 23068702   /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b6d2f000-b6d30000 rw-p 00011000 03:41 23068702   /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b6d30000-b6d90000 rw-s 00000000 00:08 23756803   /SYSV00000000 (deleted)
b6d90000-b6d97000 r-xp 00000000 03:41 23004861   /usr/lib/libfam.so.0.0.0
b6d97000-b6d98000 rw-p 00006000 03:41 23004861   /usr/lib/libfam.so.0.0.0
b6d98000-b6d9e000 r-xp 00000000 03:41 22609947   /lib/libacl.so.1.1.0
b6d9e000-b6d9f000 rw-p 00005000 03:41 22609947   /lib/libacl.so.1.1.0
b6d9f000-b6da2000 r-xp 00000000 03:41 22609951   /lib/libattr.so.1.1.0
b6da2000-b6da3000 rw-p 00002000 03:41 22609951   /lib/libattr.so.1.1.0
b6da4000-b6da6000 r--s 00000000 03:41 26974558   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6da6000-b6da8000 r--s 00000000 03:41 26974557   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6da8000-b6daf000 r--s 00000000 03:41 26970338   /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6daf000-b6db4000 r-xp 00000000 03:41 23068718   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b6db4000-b6db5000 rw-p 00004000 03:41 23068718   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b6db5000-b6dc1000 r-xp 00000000 03:41 23007199   /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6dc1000-b6dc2000 rw-p 0000b000 03:41 23007199   /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6dc2000-b6dc3000 r-xp 00000000 03:41 23006788   /usr/lib/gconv/ISO8859-1.so
b6dc3000-b6dc5000 rw-p 00000000 03:41 23006788   /usr/lib/gconv/ISO8859-1.so
b6dc5000-b6e00000 r--p 00000000 03:41 23069693   /usr/lib/locale/en_US.utf8/LC_CTYPE
b6e00000-b6ed7000 r--p 00000000 03:41 23069692   /usr/lib/locale/en_US.utf8/LC_COLLATE
b6ed7000-b6ee0000 r-xp 00000000 03:41 22613237   /lib/tls/i686/cmov/libnss_files-2.5.so
b6ee0000-b6ee2000 rw-p 00008000 03:41 22613237   /lib/tls/i686/cmov/libnss_files-2.5.so
b6ee2000-b6eea000 r-xp 00000000 03:41 22613241   /lib/tls/i686/cmov/libnss_nis-2.5.so
b6eea000-b6eec000 rw-p 00007000 03:41 22613241   /lib/tls/i686/cmov/libnss_nis-2.5.so
b6eec000-b6ef3000 r-xp 00000000 03:41 22613233   /lib/tls/i686/cmov/libnss_compat-2.5.so
b6ef3000-b6ef5000 rw-p 00006000 03:41 22613233   /lib/tls/i686/cmov/libnss_compat-2.5.so
b6ef5000-b6ef8000 rw-p b6ef5000 00:00 0 
b6ef8000-b6f2e000 r-xp 00000000 03:41 22610038   /lib/libsepol.so.1
b6f2e000-b6f2f000 rw-p 00035000 03:41 22610038   /lib/libsepol.so.1
b6f2f000-b6f39000 rw-p b6f2f000 00:00 0 
b6f39000-b6f3c000 r-xp 00000000 03:41 23005014   /usr/lib/libgpg-error.so.0.3.0
b6f3c000-b6f3d000 rw-p 00002000 03:41 23005014   /usr/lib/libgpg-error.so.0.3.0
b6f3d000-b6f8c000 r-xp 00000000 03:41 23004902   /usr/lib/libgcrypt.so.11.2.2
b6f8c000-b6f8e000 rw-p 0004e000 03:41 23004902   /usr/lib/libgcrypt.so.11.2.2
b6f8e000-b6f8f000 rw-p b6f8e000 00:00 0 
b6f8f000-b6fa3000 r-xp 00000000 03:41 23005358   /usr/lib/libtasn1.so.3.0.6
b6fa3000-b6fa4000 rw-p 00013000 03:41 23005358   /usr/lib/libtasn1.so.3.0.6
b6fa4000-b6fa6000 r-xp 00000000 03:41 22613254   /lib/tls/i686/cmov/libutil-2.5.so
b6fa6000-b6fa8000 rw-p 00001000 03:41 22613254   /lib/tls/i686/cmov/libutil-2.5.so
b6fa8000-b6fbc000 r-xp 00000000 03:41 22610037   /lib/libselinux.so.1
b6fbc000-b6fbe000 rw-p 00013000 03:41 22610037   /lib/libselinux.so.1
b6fbe000-b6fcd000 r-xp 00000000 03:41 22613248   /lib/tls/i686/cmov/libresolv-2.5.so
b6fcd000-b6fcf000 rw-p 0000f000 03:41 22613248   /lib/tls/i686/cmov/libresolv-2.5.so
b6fcf000-b6fd1000 rw-p b6fcf000 00:00 0 
b6fd1000-b6fdf000 r-xp 00000000 03:41 23004740   /usr/lib/libavahi-client.so.3.2.2
b6fdf000-b6fe0000 rw-p 0000e000 03:41 23004740   /usr/lib/libavahi-client.so.3.2.2
b6fe0000-b6fe1000 rw-p b6fe0000 00:00 0 
b6fe1000-b6feb000 r-xp 00000000 03:41 23004742   /usr/lib/libavahi-common.so.3.4.3
b6feb000-b6fec000 rw-p 00009000 03:41 23004742   /usr/lib/libavahi-common.so.3.4.3
b6fec000-b6fee000 r-xp 00000000 03:41 23004746   /usr/lib/libavahi-glib.so.1.0.1
b6fee000-b6fef000 rw-p 00001000 03:41 23004746   /usr/lib/libavahi-glib.so.1.0.1
b6fef000-b7059000 r-xp 00000000 03:41 23005010   /usr/lib/libgnutls.so.13.0.9
b7059000-b705f000 rw-p 0006a000 03:41 23005010   /usr/lib/libgnutls.so.13.0.9
b705f000-b7081000 r-xp 00000000 03:41 23005270   /usr/lib/libpng12.so.0.15.0
b7081000-b7082000 rw-p 00021000 03:41 23005270   /usr/lib/libpng12.so.0.15.0
b7082000-b70a0000 r-xp 00000000 03:41 23004857   /usr/lib/libexpat.so.1.0.0
b70a0000-b70a2000 rw-p 0001d000 03:41 23004857   /usr/lib/libexpat.so.1.0.0
b70a2000-b70a3000 rw-p b70a2000 00:00 0 
b70a3000-b710b000 r-xp 00000000 03:41 23004873   /usr/lib/libfreetype.so.6.3.10
b710b000-b710e000 rw-p 00068000 03:41 23004873   /usr/lib/libfreetype.so.6.3.10
b710e000-b7121000 r-xp 00000000 03:41 23005416   /usr/lib/libz.so.1.2.3
b7121000-b7122000 rw-p 00012000 03:41 23005416   /usr/lib/libz.so.1.2.3
b7122000-b7135000 r-xp 00000000 03:41 22613231   /lib/tls/i686/cmov/libnsl-2.5.so
b7135000-b7137000 rw-p 00012000 03:41 22613231   /lib/tls/i686/cmov/libnsl-2.5.so
b7137000-b7139000 rw-p b7137000 00:00 0 
b7139000-b713d000 r-xp 00000000 03:41 23004647   /usr/lib/libORBitCosNaming-2.so.0.1.0
b713d000-b713e000 rw-p 00003000 03:41 23004647   /usr/lib/libORBitCosNaming-2.so.0.1.0
b713e000-b713f000 rw-p b713e000 00:00 0 
b713f000-b7143000 r-xp 00000000 03:41 23004672   /usr/lib/libXdmcp.so.6.0.0
b7143000-b7144000 rw-p 00003000 03:41 23004672   /usr/lib/libXdmcp.so.6.0.0
b7144000-b7162000 r-xp 00000000 03:41 23005139   /usr/lib/libjpeg.so.62.0.0
b7162000-b7163000 rw-p 0001d000 03:41 23005139   /usr/lib/libjpeg.so.62.0.0
b7163000-b716b000 r-xp 00000000 03:41 23005348   /usr/lib/libstartup-notification-1.so.0.0.0
b716b000-b716c000 rw-p 00007000 03:41 23005348   /usr/lib/libstartup-notification-1.so.0.0.0
b716c000-b716d000 rw-p b716c000 00:00 0 
b716d000-b7174000 r-xp 00000000 03:41 22613250   /lib/tls/i686/cmov/librt-2.5.so
b7174000-b7176000 rw-p 00006000 03:41 22613250   /lib/tls/i686/cmov/librt-2.5.so
b7176000-b717a000 r-xp 00000000 03:41 23005066   /usr/lib/libgthread-2.0.so.0.1200.11
b717a000-b717b000 rw-p 00003000 03:41 23005066   /usr/lib/libgthread-2.0.so.0.1200.11
b717b000-b717d000 r-xp 00000000 03:41 22613226   /lib/tls/i686/cmov/libdl-2.5.so
b717d000-b717f000 rw-p 00001000 03:41 22613226   /lib/tls/i686/cmov/libdl-2.5.so
b717f000-b7181000 r-xp 00000000 03:41 23004968   /usr/lib/libgmodule-2.0.so.0.1200.11
b7181000-b7182000 rw-p 00002000 03:41 23004968   /usr/lib/libgmodule-2.0.so.0.1200.11
b7182000-b71d8000 r-xp 00000000 03:41 23005002   /usr/lib/libgnomevfs-2.so.0.1800.1
b71d8000-b71db000 rw-p 00055000 03:41 23005002   /usr/lib/libgnomevfs-2.so.0.1800.1
b71db000-b7249000 r-xp 00000000 03:41 23004765   /usr/lib/libcairo.so.2.11.1
b7249000-b724b000 rw-p 0006d000 03:41 23004765   /usr/lib/libcairo.so.2.11.1
b724b000-b724c000 rw-p b724b000 00:00 0 
b724c000-b7250000 r-xp 00000000 03:41 23004678   /usr/lib/libXfixes.so.3.1.0
b7250000-b7251000 rw-p 00003000 03:41 23004678   /usr/lib/libXfixes.so.3.1.0
b7251000-b7259000 r-xp 00000000 03:41 23004668   /usr/lib/libXcursor.so.1.0.2
b7259000-b725a000 rw-p 00007000 03:41 23004668   /usr/lib/libXcursor.so.1.0.2
b725a000-b7261000 r-xp 00000000 03:41 23004684   /usr/lib/libXi.so.6.0.0
b7261000-b7262000 rw-p 00006000 03:41 23004684   /usr/lib/libXi.so.6.0.0
b7262000-b7264000 r-xp 00000000 03:41 23004686   /usr/lib/libXinerama.so.1.0.0
b7264000-b7265000 rw-p 00001000 03:41 23004686   /usr/lib/libXinerama.so.1.0.0
b7265000-b726c000 r-xp 00000000 03:41 23004698   /usr/lib/libXrender.so.1.3.0
b726c000-b726d000 rw-p 00006000 03:41 23004698   /usr/lib/libXrender.so.1.3.0
b726d000-b727a000 r-xp 00000000 03:41 23004676   /usr/lib/libXext.so.6.4.0
b727a000-b727b000 rw-p 0000d000 03:41 23004676   /usr/lib/libXext.so.6.4.0
b727b000-b727c000 rw-p b727b000 00:00 0 
b727c000-b729f000 r-xp 00000000 03:41 23004863   /usr/lib/libfontconfig.so.1.2.0
b729f000-b72a7000 rw-p 00023000 03:41 23004863   /usr/lib/libfontconfig.so.1.2.0
b72a7000-b72ae000 r-xp 00000000 03:41 23005247   /usr/lib/libpangocairo-1.0.so.0.1600.2
b72ae000-b72af000 rw-p 00007000 03:41 23005247   /usr/lib/libpangocairo-1.0.so.0.1600.2
b72af000-b72d9000 r-xp 00000000 03:41 23005249   /usr/lib/libpangoft2-1.0.so.0.1600.2
b72d9000-b72da000 rw-p 0002a000 03:41 23005249   /usr/lib/libpangoft2-1.0.so.0.1600.2
b72da000-b72ee000 r-xp 00000000 03:41 23004724   /usr/lib/libart_lgpl_2.so.2.3.17
b72ee000-b72ef000 rw-p 00013000 03:41 23004724   /usr/lib/libart_lgpl_2.so.2.3.17
b72ef000-b72f6000 r-xp 00000000 03:41 22610027   /lib/libpopt.so.0.0.0
b72f6000-b72f7000 rw-p 00006000 03:41 22610027   /lib/libpopt.so.0.0.0
b72f7000-b7320000 r-xp 00000000 03:41 23004984   /usr/lib/libgnomecanvas-2.so.0.1400.0
b7320000-b7321000 rw-p 00029000 03:41 23004984   /usr/lib/libgnomecanvas-2.so.0.1400.0
b7321000-b7322000 rw-p b7321000 00:00 0 
b7322000-b737d000 r-xp 00000000 03:41 23004761   /usr/lib/libbonoboui-2.so.0.0.0
b737d000-b7380000 rw-p 0005a000 03:41 23004761   /usr/lib/libbonoboui-2.so.0.0.0
b7380000-b7497000 r-xp 00000000 03:41 23005410   /usr/lib/libxml2.so.2.6.27
b7497000-b749d000 rw-p 00116000 03:41 23005410   /usr/lib/libxml2.so.2.6.27
b749d000-b755d000 r-xp 00000000 03:41 23004726   /usr/lib/libasound.so.2.0.0
b755d000-b7562000 rw-p 000bf000 03:41 23004726   /usr/lib/libasound.so.2.0.0
b7562000-b7587000 r-xp 00000000 03:41 22613228   /lib/tls/i686/cmov/libm-2.5.so
b7587000-b7589000 rw-p 00024000 03:41 22613228   /lib/tls/i686/cmov/libm-2.5.so
b7589000-b75a9000 r-xp 00000000 03:41 23004738   /usr/lib/libaudiofile.so.0.0.2
b75a9000-b75ab000 rw-p 00020000 03:41 23004738   /usr/lib/libaudiofile.so.0.0.2
b75ab000-b76e6000 r-xp 00000000 03:41 22613220   /lib/tls/i686/cmov/libc-2.5.so
b76e6000-b76e7000 r--p 0013b000 03:41 22613220   /lib/tls/i686/cmov/libc-2.5.so
b76e7000-b76e9000 rw-p 0013c000 03:41 22613220   /lib/tls/i686/cmov/libc-2.5.so
b76e9000-b76ed000 rw-p b76e9000 00:00 0 
b76ed000-b76f4000 r-xp 00000000 03:41 22610058   /lib/libwrap.so.0.7.6
b76f4000-b76f5000 rw-p 00007000 03:41 22610058   /lib/libwrap.so.0.7.6
b76f5000-b7789000 r-xp 00000000 03:41 23004958   /usr/lib/libglib-2.0.so.0.1200.11
b7789000-b778a000 rw-p 00093000 03:41 23004958   /usr/lib/libglib-2.0.so.0.1200.11
b778a000-b7796000 r-xp 00000000 03:41 23004974   /usr/lib/libgnome-keyring.so.0.0.1
b7796000-b7797000 rw-p 0000b000 03:41 23004974   /usr/lib/libgnome-keyring.so.0.0.1
b7797000-b77d0000 r-xp 00000000 03:41 23005012   /usr/lib/libgobject-2.0.so.0.1200.11
b77d0000-b77d1000 rw-p 00039000 03:41 23005012   /usr/lib/libgobject-2.0.so.0.1200.11
b77d1000-b7802000 r-xp 00000000 03:41 23004799   /usr/lib/libdbus-1.so.3.2.0
b7802000-b7803000 rw-p 00031000 03:41 23004799   /usr/lib/libdbus-1.so.3.2.0
b7803000-b781d000 r-xp 00000000 03:41 23004801   /usr/lib/libdbus-glib-1.so.2.1.0
b781d000-b781e000 rw-p 0001a000 03:41 23004801   /usr/lib/libdbus-glib-1.so.2.1.0
b781e000-b781f000 rw-p b781e000 00:00 0 
b781f000-b7832000 r-xp 00000000 03:41 22613246   /lib/tls/i686/cmov/libpthread-2.5.so
b7832000-b7834000 rw-p 00013000 03:41 22613246   /lib/tls/i686/cmov/libpthread-2.5.so
b7834000-b7836000 rw-p b7834000 00:00 0 
b7836000-b787f000 r-xp 00000000 03:41 23004643   /usr/lib/libORBit-2.so.0.1.0
b787f000-b7889000 rw-p 00048000 03:41 23004643   /usr/lib/libORBit-2.so.0.1.0
b7889000-b78b8000 r-xp 00000000 03:41 23004900   /usr/lib/libgconf-2.so.4.1.2
b78b8000-b78bb000 rw-p 0002e000 03:41 23004900   /usr/lib/libgconf-2.so.4.1.2
b78bb000-b78ce000 r-xp 00000000 03:41 23004759   /usr/lib/libbonobo-activation.so.4.0.0
b78ce000-b78d0000 rw-p 00013000 03:41 23004759   /usr/lib/libbonobo-activation.so.4.0.0
b78d0000-b7922000 r-xp 00000000 03:41 23004757   /usr/lib/libbonobo-2.so.0.0.0
b7922000-b792c000 rw-p 00051000 03:41 23004757   /usr/lib/libbonobo-2.so.0.0.0
b792c000-b792d000 rw-p b792c000 00:00 0 
b792d000-b7a1a000 r-xp 00000000 03:41 23004655   /usr/lib/libX11.so.6.2.0
b7a1a000-b7a1e000 rw-p 000ed000 03:41 23004655   /usr/lib/libX11.so.6.2.0
b7a1e000-b7a5a000 r-xp 00000000 03:41 23005245   /usr/lib/libpango-1.0.so.0.1600.2
b7a5a000-b7a5c000 rw-p 0003b000 03:41 23005245   /usr/lib/libpango-1.0.so.0.1600.2
b7a5c000-b7a61000 r-xp 00000000 03:41 23004696   /usr/lib/libXrandr.so.2.1.0
b7a61000-b7a62000 rw-p 00005000 03:41 23004696   /usr/lib/libXrandr.so.2.1.0
b7a62000-b7a78000 r-xp 00000000 03:41 23004922   /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a78000-b7a79000 rw-p 00015000 03:41 23004922   /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a79000-b7a92000 r-xp 00000000 03:41 23004732   /usr/lib/libatk-1.0.so.0.1809.1
b7a92000-b7a94000 rw-p 00018000 03:41 23004732   /usr/lib/libatk-1.0.so.0.1809.1
b7a94000-b7b17000 r-xp 00000000 03:41 23004920   /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b17000-b7b1a000 rw-p 00083000 03:41 23004920   /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b1a000-b7b1b000 rw-p b7b1a000 00:00 0 
b7b1b000-b7e6c000 r-xp 00000000 03:41 23005069   /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e6c000-b7e72000 rw-p 00351000 03:41 23005069   /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e72000-b7e73000 rw-p b7e72000 00:00 0 
b7e73000-b7e87000 r-xp 00000000 03:41 23004970   /usr/lib/libgnome-2.so.0.1800.0
b7e87000-b7e88000 rw-p 00014000 03:41 23004970   /usr/lib/libgnome-2.so.0.1800.0
b7e88000-b7e9d000 r-xp 00000000 03:41 23004633   /usr/lib/libICE.so.6.3.0
b7e9d000-b7e9f000 rw-p 00014000 03:41 23004633   /usr/lib/libICE.so.6.3.0
b7e9f000-b7ea0000 rw-p b7e9f000 00:00 0 
b7ea0000-b7ea8000 r-xp 00000000 03:41 23004651   /usr/lib/libSM.so.6.0.0
b7ea8000-b7ea9000 rw-p 00007000 03:41 23004651   /usr/lib/libSM.so.6.0.0
b7ea9000-b7f33000 r-xp 00000000 03:41 23005000   /usr/lib/libgnomeui-2.so.0.1788.4
b7f33000-b7f37000 rw-p 00089000 03:41 23005000   /usr/lib/libgnomeui-2.so.0.1788.4
b7f37000-b7f4b000 r-xp 00000000 03:41 23004972   /usr/lib/libgnome-desktop-2.so.2.3.5
b7f4b000-b7f4c000 rw-p 00014000 03:41 23004972   /usr/lib/libgnome-desktop-2.so.2.3.5
b7f4c000-b7f4d000 rw-p b7f4c000 00:00 0 
b7f4d000-b7f56000 r-xp 00000000 03:41 23004848   /usr/lib/libesd.so.0.2.36
b7f56000-b7f57000 rw-p 00009000 03:41 23004848   /usr/lib/libesd.so.0.2.36
b7f57000-b7f59000 r-xp 00000000 03:41 23004661   /usr/lib/libXau.so.6.0.0
b7f59000-b7f5a000 rw-p 00001000 03:41 23004661   /usr/lib/libXau.so.6.0.0
b7f5a000-b7f5b000 r--s 00000000 03:41 26975042   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7f5b000-b7f5c000 r--p 00000000 03:41 23069698   /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7f5c000-b7f5d000 r--p 00000000 03:41 23069701   /usr/lib/locale/en_US.utf8/LC_TIME
b7f5d000-b7f5e000 r--p 00000000 03:41 23069696   /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f5e000-b7f5f000 r--p 00000000 03:41 23069702   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f5f000-b7f60000 r--p 00000000 03:41 23069699   /usr/lib/locale/en_US.utf8/LC_PAPER
b7f60000-b7f61000 r--p 00000000 03:41 23069697   /usr/lib/locale/en_US.utf8/LC_NAME
b7f61000-b7f62000 r--p 00000000 03:41 23069691   /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f62000-b7f63000 r--p 00000000 03:41 23069700   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f63000-b7f64000 r--p 00000000 03:41 23069695   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f64000-b7f6b000 r--s 00000000 03:41 23006841   /usr/lib/gconv/gconv-modules.cache
b7f6b000-b7f6c000 r--p 00000000 03:41 23069694   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f6c000-b7f6e000 rw-p b7f6c000 00:00 0 
b7f6e000-b7f87000 r-xp 00000000 03:41 22609941   /lib/ld-2.5.so
b7f87000-b7f89000 rw-p 00019000 03:41 22609941   /lib/ld-2.5.so
bff53000-bff69000 rw-p bff53000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

(update-notifier:27551): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
```

oh and i am unable to loginto any kind of session for this account with out getting this error, but as long as i dont click ok, i am able to stay in that account

---

### Post by Ek0nomik on 2007-05-29
It's not this error is it?

[http://ubuntuforums.org/showthread.php?t=278222](http://ubuntuforums.org/showthread.php?t=278222)

Please let me know.

---

### Post by k33bz on 2007-05-29
ya it is that error, this is the second time i have come across this error, actually 3rd time, had it with my main account before so i changed the name of Xsession to Xsession.bak, which worked, but i cant find that file, and i have deleted the xsession-error before, and it just did it again.

---

### Post by zvacet on 2007-05-30
[https://help.ubuntu.com/community/AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")

---

### Post by k33bz on 2007-05-30
> **zvacet said:**
> [https://help.ubuntu.com/community/AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")

ya i know how to add a user, that isnt my problem, this is the 2nd time i tried to install a 3rd account on my computer. the main account, and my second account work fine, it is my 3rd account i am having issues with.

---

### Post by k33bz on 2007-05-30
anybody??
and please read first post in this thread

---

