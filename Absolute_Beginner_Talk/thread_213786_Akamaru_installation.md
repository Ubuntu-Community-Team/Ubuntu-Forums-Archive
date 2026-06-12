---
title: "Akamaru installation"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by FPStanley on 2006-07-11
I am not sure how many people are familar with it, so here is the link:

[Akamaru]("http://people.freedesktop.org/~krh/akamaru.git/")

I ran make in terminal as was then given the following error:

> 
~/Desktop/akamaru$ make
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package cairo was not found in the pkg-config search path.
Perhaps you should add the directory containing `cairo.pc'
to the PKG_CONFIG_PATH environment variable
No package 'cairo' found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
cc -Wall -g   -c -o akamaru.o akamaru.c
akamaru.c:16:18: error: glib.h: No such file or directory
akamaru.c: In function ‘model_add_spring’:
akamaru.c:95: warning: implicit declaration of function ‘g_new’
akamaru.c:95: error: syntax error before ‘Spring’
akamaru.c: In function ‘model_add_stick’:
akamaru.c:117: error: syntax error before ‘Stick’
akamaru.c: In function ‘model_add_string’:
akamaru.c:139: error: syntax error before ‘String’
akamaru.c: In function ‘model_add_spacer’:
akamaru.c:171: error: syntax error before ‘Spacer’
akamaru.c: In function ‘model_add_anchor’:
akamaru.c:193: error: syntax error before ‘Anchor’
akamaru.c: In function ‘polygon_init_from_va_list’:
akamaru.c:213: error: syntax error before ‘Point’
akamaru.c:221: error: syntax error before ‘Vector’
akamaru.c: In function ‘model_add_polygon’:
akamaru.c:250: warning: implicit declaration of function ‘g_new0’
akamaru.c:250: error: syntax error before ‘Polygon’
akamaru.c: In function ‘polygon_init_diamond’:
akamaru.c:262: error: ‘FALSE’ undeclared (first use in this function)
akamaru.c:262: error: (Each undeclared identifier is reported only once
akamaru.c:262: error: for each function it appears in.)
akamaru.c: In function ‘polygon_init_rectangle’:
akamaru.c:274: error: ‘FALSE’ undeclared (first use in this function)
akamaru.c: In function ‘polygon_init_enclosing_rectangle’:
akamaru.c:281: error: ‘TRUE’ undeclared (first use in this function)
akamaru.c: In function ‘model_add_enclosing_rectangle’:
akamaru.c:288: error: ‘TRUE’ undeclared (first use in this function)
akamaru.c: In function ‘model_init’:
akamaru.c:295: warning: implicit declaration of function ‘G_STRUCT_OFFSET’
akamaru.c:295: error: syntax error before ‘Object’
akamaru.c:296: error: syntax error before ‘Spacer’
akamaru.c:297: error: syntax error before ‘Spring’
akamaru.c:298: error: syntax error before ‘Stick’
akamaru.c:299: error: syntax error before ‘String’
akamaru.c:300: error: syntax error before ‘Anchor’
akamaru.c:301: error: syntax error before ‘Polygon’
akamaru.c:302: error: syntax error before ‘Offset’
akamaru.c: In function ‘model_add_object’:
akamaru.c:310: error: syntax error before ‘Object’
akamaru.c: In function ‘model_fini’:
akamaru.c:333: warning: implicit declaration of function ‘g_free’
make: *** [akamaru.o] Error 1
matt@MAGI:~/Desktop/akamaru$ sudo make
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package cairo was not found in the pkg-config search path.
Perhaps you should add the directory containing `cairo.pc'
to the PKG_CONFIG_PATH environment variable
No package 'cairo' found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
cc -Wall -g   -c -o akamaru.o akamaru.c
akamaru.c:16:18: error: glib.h: No such file or directory
akamaru.c: In function ‘model_add_spring’:
akamaru.c:95: warning: implicit declaration of function ‘g_new’
akamaru.c:95: error: syntax error before ‘Spring’
akamaru.c: In function ‘model_add_stick’:
akamaru.c:117: error: syntax error before ‘Stick’
akamaru.c: In function ‘model_add_string’:
akamaru.c:139: error: syntax error before ‘String’
akamaru.c: In function ‘model_add_spacer’:
akamaru.c:171: error: syntax error before ‘Spacer’
akamaru.c: In function ‘model_add_anchor’:
akamaru.c:193: error: syntax error before ‘Anchor’
akamaru.c: In function ‘polygon_init_from_va_list’:
akamaru.c:213: error: syntax error before ‘Point’
akamaru.c:221: error: syntax error before ‘Vector’
akamaru.c: In function ‘model_add_polygon’:
akamaru.c:250: warning: implicit declaration of function ‘g_new0’
akamaru.c:250: error: syntax error before ‘Polygon’
akamaru.c: In function ‘polygon_init_diamond’:
akamaru.c:262: error: ‘FALSE’ undeclared (first use in this function)
akamaru.c:262: error: (Each undeclared identifier is reported only once
akamaru.c:262: error: for each function it appears in.)
akamaru.c: In function ‘polygon_init_rectangle’:
akamaru.c:274: error: ‘FALSE’ undeclared (first use in this function)
akamaru.c: In function ‘polygon_init_enclosing_rectangle’:
akamaru.c:281: error: ‘TRUE’ undeclared (first use in this function)
akamaru.c: In function ‘model_add_enclosing_rectangle’:
akamaru.c:288: error: ‘TRUE’ undeclared (first use in this function)
akamaru.c: In function ‘model_init’:
akamaru.c:295: warning: implicit declaration of function ‘G_STRUCT_OFFSET’
akamaru.c:295: error: syntax error before ‘Object’
akamaru.c:296: error: syntax error before ‘Spacer’
akamaru.c:297: error: syntax error before ‘Spring’
akamaru.c:298: error: syntax error before ‘Stick’
akamaru.c:299: error: syntax error before ‘String’
akamaru.c:300: error: syntax error before ‘Anchor’
akamaru.c:301: error: syntax error before ‘Polygon’
akamaru.c:302: error: syntax error before ‘Offset’
akamaru.c: In function ‘model_add_object’:
akamaru.c:310: error: syntax error before ‘Object’
akamaru.c: In function ‘model_fini’:
akamaru.c:333: warning: implicit declaration of function ‘g_free’
make: *** [akamaru.o] Error 1


From what I have read the installation of this dock should be relatively problem free, so I'm curious where I could have went wrong. I'm still new to Ubuntu so any suggestions or help is greatly appreciated. Thank you!

---

### Post by ASUmusicMAN on 2006-07-12
I have downloaded the tarball from the site and "sudo make" left me with command not found.  I also tried ./Makefile and I got the following output

> ./Makefile: line 1: CFLAGS: command not found
./Makefile: line 2: shell: command not found
./Makefile: line 2: CPPFLAGS: command not found
./Makefile: line 3: shell: command not found
./Makefile: line 3: LDLIBS: command not found
./Makefile: line 4: LDFLAGS: command not found
./Makefile: line 5: GCONFTOOL: command not found
./Makefile: line 7: targets: command not found
./Makefile: line 8: schemas: command not found
./Makefile: line 9: akamaru_objs: command not found
./Makefile: line 10: dock_objs: command not found
./Makefile: line 11: akamaru_objs: command not found
./Makefile: line 11: dock_objs: command not found
./Makefile: line 11: objs: command not found
./Makefile: line 13: targets: command not found
./Makefile: line 13: all: command not found
./Makefile: line 15: akamaru_objs: command not found
./Makefile: line 15: akamaru: command not found
./Makefile: line 17: dock_objs: command not found
./Makefile: line 17: dock: command not found
./Makefile: line 19: objs: command not found
./Makefile: line 21: install-schemas: command not found
./Makefile: line 22: GCONFTOOL: command not found
./Makefile: line 22: schemas: command not found
./Makefile: line 22: GCONF_CONFIG_SOURCE: command not found
./Makefile: line 22: --makefile-install-rule: command not found
./Makefile: line 25: uninstall-schemas: command not found
./Makefile: line 26: GCONFTOOL: command not found
./Makefile: line 26: schemas: command not found
./Makefile: line 26: GCONF_CONFIG_SOURCE: command not found
./Makefile: line 26: --makefile-uninstall-rule: command not found
./Makefile: line 29: gconf-clean: command not found
./Makefile: line 30: GCONFTOOL: command not found
./Makefile: line 30: --recursive-unset: command not found
./Makefile: line 32: index.html: command not found
./log.sh: line 6: git-rev-list: command not found
./Makefile: line 35: clean: command not found
./Makefile: line 36: targets: command not found
./Makefile: line 36: objs: command not found


Does the tarball not work in ubuntu?

---

### Post by Nomad64 on 2006-07-12
I had to do the following in order to get the Akamaru panel to work:
```
sudo apt-get install build-essential libgconf2-dev
cd akamaru/
make
./dock &

```

Unfortunately, it doesn't seem to practical at the moment...just another fun play toy.

---

### Post by FPStanley on 2006-07-15
> **Nomad64 said:**
> I had to do the following in order to get the Akamaru panel to work:
```
sudo apt-get install build-essential libgconf2-dev
cd akamaru/
make
./dock &

```

Unfortunately, it doesn't seem to practical at the moment...just another fun play toy.

Thank you!

---

### Post by Jedeye on 2006-07-22
So I got what seems to be the same error ```
jon@dapper:~/Desktop/akamaru$ make && ./populate-dock.sh
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package cairo was not found in the pkg-config search path.
Perhaps you should add the directory containing `cairo.pc'
to the PKG_CONFIG_PATH environment variable
No package 'cairo' found
cc -Wall -g   -c -o akamaru.o akamaru.c
akamaru.c:16:18: error: glib.h: No such file or directory
akamaru.c: In function ‘model_add_spring’:
akamaru.c:98: warning: implicit declaration of function ‘g_new’
akamaru.c:98: error: syntax error before ‘Spring’
akamaru.c: In function ‘model_add_stick’:
akamaru.c:126: error: syntax error before ‘Stick’
akamaru.c: In function ‘model_add_string’:
akamaru.c:154: error: syntax error before ‘String’
akamaru.c: In function ‘model_add_offset_spring’:
akamaru.c:175: error: syntax error before ‘OffsetSpring’
akamaru.c: In function ‘model_add_spacer’:
akamaru.c:204: error: syntax error before ‘Spacer’
akamaru.c: In function ‘model_add_anchor’:
akamaru.c:232: error: syntax error before ‘Anchor’
akamaru.c: In function ‘model_delete_anchor’:
akamaru.c:245: warning: implicit declaration of function ‘g_free’
akamaru.c: In function ‘polygon_init_from_va_list’:
akamaru.c:265: error: syntax error before ‘Point’
akamaru.c:273: error: syntax error before ‘Vector’
akamaru.c: In function ‘model_add_polygon’:
akamaru.c:302: warning: implicit declaration of function ‘g_new0’
akamaru.c:302: error: syntax error before ‘Polygon’
akamaru.c: In function ‘model_add_diamond’:
akamaru.c:320: error: ‘FALSE’ undeclared (first use in this function)
akamaru.c:320: error: (Each undeclared identifier is reported only once
akamaru.c:320: error: for each function it appears in.)
akamaru.c: In function ‘model_add_rectangle’:
akamaru.c:331: error: ‘FALSE’ undeclared (first use in this function)
akamaru.c: In function ‘model_add_enclosing_rectangle’:
akamaru.c:338: error: ‘TRUE’ undeclared (first use in this function)
akamaru.c: In function ‘model_add_offset’:
akamaru.c:346: error: syntax error before ‘Offset’
akamaru.c:348: error: syntax error before ‘Object’
akamaru.c: In function ‘model_init’:
akamaru.c:366: warning: implicit declaration of function ‘G_STRUCT_OFFSET’
akamaru.c:366: error: syntax error before ‘Object’
akamaru.c:367: error: syntax error before ‘Spacer’
akamaru.c:368: error: syntax error before ‘String’
akamaru.c:369: error: syntax error before ‘Stick’
akamaru.c:370: error: syntax error before ‘Spring’
akamaru.c:371: error: syntax error before ‘Anchor’
akamaru.c:372: error: syntax error before ‘Polygon’
akamaru.c:373: error: syntax error before ‘Offset’
akamaru.c:375: error: syntax error before ‘OffsetSpring’
akamaru.c: In function ‘model_add_object’:
akamaru.c:383: error: syntax error before ‘Object’
make: *** [akamaru.o] Error 1
jon@dapper:~/Desktop/akamaru$ sudo make && ./populate-dock.sh
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package cairo was not found in the pkg-config search path.
Perhaps you should add the directory containing `cairo.pc'
to the PKG_CONFIG_PATH environment variable
No package 'cairo' found
cc -Wall -g   -c -o akamaru.o akamaru.c
akamaru.c:16:18: error: glib.h: No such file or directory
akamaru.c: In function ‘model_add_spring’:
akamaru.c:98: warning: implicit declaration of function ‘g_new’
akamaru.c:98: error: syntax error before ‘Spring’
akamaru.c: In function ‘model_add_stick’:
akamaru.c:126: error: syntax error before ‘Stick’
akamaru.c: In function ‘model_add_string’:
akamaru.c:154: error: syntax error before ‘String’
akamaru.c: In function ‘model_add_offset_spring’:
akamaru.c:175: error: syntax error before ‘OffsetSpring’
akamaru.c: In function ‘model_add_spacer’:
akamaru.c:204: error: syntax error before ‘Spacer’
akamaru.c: In function ‘model_add_anchor’:
akamaru.c:232: error: syntax error before ‘Anchor’
akamaru.c: In function ‘model_delete_anchor’:
akamaru.c:245: warning: implicit declaration of function ‘g_free’
akamaru.c: In function ‘polygon_init_from_va_list’:
akamaru.c:265: error: syntax error before ‘Point’
akamaru.c:273: error: syntax error before ‘Vector’
akamaru.c: In function ‘model_add_polygon’:
akamaru.c:302: warning: implicit declaration of function ‘g_new0’
akamaru.c:302: error: syntax error before ‘Polygon’
akamaru.c: In function ‘model_add_diamond’:
akamaru.c:320: error: ‘FALSE’ undeclared (first use in this function)
akamaru.c:320: error: (Each undeclared identifier is reported only once
akamaru.c:320: error: for each function it appears in.)
akamaru.c: In function ‘model_add_rectangle’:
akamaru.c:331: error: ‘FALSE’ undeclared (first use in this function)
akamaru.c: In function ‘model_add_enclosing_rectangle’:
akamaru.c:338: error: ‘TRUE’ undeclared (first use in this function)
akamaru.c: In function ‘model_add_offset’:
akamaru.c:346: error: syntax error before ‘Offset’
akamaru.c:348: error: syntax error before ‘Object’
akamaru.c: In function ‘model_init’:
akamaru.c:366: warning: implicit declaration of function ‘G_STRUCT_OFFSET’
akamaru.c:366: error: syntax error before ‘Object’
akamaru.c:367: error: syntax error before ‘Spacer’
akamaru.c:368: error: syntax error before ‘String’
akamaru.c:369: error: syntax error before ‘Stick’
akamaru.c:370: error: syntax error before ‘Spring’
akamaru.c:371: error: syntax error before ‘Anchor’
akamaru.c:372: error: syntax error before ‘Polygon’
akamaru.c:373: error: syntax error before ‘Offset’
akamaru.c:375: error: syntax error before ‘OffsetSpring’
akamaru.c: In function ‘model_add_object’:
akamaru.c:383: error: syntax error before ‘Object’
make: *** [akamaru.o] Error 1

```
So I ran ```
sudo apt-get install build-essential libgconf2-dev
```
And I got
```
jon@dapper:~/Desktop/akamaru$ sudo apt-get install build-essential libgconf2-devReading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
libgconf2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Would really like to try this dock out but cant get it to work... any ideas?

---

### Post by panurge77 on 2006-07-23
Theres some forked development of this dock at compiz forums. You could check there for more info or new features.
(Actually the dock is named kiba, akamaru is the engine)

[http://www.compiz.net/viewtopic.php?id=1972](http://www.compiz.net/viewtopic.php?id=1972)

---

### Post by ASUmusicMAN on 2006-07-24
I kinda got the akamaru working, but going to compiz forums and using kiba fixed it up nice.  Here's an easy how-to

[http://www.compiz.net/viewtopic.php?id=2004](http://www.compiz.net/viewtopic.php?id=2004)

---

### Post by hype on 2006-07-26
Thanx panurge, i will check that out.
The little demo about physical effects seems quite cool :p
 By the way, im willing to try akamaru (kiba) because id like to use a dock applet: for you what is the best dock applet?
 What about cairo-dock?
(i really appreciate the fact that cairo is based on open GL, but installation and configurtaion doesnt seem really easy at the time, right?)

---

### Post by dipswitch on 2006-07-29
This thing is kinda cool. Here is what I had to do from a fresh install.

First I installed build essentials
```

sudo apt-get install build-essential

```

Then installed the GTK+ and Cairo libraries
```

sudo apt-get install libcairo2-dev libgtk2.0-dev

```

Then had to install some gnome libraries... dum dee dum...
```

sudo apt-get install libgconf2-dev

```

Then installed cvs.......
```

sudo apt-get install cvs

```

After that I was able to download, install, and compile from following the first post on the howto at [http://www.compiz.net/viewtopic.php?id=2004]("http://www.compiz.net/viewtopic.php?id=2004") and got it working.

I added the dock to the startup session to make it run on login.

---

