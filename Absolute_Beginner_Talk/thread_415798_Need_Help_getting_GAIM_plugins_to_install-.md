---
title: "Need: Help getting GAIM plugins to install-"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Feba on 2007-04-20
[http://svana.org/kleptog/index.html](http://svana.org/kleptog/index.html)

Downloaded teh GAIM plugins from here, and I've got it working fine upto the point where the README says to run "make && make install" on the folder, which seems to work, but returns:

```
:~/Desktop/plugins$ make && make
gcc -O2 -g -Wall `pkg-config --cflags glib-2.0 gaim` -DPLUGIN_VERSION=0.2   -c -o buddytimezone.o buddytimezone.c
buddytimezone.c:123: error: expected identifier or ‘(’ before ‘{’ token
make: *** [buddytimezone.o] Error 1
```

This is the file I downloaded this for, and it seems to be the first thing attempted (and failed)

Does anyone know how to get this working?

---

### Post by Feba on 2007-04-20
If anyone knows of another plugin with the same functionality, I could use that too.. =/

---

### Post by Sef on 2007-04-20
Which version did you download?

---

### Post by Feba on 2007-04-21
Which version of what? I downloaded GAIM through Synaptic/AddRemove

---

### Post by Feba on 2007-04-21
I'm running Feisty, if that's what you meant.

---

### Post by Feba on 2007-04-23
I still need an answer for this..

---

### Post by Skerit on 2007-04-28
Yeah, I tried to compile a plugin, too, and it said it couldn't find "gaim"...

No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables gaim_CFLAGS
and gaim_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


That's a lot of work for one stupid plugin, though

---

