---
title: "Help - what do I do now?"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-17
E: The package avidemux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
E: Unable to lock the list directory

I received this message a while after opening Synaptic. I'd earlier tried to install the avidemux but it reported errors that I did not write down. (I had mowever moved 
the avidemux-2.0.24-Suse9.0.i686.rpm and avidemux-2.0.24-Suse9.0.i686.deb files frommy Desktop to a subdirectory.

[B]I am not as concerned about being unable to install avidemux as I am about being unable to load Synaptic.

[/B]

---

### Post by cliff0108 on 2006-04-17
When I moved it back to the desktop and attempted another installation I got the same errors I recall getting when I fiirst attempted the install:

[B]cliff@ubuntu:~/Desktop$ sudo dpkg -i avidemux_2.0.24-2_i386.deb
(Reading database ...
dpkg: serious warning: files list file for package `avidemux' missing, assuming package has no files currently installed.
108983 files and directories currently installed.)
Preparing to replace avidemux 2.0.24-2 (using avidemux_2.0.24-2_i386.deb) ...
Unpacking replacement avidemux ...
dpkg-deb: unexpected end of file in between members in avidemux_2.0.24-2_i386.deb
Segmentation fault[/B]

---

