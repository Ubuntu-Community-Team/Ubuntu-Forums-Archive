---
title: "gettext installation"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by powerroot on 2008-01-03
Hello,

I'd like to install gstreamer0.8-ffmpeg eventually and now I'm trying to install gettext because of the dependency issue. 

I have installed the latest gettext-0.17 on my computer, it didn't complain anything through installation.(configure;make;make test;make install)
However, when I tried installing the next software that depends on xgettext, it gives an error because of the gettext library is not loading successfully. 

ERROR MESSAGE
xgettext: error while loading shared libraries: libgettextsrc-0.17.so: cannot open shared object file: No such file or directory

I checked and the libgettextsrc-0.17.so is in /usr/local/lib folder. 
I'm wondering what I'm doing wrong to make gettext not work. 
I'd like to get some help and I really appreciate your help. 

thanks, 
jungsook

---

### Post by PeterJS on 2008-01-03
Is gettext0-17 specifically required for the version of gstreamer you're planning to build?

I forgot the exact name of the environment variable, but it's LIB_PATH or something equally obvious that tells the linker where to look for libraries, that might not include /usr/local/lib/, if it's not included then it won't load because it won't know where to find the library.

---

### Post by powerroot on 2008-01-03
gettext was needed and my LIB_PATH env variable has /usr/lib:/usr/local/lib . 


I assume that xgettext is installed by gettext-0.17 package along with gettext. 
is it right? 

thanks,
js

---

### Post by PeterJS on 2008-01-03
> **powerroot said:**
> gettext was needed and my LIB_PATH env variable has /usr/lib:/usr/local/lib . 


I assume that xgettext is installed by gettext-0.17 package along with gettext. 
is it right? 

thanks,
js

I mean version 0-17 specifically, and looks right as far as I know. Yeah, I don't know about gettext and xgettext so I can't give you more specific advice, good luck.

---

### Post by Moeng on 2008-07-06
I also need to install gettext to resolve a dependency and am getting the same error, except through the msgfmt program instead of xgettext.

If it helps, I'm running Ubuntu through VMPlayer.
The installation for gettext seemed so have worked, but using accessing msgfmt brings up the error with libgettextsrc-0.17.so being missing.

---

### Post by hyperrealityMan on 2008-07-08
Hi!
This is the first time I've ever been able to help somebody with Linux!!! (I'm pretty excited :))

What you need to do is place symlinks to the library files in /usr/lib.
The commands will be (assuming you installed gettext to /usr/local and you are currently in /usr/lib)

```

ln -s ../local/lib/libgettextsrc-0.17.so libgettextsrc-0.17.so
ln -s ../local/lib/libgettextlib-0.17.so libgettextlib-0.17.so

```

That resolves it. 

:D

---

### Post by Moeng on 2008-07-08
> **hyperrealityMan said:**
> Hi!
This is the first time I've ever been able to help somebody with Linux!!! (I'm pretty excited :))

What you need to do is place symlinks to the library files in /usr/lib.
The commands will be (assuming you installed gettext to /usr/local and you are currently in /usr/lib)

```

ln -s ../local/lib/libgettextsrc-0.17.so libgettextsrc-0.17.so
ln -s ../local/lib/libgettextlib-0.17.so libgettextlib-0.17.so

```

That resolves it. 

:D

This worked, thanks so much.  Only tweak I had to use was "sudo" before the commands because I wasn't logged in as the root.

---

