---
title: "Weird ./configure error"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Atanvarno on 2007-04-21
I tried to install playground via Synaptic, but it didn't seem to work, so I got the tarball, and ./configure returns> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
Config.log hurts my eyes to look at, so I Googled the error and found [http://www.geektimes.com/linux/troubleshooting/c-cant-create-executables.html](http://www.geektimes.com/linux/troubleshooting/c-cant-create-executables.html) which isn't that helpful as its about RedHat and refers to packages that don't seem to exist for Ubuntu.

What's going wrong?

---

### Post by tsg1zzn on 2007-04-21
It seems like there are some permission problems. Maybe gcc isn't correctly installed. Do you have writing rights to the source directory?

---

### Post by Bachstelze on 2007-04-21
```
sudo apt-get install build-essential
```

---

### Post by Atanvarno on 2007-04-21
Trying sudo ./configure didn't help. gcc should be correctly installed, Ubuntu was freshly installed today.

Edit: Thanks HymnToLife, I'll try that.

---

### Post by Atanvarno on 2007-04-21
That seems to have opened up another problem:> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
./configure: eval: line 1505: syntax error near unexpected token `('
./configure: eval: line 1505: `${SHELL} /home/atan/.Trash/playground-0 (copy).3/missing --run true'
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... configure: error: Package requirements (gtk+-2.0 >= 2.0.0
                         libpanelapplet-2.0 >= 2.0.0
                         libglade-2.0 >= 2.0.0
                         gconf-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found
No package 'libpanelapplet-2.0' found
No package 'libglade-2.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_CFLAGS
and GNOME_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I did a quick search in Synaptic, but the only one I get an exact match for, libglade-2.0, is already installed.

Thanks for your patience.

---

### Post by shirilover on 2007-04-21
you need to install the -dev files as well

---

### Post by Bachstelze on 2007-04-21
```
sudo apt-get install libgtk2.0-dev
```

---

