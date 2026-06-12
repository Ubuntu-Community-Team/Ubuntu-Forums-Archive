---
title: "Anjuta: Auto generate and Build Distribution"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by Daniel Ngu on 2006-04-08
Hi,

I'm kept getting these two red lines of text from _Build->Auto generate_:

[COLOR="Red"]Makefile.am:6: AM_GNU_GETTEXT in `configure.in' but `po' not in SUBDIRS[/COLOR]
[COLOR="Red"]Makefile.am:6: AM_GNU_GETTEXT in `configure.in' but `intl' not in SUBDIRS[/COLOR]

However, _Build->Build All_ completed successfully.

_Build->Execute_ ran successfully as well.

However, _Build->Build Distribution_ gives the following:

[COLOR="RoyalBlue"]configure.in: 78: required file `./ABOUT-NLS' not found[/COLOR]
[COLOR="Red"]Makefile.am:6: AM_GNU_GETTEXT in `configure.in' but `po' not in SUBDIRS[/COLOR]
[COLOR="Red"]Makefile.am:6: AM_GNU_GETTEXT in `configure.in' but `intl' not in SUBDIRS[/COLOR]
[COLOR="RoyalBlue"]automake: Makefile.am: AM_GNU_GETTEXT in `configure.in' but `ALL_LINGUAS' not defined[/COLOR]
[COLOR="RoyalBlue"]make: *** [distdir] Error 1[/COLOR]
Completed ... unsuccessful

Am I missing any packages that might be causing this?

Thanks in advance.

Daniel

---

