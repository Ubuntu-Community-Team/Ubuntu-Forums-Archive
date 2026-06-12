---
title: "Using Bitwise IM, Help Please"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by timr92 on 2008-03-09
Hi, I'm trying to use BitWise IM on my laptop running Ubuntu 7.10.

I downloaded and extracted it to my desktop, but it wont work... Nor does the BitWise Routing Server.

When i try and go to preferences in the Routing Server while running from a terminal, it gives me this:
```
*** glibc detected *** ./BitWiseRoutingServer: double free or corruption (out): 0x084c8db0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76f6d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb76fa800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7952961]
./BitWiseRoutingServer[0x80c0fa8]
./BitWiseRoutingServer[0x80c1496]
./BitWiseRoutingServer[0x80632e5]
./BitWiseRoutingServer[0x806f677]
./BitWiseRoutingServer[0x8069da4]
./BitWiseRoutingServer[0x81b9d78]
./BitWiseRoutingServer[0x8233e18]
./BitWiseRoutingServer[0x823339c]
./BitWiseRoutingServer[0x8233f9d]
./BitWiseRoutingServer[0x80c99dc]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb7a11c09]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb7a04772]
/usr/lib/libgobject-2.0.so.0[0xb7a15323]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb7a16847]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb7a16a09]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_activate+0x58)[0xb7deafe8]
/usr/lib/libgtk-x11-2.0.so.0(gtk_menu_shell_activate_item+0x14a)[0xb7cd538a]
/usr/lib/libgtk-x11-2.0.so.0[0xb7cd6f28]
/usr/lib/libgtk-x11-2.0.so.0[0xb7cce178]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7cc81de]
/usr/lib/libgobject-2.0.so.0[0xb7a02f89]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb7a04772]
/usr/lib/libgobject-2.0.so.0[0xb7a15973]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb7a1660f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb7a16a09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7de6498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0x14f)[0xb7cc136f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x307)[0xb7cc2587]
/usr/lib/libgdk-x11-2.0.so.0[0xb7b2db9a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb794b11c]
/usr/lib/libglib-2.0.so.0[0xb794e55f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb794e909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7cc29e4]
./BitWiseRoutingServer[0x814dc79]
./BitWiseRoutingServer[0x80df9f2]
./BitWiseRoutingServer[0x80dfb2a]
./BitWiseRoutingServer[0x81f01ed]
./BitWiseRoutingServer[0x806600b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb76a3050]
./BitWiseRoutingServer[0x80586a1]
======= Memory map: ========
08048000-082fc000 r-xp 00000000 08:01 5357641    /home/timothy/Desktop/BitWiseRoutingServer/BitWiseRoutingServer
082fc000-08304000 rw-p 002b3000 08:01 5357641    /home/timothy/Desktop/BitWiseRoutingServer/BitWiseRoutingServer
08304000-08569000 rw-p 08304000 00:00 0          [heap]
b5d00000-b5d21000 rw-p b5d00000 00:00 0 
b5d21000-b5e00000 ---p b5d21000 00:00 0 
b5e48000-b5e49000 ---p b5e48000 00:00 0 
b5e49000-b6649000 rw-p b5e49000 00:00 0 
b6649000-b664c000 rw-s 00000000 00:09 3407893    /SYSV00000000 (deleted)
b664c000-b66ac000 rw-s 00000000 00:09 3375123    /SYSV00000000 (deleted)
b66ac000-b670c000 rw-s 00000000 00:09 3342356    /SYSV00000000 (deleted)
b670c000-b6712000 r-xp 00000000 08:01 1000296    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b6712000-b6713000 rw-p 00005000 08:01 1000296    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b6713000-b6937000 r--p 00000000 08:01 1002724    /usr/share/icons/hicolor/icon-theme.cache
b6937000-b7096000 r--p 00000000 08:01 1039024    /usr/share/icons/gnome/icon-theme.cache
b7096000-b7141000 r--p 00000000 08:01 1347002    /usr/share/icons/Tangerine/icon-theme.cache
b7141000-b71cc000 r--p 00000000 08:01 1133083    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b71cc000-b71ce000 r-xp 00000000 08:01 1000223    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b71ce000-b71cf000 rw-p 00001000 08:01 1000223    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b71cf000-b71d3000 r--p 00000000 08:01 934754     /usr/share/locale-langpack/en_AU/LC_MESSAGES/glib20.mo
b71d3000-b71d9000 r--s 00000000 08:01 1165277    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b71d9000-b71dc000 r--s 00000000 08:01 1165262    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b71dc000-b71e00Aborted (core dumped)

```

And this, when running BitWise IM:
```
*** glibc detected *** ./BitWise: double free or corruption (out): 0x08b006d0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb773cd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7740800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7998961]
./BitWise[0x8393cc8]
./BitWise[0x83941b6]
./BitWise[0x8070337]
./BitWise[0x8231fe9]
./BitWise[0x82309a5]
./BitWise[0x806cf61]
./BitWise[0x806e0d1]
./BitWise[0x84d465c]
./BitWise[0x806b8cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb76e9050]
./BitWise[0x805b7a1]
======= Memory map: ========
08048000-088f3000 r-xp 00000000 08:01 5357679    /home/timothy/Desktop/BitWise/BitWise
088f3000-08906000 rw-p 008aa000 08:01 5357679    /home/timothy/Desktop/BitWise/BitWise
08906000-08b5b000 rw-p 08906000 00:00 0          [heap]
b6600000-b6621000 rw-p b6600000 00:00 0 
b6621000-b6700000 ---p b6621000 00:00 0 
b6759000-b697d000 r--p 00000000 08:01 1002724    /usr/share/icons/hicolor/icon-theme.cache
b697d000-b70dc000 r--p 00000000 08:01 1039024    /usr/share/icons/gnome/icon-theme.cache
b70dc000-b7187000 r--p 00000000 08:01 1347002    /usr/share/icons/Tangerine/icon-theme.cache
b7187000-b7212000 r--p 00000000 08:01 1133083    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b7212000-b7214000 r-xp 00000000 08:01 1000223    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b7214000-b7215000 rw-p 00001000 08:01 1000223    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b7215000-b7219000 r--p 00000000 08:01 934754     /usr/share/locale-langpack/en_AU/LC_MESSAGES/glib20.mo
b7219000-b721f000 r--s 00000000 08:01 1165277    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b721f000-b7222000 r--s 00000000 08:01 1165262    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b7222000-b7226000 r--s 00000000 08:01 1165234    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b7226000-b7227000 r--s 00000000 08:01 1165219    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b7227000-b7228000 r--s 00000000 08:01 1165205    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b7228000-b722b000 r--s 00000000 08:01 1165197    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b722b000-b722c000 r--s 00000000 08:01 1165195    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b722c000-b722f000 r--s 00000000 08:01 1165192    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b722f000-b7231000 r--s 00000000 08:01 1165179    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b7231000-b7239000 r--s 00000000 08:01 1165138    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b7239000-b723f000 r--s 00000000 08:01 1165105    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b723f000-b7240000 r--s 00000000 08:01 1164987    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b7240000-b7257000 r--s 00000000 08:01 1164986    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b7257000-b7259000 r--s 00000000 08:01 1164985    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b7259000-b725f000 r--s 00000000 08:01 1164983    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b725f000-b7263000 r--s 00000000 08:01 1164953    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b7263000-b7265000 r--s 00000000 08:01 1164785    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b7265000-b7266000 r--s 00000000 08:01 1165411    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b7266000-b7267000 r--s 00000000 08:01 1165403    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b7267000-b7268000 r--s 00000000 08:01 1165393    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b7268000-b726b000 r--s 00000000 08:01 1165392    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b726b000-b726e000 r--s 00000000 08:01 1165390    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b726e000-b7275000 r--s 00000000 08:01 1165389    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b7275000-b7277000 r--s 00000000 08:01 1165386    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b7277000-b7278000 r--s 00000000 08:01 1165378    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b7278000-b7279000 r--s 00000000 08:01 1165373    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b7279000-b727a000 r--s 00000000 08:01 1165372    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b727a000-b727f000 r--s 00000000 08:01 1165370    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b727f000-b7284000 r--s 00000000 08:01 1165369    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b7284000-b7286000 r--s 00000000 08:01 1165368    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b7286000-b7289000 r--s 00000000 08:01 1165367    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b7289000-b728a000 r--s 00000000 08:01 1165339    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b728a000-b728b000 r--s 00000000 08:01 1165331    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b728b000-b728c000 r--s 00000000 08:01 1165328    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b728c000-b7290000 r--s 00000000 08:01 1165321    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b7290000-b7296000 r--s 00000000 08:01 1165318    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b7296000-b7297000 r--s 00000000 08:01 1165312    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7297000-b729b000 r--s 00000000 08:01 1165310    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b729b000-b729f000 r--s 00000000 08:01 1165304    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b729f000-b72a3000 r--s 00000000 08:01 1165295    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b72a3000-b72c9000 r-xp 00000000 08:01 1039002    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b72c9000-b72ca000 rw-p 00025000 08:01 1039002    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b72ca000-b72d3000 r-xp 00000000 08:01 5898270    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b72d3000-b72d5000 rw-p 00008000 08:01 5898270    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b72d5000-b72dd000 r-xp 00000000 08:01 5898272    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b72dd000-b72df000 rw-Aborted (core dumped)

```

Anyone know whats going on and could help me??

Thanks,
Tim

---

### Post by Redtide on 2008-04-06
Hi Tim, i was wondering if you ever go an answer to this question, and i also wanted to bump this thread, as my friend that got me to try Linux refuses to use a different IM other than bitwise, and my hardware refuses to work with 7.04, which is the last release of ubuntu that bitwise plays with. It works right out of the box with 7.04...but refuses to work no matter what with 7.10. Can someone please help us? I get the exact same errors he does, So i don't feel any need to post them. Something that was updated between 7.04 and 7.10 broke bitwise, and i would really love to know what it is...or a fix for it. thank you in advance.

---

### Post by timr92 on 2008-05-04
ya, i still cant get it to work. see my post on the [bitwise forums]("http://www.bitwiseim.com/phpBB2/viewtopic.php?p=6825#6825")

---

