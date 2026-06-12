---
title: "Can't run Scid"
date: 2006-03-04
forum: Bug Reports / Support
---

### Post by viriathus on 2006-03-04
I can't run scid.

Package: scid
Priority: optional
Section: universe/games
Installed-Size: 5976
Maintainer: Peter van Rossum <petervr@debian.org>
Architecture: i386
Version: 3.6.1-1build1
Depends: libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.0-7), libstdc++6 (>= 4.0.0-9), libx11-6, tcl8.4 (>= 8.4.5), tk8.4 (>= 8.4.5), zlib1g (>= 1:1.2.1), python
Suggests: tex-chess
Filename: pool/universe/s/scid/scid_3.6.1-1build1_i386.deb
Size: 1797366
MD5sum: c229f59c83d9c52bcff8d7db7cf21b75

Error:

Application initialization failed: this isn't a Tk applicationunknown color name "Black"
Error in startup script: invalid command name "sc_info"
    while executing
"sc_info version"
    (file "/usr/bin/scid" line 1)

My system is:

Ubuntu Dapper, Linux 2.6.15-14-686
tcl8.3                                    8.3.5-5
tcl8.4                                    8.4.12-0ubuntu1
tk8.3                                     8.3.5-4ubuntu1
tk8.4                                     8.4.12-0ubuntu1

---

### Post by viriathus on 2006-03-04
mmm, with xserver-xgl not run, but with xorg yes. I think that xserver-xgl dont load rgb.txt

---

### Post by MischaTuffield on 2006-05-09
Well, i am having a similar problem. I get the error when i attempt to use amsn. I dont have this problem when i am using my normal xorg setup, but when using Xgl i get the following error:

Application initialization failed: this isn't a Tk applicationunknown color name "Black"
Error in startup script: this isn't a Tk applicationunknown color name "Black"
    (default value for "-highlightcolor" in widget ".")

You can have a look at this page, it may help you. The solution doesnt help me , for their proposed link_name is where my rgb.txt file is.

[http://www.ubuntuforums.org/showthread.php?t=133427&page=10](http://www.ubuntuforums.org/showthread.php?t=133427&page=10)

I hope this helps ...

---

