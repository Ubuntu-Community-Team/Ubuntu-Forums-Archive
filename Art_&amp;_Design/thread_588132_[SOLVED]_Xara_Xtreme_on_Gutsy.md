---
title: "[SOLVED] Xara Xtreme on Gutsy"
date: 2007-10-23
forum: Art &amp; Design
---

### Post by galvao on 2007-10-23
Greetings.

I have Xara Xtreme, which always worked perfectly on Feisty, but after a clean install of gutsy I can't make it work.

Below is the program's error output when I try running it via shell.

Can anyone shed some light on this?

TIA,

*** glibc detected *** /home/galvao/downloads/xaralx/bin/xaralx: munmap_chunk(): invalid pointer: 0x0a1f1130 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb75b192b]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb77cb961]
/home/galvao/downloads/xaralx/bin/xaralx[0x8c88348]
/home/galvao/downloads/xaralx/bin/xaralx[0x8c88836]
/home/galvao/downloads/xaralx/bin/xaralx[0x808cf69]
/home/galvao/downloads/xaralx/bin/xaralx[0x808f899]
/home/galvao/downloads/xaralx/bin/xaralx[0x8a2a0ea]
/home/galvao/downloads/xaralx/bin/xaralx[0x83f8d59]
/home/galvao/downloads/xaralx/bin/xaralx[0x844a129]
/home/galvao/downloads/xaralx/bin/xaralx[0x8449aa2]
/home/galvao/downloads/xaralx/bin/xaralx[0x8061130]
/home/galvao/downloads/xaralx/bin/xaralx[0x80686c1]
/home/galvao/downloads/xaralx/bin/xaralx[0x8dca0dc]
/home/galvao/downloads/xaralx/bin/xaralx[0x805f4eb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb755a050]
/home/galvao/downloads/xaralx/bin/xaralx[0x805eec1]
======= Memory map: ========
08048000-09351000 r-xp 00000000 08:16 8571365    /home/galvao/downloads/xaralx/bin/xaralx
09351000-09468000 rw-p 01308000 08:16 8571365    /home/galvao/downloads/xaralx/bin/xaralx
09468000-0a494000 rw-p 09468000 00:00 0          [heap]
b5da2000-b5eba000 r-xp 00000000 08:15 1866220    /usr/lib/libxml2.so.2.6.30
b5eba000-b5ebf000 rw-p 00118000 08:15 1866220    /usr/lib/libxml2.so.2.6.30
b5ebf000-b5ec0000 rw-p b5ebf000 00:00 0 
b5ec0000-b5ef2000 r-xp 00000000 08:15 1865570    /usr/lib/libcroco-0.6.so.3.0.1
b5ef2000-b5ef5000 rw-p 00031000 08:15 1865570    /usr/lib/libcroco-0.6.so.3.0.1
b5ef5000-b60fa000 r--p 00000000 08:15 2179960    /usr/share/icons/hicolor/icon-theme.cache
b60fa000-b6859000 r--p 00000000 08:15 2178286    /usr/share/icons/gnome/icon-theme.cache
b6859000-b6904000 r--p 00000000 08:15 2176925    /usr/share/icons/Tangerine/icon-theme.cache
b6904000-b6b20000 r--p 00000000 08:15 2060521    /usr/share/fonts/truetype/unfonts/UnDotum.ttf
b6b49000-b6ba9000 rw-s 00000000 00:09 49872939   /SYSV00000000 (deleted)
b6ba9000-b6d0f000 r--p 00000000 08:15 2175390    /usr/share/icons/Human/icon-theme.cache
b6d0f000-b6ea3000 rw-p b6d0f000 00:00 0 
b6ea3000-b6f2e000 r--p 00000000 08:15 2060480    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6f3e000-b6f6e000 r-xp 00000000 08:15 1865812    /usr/lib/libgsf-1.so.114.0.7
b6f6e000-b6f71000 rw-p 0002f000 08:15 1865812    /usr/lib/libgsf-1.so.114.0.7
b6f71000-b6f72000 rw-p b6f71000 00:00 0 
b6f72000-b6faf000 r--p 00000000 08:15 2060484    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
b6faf000-b6ffa000 r--p 00000000 08:15 2060482    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b7015000-b7045000 r-xp 00000000 08:15 1866110    /usr/lib/librsvg-2.so.2.18.2
b7045000-b7046000 rw-p 00030000 08:15 1866110    /usr/lib/librsvg-2.so.2.18.2
b7046000-b7077000 r--p 00000000 08:15 2060494    /usr/share/fonts/truetype/ttf-indic-fonts-core/Vemana.ttf
b7077000-b709a000 r--p 00000000 08:15 2076773    /usr/share/fonts/type1/gsfonts/n021003l.pfb
b709c000-b70ab000 r-xp 00000000 08:15 245319     /lib/libbz2.so.1.0.4
b70ab000-b70ac000 rw-p 0000f000 08:15 245319     /lib/libbz2.so.1.0.4
b70ac000-b710c000 rw-s 00000000 00:09 49709076   /SYSV00000000 (deleted)
b7120000-b7121000 r-xp 00000000 08:15 1913713    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b7121000-b7122000 rw-p 00000000 08:15 1913713    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b7122000-b7145000 r--p 00000000 08:15 2076722    /usr/share/fonts/type1/gsfonts/b018012l.pfb
b7145000-b7147000 r-xp 00000000 08:15 1979318    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b7147000-b7148000 rw-p 00001000 08:15 1979318    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b7148000-b7155000 r--p 00000000 08:15 2076812    /usr/share/fonts/type1/gsfonts/z003034l.pfb
b7155000-b7162000 r--p 00000000 08:15 2060425    /usr/share/fonts/truetype/thai/TlwgTypewriter.ttf
b7162000-b716e000 r--p 00000000 08:15 2060429    /usr/share/fonts/truetype/thai/TlwgTypist.ttf
b716e000-b7246000 rw-p b716e000 00:00 0 
b7246000-b724c000 r--s 00000000 08:15 1700684    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3efish: Job 1, “/home/galvao/downloads/xaralx/bin/xaralx” terminated by signal SIGABRT (Abort)

---

### Post by Vadi on 2007-10-23
That's weird, it works all okay for me.

Usually a glibc is a bad problem in the program.

What version are you using? 0.7 works fine for me.

---

### Post by galvao on 2007-10-24
Hi. I've downloaded and installed the latest version, but still can't run it. Allow me to add some more information:

When I run it I can see Xara Xtreme's splash screen, but then the following alert box shows up:

"Deleted stale lock file /home/galvao/.XARA-XTREME-WX-xaralx-galvao"

And then I have the error messages I already showed in my first post. Funny thing is that after all of this happen the file remains in my home directory.

I've tried then deleteing it manually, but then I got another alert message saying something like "An extremely serious error occurred, Xara Xtreme must quit now".

Any ideas?

TIA,

---

### Post by Vadi on 2007-10-24
I get that deleted stale lock file msg also, I just ignore it.

What did you download? I didn't know how to use the .package, so I just used the .tar.gz file, extracted it, went into the bin folder, and launched xaralx.

---

### Post by galvao on 2007-10-24
Well, I was downloading always the latest version, 0.7 rev 1783, because I really need all the bug fixes and stuff they are implementing in each version.

I just solved the problem:

* Installed the repo package, using apt-get.
* apt-get suggested me xaralx-svg and imagemagick, which I also installed
* Uninstalled the repo package
* Installed the latest version via autopackage

Maybe it was the lack of imagemagick?

Anyway, thank you all for the help!

Regards,

---

### Post by Vadi on 2007-10-24
There'a a repo package? Never knew. I just got it from their site.

---

### Post by galvao on 2007-10-24
galvao@galvao-desktop ~> sudo apt-cache search xara
xara-gtk - GTK utility for searching the Debian package database
xara-gtk-byte - GTK utility for searching the Debian package database
xaralx - Heavyweight vector graphics, illustration and DTP Program
xaralx-examples - Examples of works created by XaraLx
xaralx-svg - SVG (Scalable Vector Graphics) plugin for XaraLX

:)

---

