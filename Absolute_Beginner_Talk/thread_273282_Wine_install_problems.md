---
title: "Wine install problems"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by lckeeper1 on 2006-10-07
Hey all, I've been trying to install the new version of wine (0.9.22) from the source in order to patch it so I can play WoW. When I get to the "make" step of compilation, I get the following errors:

In file included from ../../include/wine/unicode.h:27,
                 from compose.c:4:
../../include/winbase.h:1307: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[2]: *** [compose.o] Error 1
make[2]: Leaving directory `/home/dan/wine-0.9.22/libs/wine'
make[1]: *** [wine] Error 2
make[1]: Leaving directory `/home/dan/wine-0.9.22/libs'
make: *** [libs] Error 2

I'n not sure how to handle this, and would like to get wine working cuz I think I'm going through WoW withdrawl :p . Thanks in advance.

---

