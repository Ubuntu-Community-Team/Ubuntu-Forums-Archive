---
title: "XChat compiling error."
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by ScotCop on 2006-07-04
Lo all im trying to compile the latest version of XChat but i keep getting this error ive tryed googling and it would seem im long with this problem.

*** Warning: Linking the shared library perl.la against the
*** static library /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a is not portable!
gcc -shared  .libs/perl.o  -L/usr/local/lib /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a -L/usr/lib/perl/5.8/CORE -lperl -lm -lpthread -lcrypt -ldl /usr/lib/libglib-2.0.so  -Wl,-E -Wl,--export-dynamic -Wl,-soname -Wl,perl.so -o .libs/perl.so

/usr/bin/ld: cannot find -lperl
collect2: ld returned 1 exit status
make[4]: *** [perl.la] Error 1
make[4]: Leaving directory `/home/scotcop/xchat-2.6.4/plugins/perl'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/scotcop/xchat-2.6.4/plugins/perl'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/scotcop/xchat-2.6.4/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/scotcop/xchat-2.6.4'
make: *** [all] Error 2
scotcop@area51:~/xchat-2.6.4$

I dont like the gnome version of XChat.

---

### Post by croak77 on 2006-07-04
In case you didn't notice, there are two versions of xchat in the repo's xchat-gnome and xchat.

---

### Post by ScotCop on 2006-07-04
Thanks but one is the older version and ive already said i dont want to use the gnome version so thats not the question.

Any help troubleshooting the error?

---

### Post by croak77 on 2006-07-04
No idea. You can try using a rpm package with alien.

---

