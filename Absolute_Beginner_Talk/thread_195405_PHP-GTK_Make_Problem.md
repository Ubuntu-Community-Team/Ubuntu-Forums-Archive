---
title: "PHP-GTK Make Problem"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by camRW on 2006-06-12
After an hour of successfully finding and solving my own problems (of trying to build PHP-GTK from source) I run make and get this:
cam@ubuntu:~/php-gtk$ sudo make
/bin/sh /home/cam/php-gtk/libtool --mode=compile gcc gen_spaned.c -I./ext/spaned/ -I/home/cam/php-gtk/./ext/spaned/ -DPHP_ATOM_INC -I/home/cam/php-gtk/include -I/home/cam/php-gtk/main -I/home/cam/php-gtk -I/usr/include/php4 -I/usr/include/php4/main -I/usr/include/php4/TSRM -I/usr/include/php4/Zend -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/gnome-xml -I/usr/include/libglade-1.0  -DHAVE_CONFIG_H  -g -O2   -c /home/cam/php-gtk/./ext/spaned/php_spaned.c -o ./ext/spaned/php_spaned.lo
 gcc gen_spaned.c -I./ext/spaned/ -I/home/cam/php-gtk/./ext/spaned/ -DPHP_ATOM_INC -I/home/cam/php-gtk/include -I/home/cam/php-gtk/main -I/home/cam/php-gtk -I/usr/include/php4 -I/usr/include/php4/main -I/usr/include/php4/TSRM -I/usr/include/php4/Zend -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/gnome-xml -I/usr/include/libglade-1.0 -DHAVE_CONFIG_H -g -O2 -c /home/cam/php-gtk/./ext/spaned/php_spaned.c  -fPIC -DPIC -o ./ext/spaned/.libs/php_spaned.o
gcc: gen_spaned.c: No such file or directory
make: *** [ext/spaned/php_spaned.lo] Error 1


Any ideas?

---

### Post by chrispaz on 2007-01-29
Hi Friens,

I had the same ##%$#@ problem, actually I had almost 3 days trying to solve this but nothig, please tell if you solve the problem, and how??


Thanks.

---

