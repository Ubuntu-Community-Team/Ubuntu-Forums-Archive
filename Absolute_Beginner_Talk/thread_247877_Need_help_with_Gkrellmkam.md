---
title: "Need help with Gkrellmkam"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by junamuno on 2006-08-31
I downloaded Gkrellmkam but I don't know how to add it into gkrellm, i go to preferences>plugins but it doesn't allow me to install anything, How am I supposed to do it???

THX

---

### Post by junamuno on 2006-08-31
Nevermind I figured it out!!!

I just had to put it gkrellmkam in the plugins folder and restart gkrellm

---

### Post by mohdridha on 2006-12-31
How you do that? I have tried to put the tarball and also the extract dir to ~/.gkrellm2/themes
but still failed.

Dont we need to type command 'make' first to install new plugin for gkrellm?
btw, i'm trying to use this plugin: [http://starforge.co.uk/gkrellm/gkrellmeris.shtml](http://starforge.co.uk/gkrellm/gkrellmeris.shtml).

---

### Post by taurus on 2006-12-31
You just unpack that to ~/.gkrellm2/plugins since it is a plugin, not theme.

---

### Post by mohdridha on 2006-12-31
Ok Sorry with my typo... its ~/gkrellm2/plugins

[email]kapla@mrn:~/.gkre[/email]llm2/plugins$ ls
gkrellkam-2.0.0  gkrellmeris-2.0.1  gkrellmeris-2.0.1.tar
[email]kapla@mrn:~/.gkre[/email]llm2/plugins$

And I still cant use that plugins.. I have closed and reopen gkrellm but still failed

I'm using Gkrellm 2.2.7

---

### Post by taurus on 2006-12-31
```
cd ~/.gkrellm2/plugins/gkrellmeris-2.0.1
make
sudo make install
```
Now, restart gkrellm...

---

### Post by mohdridha on 2006-12-31
I have tried that but got this error message:

[email]kapla@mrn:~/.gkre[/email]llm2/plugins/gkrellmeris-2.0.1$ ls
gkrellmeris.c  INSTALL  Makefile  README
[email]kapla@mrn:~/.gkre[/email]llm2/plugins/gkrellmeris-2.0.1$ make
gcc -O2 -Wall -fPIC `pkg-config gtk+-2.0 --cflags` -DPACKAGE="\"gkrellmeris\"" -DPREFIX=\"/usr/local\" -DVERSION=\"2.0.0\" -c gkrellmeris.c
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
In file included from gkrellmeris.c:2:
/usr/include/gkrellm2/gkrellm.h:30:21: error: gtk/gtk.h: No such file or directory
In file included from gkrellmeris.c:2:
/usr/include/gkrellm2/gkrellm.h:195: error: syntax error before ‘gfloat’
/usr/include/gkrellm2/gkrellm.h:198: error: syntax error before ‘}’ token
/usr/include/gkrellm2/gkrellm.h:219: error: syntax error before ‘PangoFontDescription’
/usr/include/gkrellm2/gkrellm.h:221: error: syntax error before ‘privat’
/usr/include/gkrellm2/gkrellm.h:222: error: syntax error before ‘effect’
/usr/include/gkrellm2/gkrellm.h:223: error: syntax error before ‘internal’
/usr/include/gkrellm2/gkrellm.h:224: error: syntax error before ‘flags’
/usr/include/gkrellm2/gkrellm.h:225: error: syntax error before ‘color’
/usr/include/gkrellm2/gkrellm.h:226: error: syntax error before ‘shadow_color’
/usr/include/gkrellm2/gkrellm.h:232: error: syntax error before ‘gchar’
/usr/include/gkrellm2/gkrellm.h:235: error: syntax error before ‘x_off_prev’

Maybe i dont have gtk+-2.0... I have search around but still dont have any clue about GTK or how to install it...

Right now i'm trying to do this:

```
 sudo apt-get build-dep gkrellm 
```

Hope it can makes my gtk2 automatically.. 

Btw Taurus, thanks for your quick reply :)

---

### Post by taurus on 2006-12-31
Well, here it what I got when I ran it...

```

taurus@taurus:~/temp/gkrellmeris-2.0.1$ make
gcc -O2 -Wall -fPIC `pkg-config gtk+-2.0 --cflags` -DPACKAGE="\"gkrellmeris\"" -DPREFIX=\"/usr/local\" -DVERSION=\"2.0.0\" -c gkrellmeris.c
gkrellmeris.c: In function ‘eris_draw_panel’:
gkrellmeris.c:339: warning: passing argument 1 of ‘gdk_string_width’ from incompatible pointer type
gkrellmeris.c:340: warning: passing argument 1 of ‘gdk_string_width’ from incompatible pointer type
gcc gkrellmeris.o -DVERSION=\"2.0.0\" -o gkrellmeris.so -shared `pkg-config gtk+-2.0 --libs`

```

Looks like you need to install the libgtk2.0-dev package as well...

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install libgtk2.0-dev
make
sudo make install
```

---

### Post by mohdridha on 2006-12-31
Sweet man, problem solved.. 

libgtk2-dev is the root of it.. 

Thanks a lot :mrgreen:

---

### Post by taurus on 2006-12-31
You're welcome.

---

