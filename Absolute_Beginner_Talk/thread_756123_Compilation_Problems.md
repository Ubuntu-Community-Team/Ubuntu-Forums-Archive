---
title: "Compilation Problems"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by ahaider on 2008-04-15
I am facing following problems while compiling some packages. Given below is a portion of ./configure output.

Package: **Linphone**
```
checking for SPEEX... configure: error: The pkg-config script could not be found or is too old.  Make sure it
is in your PATH or set the PKG_CONFIG environment variable to the full
path to pkg-config.

Alternatively, you may set the environment variables SPEEX_CFLAGS
and SPEEX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

To get pkg-config, see <http://pkg-config.freedesktop.org/>.
See `config.log' for more details.
```

Package: **Kphone**
```
checking location of Qt header files...
not found. Giving up.
```

What libraries do i need to remove these errors.

---

### Post by oldos2er on 2008-04-15
Is there some particular reason you're compiling from source, and not installing these programs from the repositories?

---

### Post by ahaider on 2008-04-16
> **oldos2er said:**
> Is there some particular reason you're compiling from source, and not installing these programs from the repositories?

The reason is that I can't run internet in ubuntu, as it does not pick my modem driver (I have tried to install one but to no avail). So, I am trying to compile the packages.

Secondly, if I succeed in compiling, then i would also be able to run a modified version of package.

---

### Post by oldos2er on 2008-04-16
Here are the dependencies for Linphone: 

Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 655k
Depends: libasound2 (> 1.0.12), libatk1.0-0 (>= 1.13.2), libavcodec1d (>=
         0.cvs20070307), libc6 (>= 2.5-5), libcairo2 (>= 1.4.0), libfontconfig1
         (>= 2.4.0), libglib2.0-0 (>= 2.13.2), libgtk2.0-0 (>= 2.10.3),
         liblinphone1 (>= 1.2.0), libmediastreamer0, libogg0 (>= 1.1.3),
         libortp5, libosip2-3, libpango1.0-0 (>= 1.17.1), libspeex1 (>= 1.1.8),
         libtheora0, libx11-6, libxcursor1 (> 1.1.2), libxext6, libxfixes3 (>=
         1:4.0.1), libxi6, libxinerama1, libxrandr2 (>= 2:1.2.0), libxrender1,
         linphone-nox (= 1.7.1-2)
Suggests: yelp

 And for Kphone:

Depends: libasound2 (> 1.0.14), libc6 (>= 2.6-1), libgcc1 (>= 1:4.2.1), libice6
         (>= 1:1.0.0), libpng12-0 (>= 1.2.13-4), libqt3-mt (>=
         3:3.3.8really3.3.7), libsm6, libssl0.9.8 (>= 0.9.8e-1), libstdc++6 (>=
         4.2.1), libx11-6, libxext6, libxt6

 Hope that helps.

---

