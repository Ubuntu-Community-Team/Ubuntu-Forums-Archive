---
title: "glib make install"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by hellohenry on 2006-01-23
hi I posted this in the desktop support but I thought this might be better?

hey can anyone help me - trying to get some programs to run on ubuntu, in particular abc torrent for bittorrent and gtkpod for ipod.
I can configure and make glib (2.8.0) but when I try make install I receive the following error message

/bin/sh ./mkinstalldirs /usr/local/bin
/usr/bin/install -c glib-gettextsize /usr/local/bin/glib-gettextize
/usr/bin/install: cannot create regular file '/usr/local/bin/glib-gettextize': Permission denied
make [3]: *** [install-binSCRIPTS] Error 1
make [3]: Leaving directory '/home/henry/Desktop/glib-2.8.0'

etc.....

that folder /usr/local/bin is empty, and when I check the user 'permissions' it says I can't write there and I can't change it as I am not the Owner.

can you help? thanks!
henry

---

