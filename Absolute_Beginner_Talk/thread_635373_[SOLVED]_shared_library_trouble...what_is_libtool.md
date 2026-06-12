---
title: "[SOLVED] shared library trouble...what is libtool?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by lbthrice on 2007-12-08
I resolved the issue below...the shared library was not recognized because of a dependency issue...sorry...learned the lesson: always ready the ./configure output!
see my post [URL="http://ubuntuforums.org/showthread.php?t=640305"]http://ubuntuforums.org/showthread.php?t=640305
[/URL] for the solution.  This is absolute beginner talk, thanks for your patience!



Hi all

I have been trying to get an install of EMBOSS (european molecular biology open software suite) running on my gutsy box.  When I invoke the make install I get a warning that tells me to run libtool --finish /usr/local/lib.

It makes sense that there is something strange going on with the shared libraries because when I attempt to invoke a program it returns an error telling me that one of the shared libraries does not exist...when, in fact, it does.

I ran libtool on the appropriate directory and libtool returns instructions to add LIBTOOL to my LD_LIBRARY_PATH env variable or to LD_RUN_PATH or to add LIBDIR to /etc/ld.so.conf.

I wonder which tact I should take and how I can fix this issue....any ideas all yous ubuntu gurus??

One more thing that may be relevant....I had this thing working on my feisty box prior to a clean install of gutsy...without using LIBTOOL...has something changed?

Thanks guys/girls!

---

