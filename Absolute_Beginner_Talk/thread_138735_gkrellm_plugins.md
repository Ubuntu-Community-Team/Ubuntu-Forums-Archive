---
title: "gkrellm plugins"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by ignorance on 2006-03-02
i found out that you can control your xmms player thru gkrellm so i tried to install the plugin but when i tried that it gave me a bunche of errors

```
cc  -O2 -Wall -fPIC `pkg-config gtk+-2.0 --cflags`  `xmms-config --cflags` -DPAC KAGE="\"gkrellmms\""     -c -o gkrellmms.o gkrellmms.c
/bin/sh: xmms-config: command not found
In file included from gkrellmms.c:22:
gkrellmms.h:31:27: error: xmms/xmmsctrl.h: No such file or directory
gkrellmms.c: In function ‘do_xmms_command’:
gkrellmms.c:106: warning: implicit declaration of function ‘xmms_remote_playlist _prev’
gkrellmms.c:108: warning: implicit declaration of function ‘xmms_remote_is_playi ng’
gkrellmms.c:109: warning: implicit declaration of function ‘xmms_remote_is_pause d’
gkrellmms.c:110: warning: implicit declaration of function ‘xmms_remote_pause’
gkrellmms.c:112: warning: implicit declaration of function ‘xmms_remote_play’
gkrellmms.c:116: warning: implicit declaration of function ‘xmms_remote_stop’
gkrellmms.c:119: warning: implicit declaration of function ‘xmms_remote_playlist _next’
gkrellmms.c:124: warning: implicit declaration of function ‘xmms_remote_eject’
gkrellmms.c: In function ‘update_gkrellmms’:
gkrellmms.c:214: warning: implicit declaration of function ‘xmms_remote_is_runni ng’
gkrellmms.c:231: warning: implicit declaration of function ‘xmms_remote_get_info ’
gkrellmms.c:300: warning: implicit declaration of function ‘xmms_remote_get_outp ut_time’
gkrellmms.c: In function ‘drag_data_received’:
gkrellmms.c:400: warning: implicit declaration of function ‘xmms_remote_playlist _clear’
gkrellmms.c:401: warning: implicit declaration of function ‘xmms_remote_playlist _add_url_string’
gkrellmms.c: In function ‘panel_button_release’:
gkrellmms.c:452: warning: implicit declaration of function ‘xmms_remote_jump_to_ time’
gkrellmms.c: In function ‘create_gkrellmms’:
gkrellmms.c:816: warning: implicit declaration of function ‘xmms_remote_main_win _toggle’
make: *** [gkrellmms.o] Error 1

```

i did it like i should ungzip and untar and than make but gues i did wrong.

---

### Post by gord on 2006-03-02
it looks like you need the xmms dev packages
```
sudo apt-get install xmms-dev
```

try again after getting that. be wary though, your entering the world of compiling, not for the faint hearted ;)

---

### Post by ignorance on 2006-03-02
well thanks to the xmms dev packages i didn't get any faults any more but still i can't get them installed or i'm mistaken.

```
cc  -O2 -Wall -fPIC `pkg-config gtk+-2.0 --cflags`  `xmms-config --cflags` -DPACKAGE="\"gkrellmms\""     -c -o gkrellmms.o gkrellmms.c
cc  -O2 -Wall -fPIC `pkg-config gtk+-2.0 --cflags`  `xmms-config --cflags` -DPACKAGE="\"gkrellmms\""     -c -o options.o options.c
cc  -O2 -Wall -fPIC `pkg-config gtk+-2.0 --cflags`  `xmms-config --cflags` -DPACKAGE="\"gkrellmms\""     -c -o playlist.o playlist.c
cc  -O2 -Wall -fPIC `pkg-config gtk+-2.0 --cflags`  `xmms-config --cflags` -DPACKAGE="\"gkrellmms\""  gkrellmms.o options.o playlist.o -o gkrellmms.so -shared -lpthread `pkg-config gtk+-2.0 --libs`  `xmms-config --libs`
(cd po && make all )
make[1]: Entering directory `/home/christophe/Desktop/gkrellmms/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/christophe/Desktop/gkrellmms/po'

```

---

### Post by gord on 2006-03-02
when compiling you generally have to do a 'sudo make install' after you have done 'make'. this installs the program. allthough i don't know that program/plugin personally so i can't be 100% sure.

---

### Post by ignorance on 2006-03-02
well i'm working in root so i don't need the sudo part

```
(cd po && make INSTALL_PREFIX= install)
make[1]: Entering directory `/home/christophe/Desktop/gkrellmms/po'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/christophe/Desktop/gkrellmms/po'
install -c -s -m 755 gkrellmms.so \
        //usr/local/lib/gkrellm2/plugins/gkrellmms.so
install: cannot create regular file `//usr/local/lib/gkrellm2/plugins/gkrellmms.so': No such file or directory
make: *** [install] Error 1

```

---

### Post by ignorance on 2006-03-02
Got it working if anyone is interested just do

```

sudo apt-get install gkrellmms
sudo apt-get install gkrellm-volume

```

if only i had figured that out earlier would have saved me a lot of trouble but thnx gord for the help or trying to.

---

