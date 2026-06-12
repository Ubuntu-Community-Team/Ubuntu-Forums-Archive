---
title: "Pidgin doesn't start."
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by trig on 2008-01-10
Hello, I am new to Ubuntu and I am having a problem with Pidgin. I have spent the last couple days on Google trying to figure this out but I am at a lossWhen I click on the icon it will show me that it is trying to start in the task bar then go away. Any help will be greatful.

Trig

---

### Post by filam on 2008-01-10
could it be minimized to the notification area? does the application load and then disappear? or do you just see a instance in the window list on the gnome panel before that instance disappears?

---

### Post by trig on 2008-01-10
It shows up in the task bar for about 10 seconds then goes away.  You never see anything in the work space itself.
 Thanks,
 Trig

---

### Post by filam on 2008-01-10
does the pidgin icon in the notification area disappear? [the icon that is the combination of the chat bubble and the clock]
is the process still running? [system - administration - system moniter]

---

### Post by trig on 2008-01-10
My wife was able to im me. so it is running some where in the system, but where

---

### Post by filam on 2008-01-10
I imagine that it is simply minimized to the Notification Area. You might not recognize this because most programs minimize to the Window Panel (the "task bar"). The Notification Area is like the system tray in Windows. In your screen shot there are two icons in the Notification Area (to the right of the Window Panel). One represents your network connection (the icon with the two computers), the other is Pidgin. Simply click on the pidgin icon (the icon with a chat bubble and a clock) and it should appear on one of your two workspaces.

---

### Post by trig on 2008-01-10
that was it thank you,
trig

---

### Post by Vanderdan on 2008-06-11
I have a similar problem. It does not show up at the bottom of the screen or in processes.

---

### Post by dje on 2008-06-11
> **Vanderdan said:**
> I have a similar problem. It does not show up at the bottom of the screen or in processes.

open a terminal (applications >> accesories >> terminal) and type:
```
pidgin
```
please post the output here

dje

---

### Post by Vanderdan on 2008-06-11
dns[6895]: Error: Parent requested resolution of an empty hostname (port = 1863)!!!
*** glibc detected *** pidgin: free(): invalid pointer: 0x0000000000e33920 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f5fc699f08a]
/lib/libc.so.6(cfree+0x8c)[0x7f5fc69a2c1c]
/usr/lib/libpurple.so.0(purple_dnsquery_destroy+0x8b)[0x7f5fc78bb538]
/usr/lib/libpurple.so.0[0x7f5fc78ba3b8]
/usr/lib/libpurple.so.0[0x7f5fc78bb264]
pidgin[0x46be51]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f2)[0x7f5fc7161262]
/usr/lib/libglib-2.0.so.0[0x7f5fc7164516]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1b7)[0x7f5fc71647d7]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x7f5fc88a7f03]
pidgin(main+0xac2)[0x486c0a]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7f5fc69491c4]
pidgin[0x42f159]
======= Memory map: ========
00400000-004e8000 r-xp 00000000 07:00 563824                             /usr/bin/pidgin
006e7000-006ed000 rw-p 000e7000 07:00 563824                             /usr/bin/pidgin
006ed000-00e4b000 rw-p 006ed000 00:00 0                                  [heap]
4067f000-40680000 ---p 4067f000 00:00 0 
40680000-40e80000 rw-p 40680000 00:00 0 
7f5fac000000-7f5fac021000 rw-p 7f5fac000000 00:00 0 
7f5fac021000-7f5fb0000000 ---p 7f5fac021000 00:00 0 
7f5fb1240000-7f5fb12a0000 rw-s 00000000 00:09 10747955                   /SYSV00000000 (deleted)
7f5fb12a0000-7f5fb13a4000 rw-p 7f5fb12a0000 00:00 0 
7f5fb13a4000-7f5fb142b000 r--p 00000000 07:00 693736                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
7f5fb142b000-7f5fb1442000 r--s 00000000 07:00 786377                     /var/lib/aspell/en_US-wo_accents-only.rws
7f5fb1442000-7f5fb16ca000 r--s 00000000 07:00 786365                     /var/lib/aspell/en-common.rws
7f5fb16ca000-7f5fb178d000 rw-p 7f5fb16ca000 00:00 0 
7f5fb178d000-7f5fb178f000 r-xp 00000000 07:00 637016                     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f5fb178f000-7f5fb198e000 ---p 00002000 07:00 637016                     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f5fb198e000-7f5fb198f000 rw-p 00001000 07:00 637016                     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f5fb198f000-7f5fb1a20000 r--p 00000000 07:00 693737                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7f5fb1a20000-7f5fb1a2f000 r-xp 00000000 07:00 228517                     /lib/libbz2.so.1.0.4
7f5fb1a2f000-7f5fb1c2e000 ---p 0000f000 07:00 228517                     /lib/libbz2.so.1.0.4
7f5fb1c2e000-7f5fb1c30000 rw-p 0000e000 07:00 228517                     /lib/libbz2.so.1.0.4
7f5fb1c30000-7f5fb1c9e000 r-xp 00000000 07:00 563358                     /usr/lib/libgio-2.0.so.0.0.0
7f5fb1c9e000-7f5fb1e9e000 ---p 0006e000 07:00 563358                     /usr/lib/libgio-2.0.so.0.0.0
7f5fb1e9e000-7f5fb1ea1000 rw-p 0006e000 07:00 563358                     /usr/lib/libgio-2.0.so.0.0.0
7f5fb1ea1000-7f5fb1ed9000 r-xp 00000000 07:00 564513                     /usr/lib/libcroco-0.6.so.3.0.1
7f5fb1ed9000-7f5fb20d8000 ---p 00038000 07:00 564513                     /usr/lib/libcroco-0.6.so.3.0.1
7f5fb20d8000-7f5fb20dc000 rw-p 00037000 07:00 564513                     /usr/lib/libcroco-0.6.so.3.0.1
7f5fb20dc000-7f5fb2113000 r-xp 00000000 07:00 564767                     /usr/lib/libgsf-1.so.114.0.7
7f5fb2113000-7f5fb2312000 ---p 00037000 07:00 564767                     /usr/lib/libgsf-1.so.114.0.7
7f5fb2312000-7f5fb2316000 rw-p 00036000 07:00 564767                     /usr/lib/libgsf-1.so.114.0.7
7f5fb2316000-7f5fb2317000 rw-p 7f5fb2316000 00:00 0 
7f5fb2317000-7f5fb234b000 r-xp 00000000 07:00 565088                     /usr/lib/librsvg-2.so.2.22.2
7f5fb234b000-7f5fb254b000 ---p 00034000 07:00 565088                     /usr/lib/librsvg-2.so.2.22.2
7f5fb254b000-7f5fb254d000 rw-p 00034000 07:00 565088                     /usr/lib/librsvg-2.so.2.22.2
7f5fb254d000-7f5fb254f000 r-xp 00000000 07:00 596116                     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f5fb254f000-7f5fb274e000 ---p 00002000 07:00 596116                     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f5fb274e000-7f5fb274f000 rw-p 00001000 07:00 596116                     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f5fb274f000-7f5fb2753000 r-xp 00000000 07:00 596333                     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f5fb2753000-7f5fb2953000 ---p 00004000 07:00 596333                     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f5fb2953000-7f5fb2954000 rw-p 00004000 07:00 596333                     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f5fb2954000-7f5fb2963000 r-xp 00000000 07:00 596066                     /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
7f5fb2963000-7f5fb2b62000 ---p 0000f000 07:00 596066                     /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
7f5fb2b62000-7f5fb2b63000 rw-p 0000e000 07:00 596066                     /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
7f5fb2b63000-7f5fb2bbc000 r-xp 00000000 07:00 720744                     /usr/lib/nss/libnssckbi.so
7f5fb2bbc000-7f5fb2dbb000 ---p 00059000 07:00 720744                     /usr/lib/nss/libnssckbi.so
7f5fb2dbb000-7f5fb2dd0000 rw-p 00058000 07:00 720744                     /usr/lib/nss/libnssckbi.so
7f5fb2dd0000-7f5fb2e21000 r-xp 00000000 07:00 571762                     /usr/lib/nss/libfreebl3.so
7f5fb2e21000-7f5fb3021000 ---p 00051000 07:00 571762                     /usr/lib/nss/libfreebl3.so
7f5fb3021000-7f5fb3022000 rw-p 00051000 07:00 571762                     /usr/lib/nss/libfreebl3.so
7f5fb3022000-7f5fb305a000 r-xp 00000000 07:00 720742                     /usr/lib/nss/libsoftokn3.so
7f5fb305a000-7f5fb325a000 ---p 00038000 07:00 720742                     /usr/lib/nss/libsoftokn3.so
7f5fb325a000-7f5fb325c000 rw-p 00038000 07:00 720742                     /usr/lib/nss/libsoftokn3.so
7f5fb325c000-7f5fb325e000 r-xp 00000000 07:00 16355                      /usr/lib/purple-2/statenotify.so
7f5fb325e000-7f5fb345d000 ---p 00002000 07:00 16355                      /usr/lib/purple-2/statenotify.so
7f5fb345d000-7f5fb345e000 rw-p 00001000 07:00 16355                      /usr/lib/purple-2/statenotify.so
7f5fb345e000-7f5fb3460000 r-xp 00000000 07:00 16327                      /usr/lib/purple-2/libaim.so
7f5fb3460000-7f5fb365f000 ---p 00002000 07:00 16327                      /usr/lib/purple-2/libaim.so
7f5fb365f000-7f5fb3660000 rw-p 00001000 07:00 16327                      /usr/lib/purple-2/libaim.so
7f5fb3660000-7f5fb3693000 r-xp 00000000 07:00 16341                      /usr/lib/purple-2/libqq.so
7f5fb3693000-7f5fb3893000 ---p 00033000 07:00 16341                      /usr/lib/purple-2/libqq.so
7f5fb3893000-7f5fb3895000 rw-p 00033000 07:00 16341                      /usr/lib/purple-2/libqq.so
7f5fb3895000-7f5fb3897000 r-xp 00000000 07:00 16351                      /usr/lib/purple-2/psychic.so
7f5fb3897000-7f5fb3a96000 ---p 00002000 07:00 16351                      /usr/lib/purple-2/psychic.so
7f5fb3a96000-7f5fb3a97000 rw-p 00001000 07:00 16351                      /usr/lib/purple-2/psychic.so
7f5fb3a97000-7f5fb3aac000 r-xp 00000000 07:00 564625                     /usr/lib/libgadu.so.3.5
7f5fb3aac000-7f5fb3cab000 ---p 00015000 07:00 564625                     /usr/lib/libgadu.so.3.5
7f5fb3cab000-7f5fb3cac000 rw-p 00014000 07:00 564625                     /usr/lib/libgadu.so.3.5
7f5fb3cac000-7f5fb3cb9000 r-xp 00000000 07:00 16329                      /usr/lib/purple-2/libgg.so
7f5fb3cb9000-7f5fb3eb9000 ---p 0000d000 07:00 16329                      /usr/lib/purple-2/libgg.so
7f5fb3eb9000-7f5fb3eba000 rw-p 0000d000 07:00 16329                      /usr/lib/purple-2/libgg.so
7f5fb3eba000-7f5fb3ed1000 r-xp 00000000 07:00 16331                      /usr/lib/purple-2/libirc.so
7f5fb3ed1000-7f5fb40d0000 ---p 00017000 07:00 16331                      /usr/lib/purple-2/libirc.so
7f5fb40d0000-7f5fb40d2000 rw-p 00016000 07:00 16331                      /usr/lib/purple-2/libirc.so
7f5fb40d2000-7f5fb40d4000 r-xp 00000000 07:00 16348                      /usr/lib/purple-2/newline.so
7f5fb40d4000-7f5fb42d3000 ---p 00002000 07:00 16348                      /usr/lib/purple-2/newline.so
7f5fb42d3000-7f5fb42d4000 rw-p 00001000 07:00 16348                      /usr/lib/purple-2/newline.so
7f5fb42d4000-7f5fb4408000 r-xp 00000000 07:00 565029                     /usr/lib/libperl.so.5.8.8
7f5fb4408000-7f5fb4607000 ---p 00134000 07:00 565029                     /usr/lib/libperl.so.5.8.8
7f5fb4607000-7f5fb4610000 rw-p 00133000 07:00 565029                     /usr/lib/libperl.so.5.8.8
7f5fb4610000-7f5fb4612000 rw-p 7f5fb4610000 00:00 0 
7f5fb4612000-7f5fb461f000 r-xp 00000000 07:00 16350                      /usr/lib/purple-2/perl.so
7f5fb461f000-7f5fb481f000 ---p 0000d000 07:00 16350                      /usr/lib/purple-2/perl.so
7f5fb481f000-7f5fb4820000 rw-p 0000d000 07:00 16350                      /usr/lib/purple-2/perl.so
7f5fb4820000-7f5Aborted

---

### Post by dje on 2008-06-11
ok see if this does anything:
```
sudo apt-get --reinstall install pidgin
```

---

### Post by Vanderdan on 2008-06-11
This is what happened.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 572kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main pidgin 1:2.4.1-1ubuntu2 [572kB]
Fetched 572kB in 6s (94.4kB/s)                                                 
(Reading database ... 117583 files and directories currently installed.)
Preparing to replace pidgin 1:2.4.1-1ubuntu2 (using .../pidgin_1%3a2.4.1-1ubuntu2_amd64.deb) ...
Unpacking replacement pidgin ...
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up pidgin (1:2.4.1-1ubuntu2) ...

Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dje on 2008-06-11
ok try:
```
sudo apt-get autoremove --purge msttcorefonts && sudo apt-get --reinstall install pidgin
```

---

### Post by Vanderdan on 2008-06-11
I still get a similar error.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts*
0 upgraded, 0 newly installed, 1 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117582 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--purge):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dje on 2008-06-11
ok try:
```
sudo apt-get install -f
```

---

### Post by Vanderdan on 2008-06-11
Still an error.

---

### Post by dje on 2008-06-11
last thing i can think of:
```
sudo dpkg --configure -a
```
if that doesn't work im afraid i dont know, ive never seen errors like those before

---

### Post by Vanderdan on 2008-06-11
What should happen after I put that in? It went back to another prompt.Thank you for your help anyway. :)

---

### Post by dje on 2008-06-11
That means it probably didn't do anything, try this again to see:
```
sudo apt-get --reinstall install pidgin
```

sorry i cant help any more
dje

---

### Post by Vanderdan on 2008-06-11
I still get the error. I appreciate the help.

---

### Post by dje on 2008-06-11
perhaps try creating a new thread relating to the exact problem your having

good luck!
dje

---

