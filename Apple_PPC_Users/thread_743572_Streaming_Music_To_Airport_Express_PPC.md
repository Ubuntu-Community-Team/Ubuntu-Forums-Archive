---
title: "Streaming Music To Airport Express PPC"
date: 2008-04-02
forum: Apple PPC Users
---

### Post by slacka-vt on 2008-04-02
Hello All

             I have been following a few posts on this topic, namely

[How to stream mp3 to an airport express using only open source ]("http://ubuntuforums.org/showthread.php?t=192806")

It seems the JustePort.exe method will only work on i386 or x86 machines because it is binary.
I have been trying to compile raop_play-0.5.1 for my machine and I keep getting:

```
autumn@ubuntu-ppc64:~/raop_play-0.5.1$ sudo make
for i in rendezvous raop_play aexcl; do make -C $i; done
make[1]: Entering directory `/home/autumn/raop_play-0.5.1/rendezvous'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/autumn/raop_play-0.5.1/rendezvous'
make[1]: Entering directory `/home/autumn/raop_play-0.5.1/raop_play'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/autumn/raop_play-0.5.1/raop_play'
make[1]: Entering directory `/home/autumn/raop_play-0.5.1/aexcl'
gcc -Wall -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I../raop_play -DGLIB_SUBST   -c -o ipod/glibsubst.o ipod/glibsubst.c
ipod/glibsubst.c:36: error: conflicting types for 'g_malloc'
/usr/include/glib-2.0/glib/gmem.h:47: error: previous declaration of 'g_malloc' was here
ipod/glibsubst.c:36: error: conflicting types for 'g_malloc'
/usr/include/glib-2.0/glib/gmem.h:47: error: previous declaration of 'g_malloc' was here
ipod/glibsubst.c:41: error: conflicting types for 'g_malloc0'
/usr/include/glib-2.0/glib/gmem.h:48: error: previous declaration of 'g_malloc0' was here
ipod/glibsubst.c:41: error: conflicting types for 'g_malloc0'
/usr/include/glib-2.0/glib/gmem.h:48: error: previous declaration of 'g_malloc0' was here
make[1]: *** [ipod/glibsubst.o] Error 1
make[1]: Leaving directory `/home/autumn/raop_play-0.5.1/aexcl'
make: *** [all] Error 2

```

I did a little "googleing" and I have found that there maybe a bug in glib-2.0 ?
has anyone had any success streaming music to an Airport Express on Linux PPC ?

Seems kind of ironic as this device was built to be supported on this Architecture.

thx
~s

---

### Post by supergau on 2008-04-22
Following thread helped me:
[http://ubuntuforums.org/archive/index.php/t-192806.html](http://ubuntuforums.org/archive/index.php/t-192806.html)

> I can compile by making this patch to aexcl/ipod/glibsubst.c:

--- ../raop_play-0.5.1-original/aexcl/ipod/glibsubst.c 2005-12-16 06:17:00.000000000 -0800
+++ aexcl/ipod/glibsubst.c 2008-03-24 11:31:24.000000000 -0700
@@ -32,12 +32,12 @@
#include "aexcl_lib.h"


-inline gpointer g_malloc(gulong size)
+inline gpointer g_malloc(gsize size)
{
return malloc(size);
}

-inline gpointer g_malloc0(gulong size)
+inline gpointer g_malloc0(gsize size)
{
gpointer p;
if((p=malloc(size))) memset(p,0,size);

but the bigger problem is that the module still doesn't load.

After this I could start raop_play and aexcl_play, and it worked.
No i'm trying to compile the driver

[http://raop-play.sourceforge.net/alsa_raoppcm.html](http://raop-play.sourceforge.net/alsa_raoppcm.html)

I'm using debian lenny but hope it helps you
think you read the REAMDE supported with the sourcecode?

regards,
gaua

---

### Post by bjerngaard on 2008-05-17
I had the same issue, this fixed it. Thanks! ~Rasmus

---

