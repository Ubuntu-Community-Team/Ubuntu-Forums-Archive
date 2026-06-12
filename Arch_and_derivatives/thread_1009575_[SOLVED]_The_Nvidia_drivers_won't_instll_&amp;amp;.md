---
title: "[SOLVED] The Nvidia drivers won't instll &amp;amp; Is there a way to install Synaptic Package"
date: 2008-12-12
forum: Arch and derivatives
---

### Post by Newuser1111 on 2008-12-12
Nvidia Driver will not install:
```
[djk@myhost synaptic-0.53]$ sudo pacman -S nvidia
Password: 
resolving dependencies...
looking for inter-conflicts...
:: nvidia-utils conflicts with libgl. Remove libgl? [Y/n] Y
error: failed to prepare transaction (could not satisfy dependencies)
:: atl2: requires kernel26<2.6.26
:: ipw3945: requires kernel26<2.6.26
:: madwifi: requires kernel26<2.6.26
:: ndiswrapper: requires kernel26<2.6.26
:: rt2500: requires kernel26<2.6.26
:: tiacx: requires kernel26<2.6.26
:: wlan-ng26: requires kernel26<2.6.26
[djk@myhost synaptic-0.53]$ 

```




How do I install Synaptic Package Manager on Arch Linux?
```
[djk@myhost synaptic-0.53]$ ./configure
checking for a BSD-compatible install... /bin/install -c
checking whether build environment is sane... yes
/home/djk/synaptic-0.53/missing: Unknown `--run' option
Try `/home/djk/synaptic-0.53/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  ar pt_BR es fr de tr zh_CN zh_HK zh_TW ru nl ja be it_IT pl cs hu sr sr@Latn da he ca ko bg
checking for intltool >= 0.23... 0.30 found
checking for perl... /usr/bin/perl
checking for xmlto... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0, libglade-2.0 >= 2.0.0, pango >= 1.0.0, glib-2.0... yes
checking PACKAGE_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libglade-2.0 -I/usr/include/libxml2  
checking PACKAGE_LIBS... -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lpangocairo-1.0 -lcairo -lfreetype -lz -lfontconfig -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
checking RPM version... checking rpm/rpmlib.h usability... no
checking rpm/rpmlib.h presence... no
checking for rpm/rpmlib.h... no
checking for rpm/rpmlib.h... (cached) no
"RPM version is none"
checking for --enable-scripts... yes
checking for ANSI C header files... (cached) yes
checking for unistd.h... (cached) yes
checking for libintl.h... (cached) yes
checking iconv.h usability... yes
checking iconv.h presence... yes
checking for iconv.h... yes
checking how to run the C++ preprocessor... g++ -E
checking apt-pkg/configuration.h usability... no
checking apt-pkg/configuration.h presence... no
checking for apt-pkg/configuration.h... no
configure: error: You need the apt-pkg headers installed to compile synaptic.
[djk@myhost synaptic-0.53]$ 

```

---

### Post by OutOfReach on 2008-12-12
Synaptic Package Manager is strictly for distros that use APT (Debian, Ubuntu, etc) so no, you can't use it in Arch.

---

### Post by Newuser1111 on 2008-12-12
> **OutOfReach said:**
> Synaptic Package Manager is strictly for distros that use APT (Debian, Ubuntu, etc) so no, you can't use it in Arch.Is there anything else similar to it?

Or can I install APT?

---

### Post by cardinals_fan on 2008-12-12
Did you upgrade your system (pacman -Syu) before trying to install the NVIDIA drivers?

If you don't want to use pacman, there's no real sense in using Arch.  You can search with "pacman -Ss".  If you really want a GUI, read this: [http://wiki.archlinux.org/index.php/Pacman_GUI_Frontends](http://wiki.archlinux.org/index.php/Pacman_GUI_Frontends)

If you're willing to learn the CLI version, read this instead: [http://wiki.archlinux.org/index.php/Pacman](http://wiki.archlinux.org/index.php/Pacman)

---

### Post by crimesaucer on 2008-12-12
No, you can not install APT. Give pacman a try before you run from it.


If you just installed the core packages from the Arch CD then you must do a full system upgrade to catch up to the current "rolling release". (kernel26 2.6.27.8-1)

```
sudo pacman -Syu
```


As for a GUI comparable to Synaptic Package Manager try something like: [http://wiki.archlinux.org/index.php/Yaourt](http://wiki.archlinux.org/index.php/Yaourt)


or just learn to use pacman (I like it much better than Synaptic apt-get):

```
man pacman
```

---

### Post by Newuser1111 on 2008-12-12
> **cardinals_fan said:**
> Did you upgrade your system (pacman -Syu) before trying to install the NVIDIA drivers?

If you don't want to use pacman, there's no real sense in using Arch.  You can search with "pacman -Ss".  If you really want a GUI, read this: [http://wiki.archlinux.org/index.php/Pacman_GUI_Frontends](http://wiki.archlinux.org/index.php/Pacman_GUI_Frontends)

If you're willing to learn the CLI version, read this instead: [http://wiki.archlinux.org/index.php/Pacman](http://wiki.archlinux.org/index.php/Pacman)
I got NVIDIA working.
Installed gtkPacman and it's working.

---

