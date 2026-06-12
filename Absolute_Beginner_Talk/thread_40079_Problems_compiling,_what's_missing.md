---
title: "Problems compiling, what's missing?"
date: 2005-06-07
forum: Absolute Beginner Talk
---

### Post by Musagetes on 2005-06-07
Hey, all. I'm trying to get hold of Xmms::Remote, but I'm receiving errors during compilations. I'm absolutely at a loss when it comes to compiling (I know ./configure, make, makeinstall/checkinstall, and that's it), so the error messages are a foreign language to me. I'm guessing I'm missing some package, but I have gcc, fakeroot, build-essentials, and such ... Can some expert run through my output and spot the culprit?

```
[hn@museion > ~]$ sudo perl -MCPAN -e 'install Xmms::Remote'
CPAN: Storable loaded ok
Going to read /home/hn/.cpan/Metadata
  Database was generated on Tue, 07 Jun 2005 15:08:01 GMT
Running install for module Xmms::Remote
Running make for D/DO/DOUGM/Xmms-Perl-0.12.tar.gz
CPAN: Digest::MD5 loaded ok
Checksum for /home/hn/.cpan/sources/authors/id/D/DO/DOUGM/Xmms-Perl-0.12.tar.gz ok
Scanning cache /home/hn/.cpan/build for sizes
Xmms-Perl-0.12/
Xmms-Perl-0.12/README
Xmms-Perl-0.12/lib/
Xmms-Perl-0.12/lib/Xmms.pm
Xmms-Perl-0.12/lib/Xmms/
Xmms-Perl-0.12/lib/Xmms/ExtUtils.pm
Xmms-Perl-0.12/lib/Bundle/
Xmms-Perl-0.12/lib/Bundle/Xmms.pm
Xmms-Perl-0.12/test3.mp3
Xmms-Perl-0.12/MANIFEST
Xmms-Perl-0.12/test.pl
Xmms-Perl-0.12/Changes
Xmms-Perl-0.12/Makefile.PL
Xmms-Perl-0.12/Config/
Xmms-Perl-0.12/Config/Config.xs
Xmms-Perl-0.12/Config/Makefile.PL
Xmms-Perl-0.12/Config/Config.pm
Xmms-Perl-0.12/patches/
Xmms-Perl-0.12/patches/xmms-playlist-delete.pat
Xmms-Perl-0.12/Remote/
Xmms-Perl-0.12/Remote/Makefile.PL
Xmms-Perl-0.12/Remote/Remote.xs
Xmms-Perl-0.12/Remote/Remote.pm
Xmms-Perl-0.12/SongChange/
Xmms-Perl-0.12/SongChange/SongChange.xs
Xmms-Perl-0.12/SongChange/Makefile.PL
Xmms-Perl-0.12/SongChange/SongChange.pm
Xmms-Perl-0.12/typemap
Xmms-Perl-0.12/test1.mp3
Xmms-Perl-0.12/test2.mp3
Removing previously used /home/hn/.cpan/build/Xmms-Perl-0.12

  CPAN.pm: Going to build D/DO/DOUGM/Xmms-Perl-0.12.tar.gz

Checking if your kit is complete...
Looks good
Note (probably harmless): No library found for -lgtk
Note (probably harmless): No library found for -lgdk
Note (probably harmless): No library found for -lglib
Writing Makefile for Xmms::Config
Note (probably harmless): No library found for -lgtk
Note (probably harmless): No library found for -lgdk
Note (probably harmless): No library found for -lglib
Writing Makefile for Xmms::Remote
Note (probably harmless): No library found for -lgtk
Note (probably harmless): No library found for -lgdk
Note (probably harmless): No library found for -lglib
Writing Makefile for Xmms::SongChange
Writing Makefile for Xmms-Perl
cp lib/Xmms/ExtUtils.pm blib/lib/Xmms/ExtUtils.pm
cp lib/Bundle/Xmms.pm blib/lib/Bundle/Xmms.pm
cp lib/Xmms.pm blib/lib/Xmms.pm
make[1]: Entering directory `/home/hn/.cpan/build/Xmms-Perl-0.12/Config'
cp Config.pm ../blib/lib/Xmms/Config.pm
/usr/bin/perl /usr/share/perl/5.8.4/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap  Config.xs > Config.xsc && mv Config.xsc Config.c
Running Mkbootstrap for Xmms::Config ()
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"0.01\" -DXS_VERSION=\"0.01\" -fPIC "-I/usr/lib/perl/5.8/CORE"   Config.c
chmod 644 Config.bs
cp Config.bs ../blib/arch/auto/Xmms/Config/Config.bs
chmod 644 ../blib/arch/auto/Xmms/Config/Config.bs
Config.xs:5:29: xmms/configfile.h: No such file or directory
Config.xs:7: error: syntax error before '*' token
Config.xs:7: warning: data definition has no type or storage class
Config.c: In function `XS_Xmms__Config_new':
Config.c:70: error: `gchar' undeclared (first use in this function)
Config.c:70: error: (Each undeclared identifier is reported only once
Config.c:70: error: for each function it appears in.)
Config.c:70: error: `filename' undeclared (first use in this function)
Config.c:71: error: syntax error before "RETVAL"
Config.c:76: error: syntax error before ')' token
Config.xs:44: error: `RETVAL' undeclared (first use in this function)
Config.c: In function `XS_Xmms__Config_DESTROY':
Config.c:101: error: syntax error before "cfg"
Config.c:105: error: `cfg' undeclared (first use in this function)
Config.c:105: error: called object is not a function
Config.c: In function `XS_Xmms__Config_write_file':
Config.c:122: error: syntax error before "cfg"
Config.c:123: error: `gchar' undeclared (first use in this function)
Config.c:123: error: `filename' undeclared (first use in this function)
Config.c:123: error: syntax error before ')' token
Config.c:124: error: `gboolean' undeclared (first use in this function)
Config.c:124: error: syntax error before "RETVAL"
Config.c:129: error: `cfg' undeclared (first use in this function)
Config.c:129: error: called object is not a function
Config.c:134: error: `RETVAL' undeclared (first use in this function)
Config.c: In function `XS_Xmms__Config_remove_key':
Config.c:147: error: syntax error before "cfg"
Config.c:148: error: `gchar' undeclared (first use in this function)
Config.c:148: error: `section' undeclared (first use in this function)
Config.c:148: error: syntax error before ')' token
Config.c:149: error: `key' undeclared (first use in this function)
Config.c:149: error: syntax error before ')' token
Config.c:153: error: `cfg' undeclared (first use in this function)
Config.c:153: error: called object is not a function
Config.c: In function `XS_Xmms__Config_read':
Config.c:170: error: syntax error before "cfg"
Config.c:171: error: `gchar' undeclared (first use in this function)
Config.c:171: error: `section' undeclared (first use in this function)
Config.c:171: error: syntax error before ')' token
Config.c:172: error: `key' undeclared (first use in this function)
Config.c:172: error: syntax error before ')' token
Config.xs:77: error: `value' undeclared (first use in this function)
Config.c:181: error: `cfg' undeclared (first use in this function)
Config.c:181: error: called object is not a function
Config.c: In function `XS_Xmms__Config_write':
Config.c:207: error: syntax error before "cfg"
Config.c:208: error: `gchar' undeclared (first use in this function)
Config.c:208: error: `section' undeclared (first use in this function)
Config.c:208: error: syntax error before ')' token
Config.c:209: error: `key' undeclared (first use in this function)
Config.c:209: error: syntax error before ')' token
Config.c:210: error: `value' undeclared (first use in this function)
Config.c:210: error: syntax error before ')' token
Config.c:214: error: `cfg' undeclared (first use in this function)
Config.c:214: error: called object is not a function
make[1]: *** [Config.o] Error 1
make[1]: Leaving directory `/home/hn/.cpan/build/Xmms-Perl-0.12/Config'
make: *** [subdirs] Error 2
  /usr/bin/make -j3 -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
```

---

### Post by Red Sparrow on 2005-06-07
```
Config.xs:5:29: xmms/configfile.h: No such file or directory
``` 

This line's probably the culprit.  According to packages.ubuntu.com, you can get the file by installing the xmms-dev package.

(- Steve -)

---

### Post by Kyral on 2005-06-07
Actually, its the libxmms-perl package :D

Had the same problem until I found out that package exists

---

### Post by Musagetes on 2005-06-07
[QUOTE=Kyral]Actually, its the libxmms-perl package :D[/QUOTE]
Well, apt-get install xmms-dev did the trick nonetheless. I'm guessing libxmms-perl was installed aswell due to dependencies. :)

But thanks for the help, both of you, it's sorted now!

---

