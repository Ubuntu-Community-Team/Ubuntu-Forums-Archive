---
title: "[SOLVED] compiling: cannot find &amp;quot;-lfreetype&amp;quot; error?"
date: 2008-07-07
forum: Arch and derivatives
---

### Post by shearn89 on 2008-07-07
okay, this is driving me frigging bonkers. I'm trying to compile fbsplash/splashutils, and everytime i get this error:

```

Making all in libs
Making all in src
  CREATE  fbsplash.h
Making all in .
daemon_cmd.c: In function ‘cmd_log’:
daemon_cmd.c:346: warning: incompatible implicit declaration of built-in function ‘strndup’
daemon_cmd.c:348: warning: incompatible implicit declaration of built-in function ‘strndup’
/usr/bin/ld: cannot find -lfreetype
collect2: ld returned 1 exit status
make[4]: *** [fbsplashctl] Error 1
make[3]: *** [all-recursive] Error 1
make[2]: *** [all] Error 2
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
==> ERROR: Build Failed.
    Aborting...

```

I have the libfreetype:
```

[/var/abs/local/fbsplash] ls -l /usr/lib/libfree*
-rwxr-xr-x 1 root root 259150 2008-07-06 16:34 /usr/lib/libfreebl3.so
lrwxrwxrwx 1 root root     21 2008-07-06 18:43 /usr/lib/libfreetype.so -> libfreetype.so.6.3.18
lrwxrwxrwx 1 root root     21 2008-07-06 18:43 /usr/lib/libfreetype.so.6 -> libfreetype.so.6.3.18
-rwxr-xr-x 1 root root 595471 2008-07-06 18:43 /usr/lib/libfreetype.so.6.3.18
[/var/abs/local/fbsplash] 

```

and this is the output of "freetype-config" (i read that it might be useful):
```

[/var/abs/local/fbsplash] freetype-config --libs
-lfreetype -lz

```


any help at all would be greatly appreciated.

---

### Post by mkokotovich on 2008-07-07
Hmm, this probably isn't it, but it's what I always try with linking errors. As root, run

```
# ldconfig
```

Again, may do nothing for you.  

Just checking, you have build-essential installed?  Have you been able to successfully compile projects before?

---

### Post by shearn89 on 2008-07-08
I can compile other stuff, as i just compiled a new nvidia module. Tried ldconfig, but same error...

---

### Post by shearn89 on 2008-07-09
sorted it - needed to recompile freetype2 with the --enable-static switch.

---

