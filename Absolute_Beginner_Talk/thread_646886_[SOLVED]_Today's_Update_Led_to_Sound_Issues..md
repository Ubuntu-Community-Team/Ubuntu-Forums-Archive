---
title: "[SOLVED] Today's Update Led to Sound Issues."
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Presto123 on 2007-12-21
Just want to get it back on my laptop  (Compaq Presario C500). Compiling is coming back as a no-go, too. Here's the error:

```
presto@presto-laptop:/usr/src/alsa$ cd alsa-driver-1.0.15
presto@presto-laptop:/usr/src/alsa/alsa-driver-1.0.15$ sudo ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
presto@presto-laptop:/usr/src/alsa/alsa-driver-1.0.15$ sudo make
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15'

Please, run the configure script as first...

presto@presto-laptop:/usr/src/alsa/alsa-driver-1.0.15$ sudo make install
if [ -L /include/sound ]; then \
                rm -f /include/sound; \
                ln -sf /usr/src/alsa/alsa-driver-1.0.15/include/sound /include/sound; \
        else \
                rm -rf /include/sound; \
                install -d -m 755 -g root -o root /include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /include/sound; \
                done \
        fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
presto@presto-laptop:/usr/src/alsa/alsa-driver-1.0.15$ sudo ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
presto@presto-laptop:/usr/src/alsa/alsa-driver-1.0.15$ 


```

---

### Post by spiderbatdad on 2007-12-21
not sure, but maybe g++ will work if you install it. also build-essential. seems the problem is in the compiler. does config.log show anything of interest?

---

### Post by spiderbatdad on 2007-12-21
ah looks like your file is not executable? ```
sudo chmod a+x /usr/src/alsa/alsa-driver-1.0.15
```

---

### Post by Presto123 on 2007-12-21
I got it back...It looks as though it was another error in my Gnome startup. Sometimes, it just refuses to start correctly and I put it into standby, after I took it out of standby I logged out and got sound back.

Blah. It's back, though.

---

