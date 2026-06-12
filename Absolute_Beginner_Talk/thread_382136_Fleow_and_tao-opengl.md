---
title: "Fleow and tao-opengl"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Astarus on 2007-03-11
Hello all,

Ive been trying to install fleow for Banshee. I have downloaded the files from svn and run ./autogen.sh

I get an error about the tao-opengl package not being found. I have searched using synaptic and google for the package but for nothing. 

Does anone know where I can get the package?

I'm running Edgy if that matters.

Thanks

---

### Post by nilsja on 2007-04-07
i have the same problem with feisty

---

### Post by nilsja on 2007-04-10
i think we need the tao framework. [http://www.taoframework.com/](http://www.taoframework.com/)

perhaps somebody here in the forum can tell us where to put these framework files, so that they get recognized by the ./autogen.sh script?

---

### Post by nilsja on 2007-04-18
can't anybody help us? its this plugin:
[http://fleow.berlios.de/](http://fleow.berlios.de/)

and the error i get trying ./autogen.sh is```
nils@schlepptop:~/fleow$ ./autogen.sh
I am going to run ./configure with no arguments - if you wish
to pass any to it, please specify them on the ./autogen.sh command line.
Running aclocal -I . ...
Running automake --gnu ...
Running autoconf ...
Running ./configure ...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yesdankbar,
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO... yes
checking for TAO... configure: error: Package requirements (tao-opengl >= 1.3.0) were not met:

No package 'tao-opengl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables TAO_CFLAGS
and TAO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

nils@schlepptop:~/fleow$
```

---

### Post by chriss_crooze on 2007-10-30
Just Read through [http://anonsvn.mono-project.com/source/trunk/tao/README.autotools](http://anonsvn.mono-project.com/source/trunk/tao/README.autotools) ... this may help a lot

---

