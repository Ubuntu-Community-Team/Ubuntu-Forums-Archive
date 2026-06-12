---
title: "BRL-CAD tk.h file missing compile error [SOLVED]"
date: 2009-02-12
forum: Art &amp; Design
---

### Post by uboltun on 2009-02-12
When trying to custom compile brl-cad everything went smooth except for some error that bombardier.c can not find tk.h. 
I found a simple fix for this is just to replace in ./src/util/Makefile
line 1645  from this :
DEFAULT_INCLUDES =  -I. -I$(srcdir) -I$(top_builddir)/include

to this:
DEFAULT_INCLUDES =  -I. -I$(srcdir) -I$(top_builddir)/include $(TK_CPPFLAGS)

a violent approach, but worked.
Then just make & make install

---

