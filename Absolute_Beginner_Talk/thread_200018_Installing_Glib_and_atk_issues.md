---
title: "Installing Glib and atk issues"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by gomezj00 on 2006-06-19
Hi,

I need a little help.  I installed glib using the following while in the extracted glib directory:
./configure --prefix=/media/firelite/gtk
make
rm -rf /install-prefix...
make install

I got no errors and the directory was built under gtk.
Then I tried to install atk while in the extracted atk directory using the following:
./configure --prefix=/media/firelite/gtk
make

Then make failed and spat out the following info:
make[2]: Entering directory '/media/firelite/atk-1.10.3/atk'
../media/firelite/gtk/gobject/glib-genmarshal --prefix=at_marshal ./atkmarshal.list --header
     && (cmp -s xgen-gmh atkmarshal.h || cp xgen-gmh atkmarshal.h) \
     && rm -f xgen-gmh xgen-gmh~
     && echo timestamp > stamp-atkmarshal.h
/bin/sh: ..//media/firelite/gtk/gobject/glib-genmarshal: No such file or directory

However, I have the glib-genmarshal file in the location it appears to be searching.  I also have my PKG_CONFIG_PATH=/media/firelite/gtk.

Any ideas?  I could really use the help.  Thanks so much.
 ](*,)

---

