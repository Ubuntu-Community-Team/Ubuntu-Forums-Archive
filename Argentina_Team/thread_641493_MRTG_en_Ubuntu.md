---
title: "MRTG en Ubuntu"
date: 2007-12-15
forum: Argentina Team
---

### Post by matlnx on 2007-12-15
BUenas tardes, necesitaría saber si alguno conoce o tiene un manual para poder instalar MRTG en Ubuntu 7.10.

Encontre uno en la pagina de MRTG para distros basadas en Debian pero hace un tiempo recuerdo que tuve problemas y no pude hacerlo funcionar.

Obviamente San Google no pudo brindarme la información necesaria ;)

Se agradece cualquier tipo de dato, ya que necesito hacerlo funcionar para monitorear unos Switches Cisco 2950 y poder agregar el MRTG como módulo de Nagios 3.

Muchas gracias nuevamente.
Sds
MatLnx

---

### Post by faktorqm on 2007-12-17
Hola, bueno, soy un g*l a bateria recargable..... te cuento, escribi el post que ves abajo y despues descubri algo muy malo (para mi).

```
sudo aptitude install mrtg
```

Estoy re caliente jajajaj Igual, te explico paso a paso como lo instale:

[SIZE="4"]**SRES. ADMINS: TIENEN UN NUEVO TUTO PARA LA NUEVA SECCION DE TUTOS DE LA PAGINA DE UBUNTU-AR**[/SIZE] :KS

1) me baje este archivo : [http://oss.oetiker.ch/mrtg/pub/mrtg-2.15.2.tar.gz](http://oss.oetiker.ch/mrtg/pub/mrtg-2.15.2.tar.gz)
2) le di click derecho -> extraer aqui y me hizo una carpeta que se llama mrtg-2.15.2
3) entre y escribi "./configure" y me decia que me faltaba la biblioteca GD. (te adjunto la salida para que tengas referencia)

```

faktorqm@ttheedge:~/mrtg-2.15.2$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for groff... /usr/bin/groff
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for inttypes.h... (cached) yes
checking for unsigned long long... yes
checking for long long... yes
checking for strtoll... yes
checking for printf long long format specifier... %lld
checking for pow in -lm... yes
checking for gdImageGif in -lgd... no
checking for gdImagePng in -lgd... no
checking for gdImagePng_jpg in -lgd... no
checking for gdImagePng_jpg_ft in -lgd... no
checking for gdImageGd in -lgd... no
checking gd.h usability... no
checking gd.h presence... no
checking for gd.h... no

** Ooops, one of many bad things happened:

   a)  You don't have the GD library installed.
       Get it from http://www.boutell.com, compile it and
       use either --with-gd-lib=DIR and --with-gd-inc=DIR to specify
       its location. You might also have to use --with-z-inc,
             --with-z-lib and --with-png-inc, --with-png-lib for gd
             versions 1.6 and higher.  Check config.log for more
       information on the problem.

   b)  You have the GD library installed, but not the gd.h
       header file.  Download the source (see above) and use
       --with-gd-inc=DIR to specify where the file can be found.

   c)  You have the library and the header file installed, but
       you also have a shared GD library in the same directory. 
       Remove the shared library files and/or links (e.g. 
       libgd.so.2.0.0, libgd.so and libgd.so.2).  This is especially
             likely if you're using a recent (post 1.8.4) version of GD
       and didn't configure it with --disable-shared.

   d)  You have gd library installed and also it's headers, but you are
       missing libpng (and headers) or freetype (and headers)
       (mrtg does not use freetype, but if your copy of gd is precompiled
       against it, you have to install it ... 

   Consider following the instructions in doc/mrtg-unix-guide.txt
faktorqm@ttheedge:~/mrtg-2.15.2$

```

4) Entonces abri el archivito ese que dice ahi que es la guia de como se instala xD y en una parte dice (copia textual):

```

       gd  This is a basic graph drawing library created by Thomas Boutell.
           Note that all releases after Version 1.3 only create PNG images.
           This is because a) Thomas got into trouble because the GIF format
           which it used to produce uses a compression technology patented by
           Unisys. b) PNG is more efficient and patent free. MRTG can work
           with old and new version of the GD library. You can get a recent
           copy of GD from:

            http://www.boutell.com/gd/

```

5) Fui a [http://www.libgd.org/releases/gd-2.0.35.tar.gz](http://www.libgd.org/releases/gd-2.0.35.tar.gz) a bajarme el gd por que no lo encontre en los repos de ubuntu. el que si encontre es el soporte para xpm que el paquete original no lo trae (me estan cargando?!?!) ok!!

6) click derecho sobre el archivo -> extraer aqui y te arma una carpeta que se llama gd-2.0.35

7) entras a esa carpeta y le das derecho al "./configure" y tiene que pasar algo como esto:

```

faktorqm@ttheedge:~/gd-2.0.35$ ./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking if we are building a Cygwin target... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for X... libraries , headers 
checking for ANSI C header files... (cached) yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking iconv.h usability... yes
checking iconv.h presence... yes
checking for iconv.h... yes
checking whether iconv.h defines iconv_t... yes
checking for sin... no
checking for sin in -lm... yes
checking for deflate in -lz... yes
checking for libpng12-config... /usr/bin/libpng12-config
checking for libpng-config... /usr/bin/libpng-config
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for png_create_read_struct in -lpng12... yes
checking for freetype-config... /usr/bin/freetype-config
checking for FT_Init_FreeType in -lfreetype... yes
checking ft2build.h usability... yes
checking ft2build.h presence... yes
checking for ft2build.h... yes
checking for FcInit in -lfontconfig... yes
checking for jpeg_set_defaults in -ljpeg... yes
checking for XpmReadFileToXpmImage in -lXpm... no
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no

** Configuration summary for gd 2.0.34:

   Support for PNG library:          yes
   Support for JPEG library:         yes
   Support for Freetype 2.x library: yes
   Support for Fontconfig library:   yes
   Support for Xpm library:          no
   Support for pthreads:             yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating config/Makefile
config.status: creating config/gdlib-config
config.status: creating test/Makefile
config.status: creating config.h
config.status: executing depfiles commands
faktorqm@ttheedge:~/gd-2.0.35$ 

```

8) Acto seguido, escribis "make" y le das enter. La salida es horrible, pero no te preocupes, es normal. Vas a ver que primero hace automaticamente otro configure y cuando termina empieza a compilar. el ultimo pedazo de salida es este:

```

if gcc -DHAVE_CONFIG_H -I. -I. -I.   -I/usr/include/freetype2   -g -O2 -MT fontconfigtest.o -MD -MP -MF ".deps/fontconfigtest.Tpo" -c -o fontconfigtest.o fontconfigtest.c; \
        then mv -f ".deps/fontconfigtest.Tpo" ".deps/fontconfigtest.Po"; else rm -f ".deps/fontconfigtest.Tpo"; exit 1; fi
/bin/bash ./libtool --tag=CC --mode=link gcc  -g -O2  -L/usr/lib  -o fontconfigtest  fontconfigtest.o ./libgd.la  -ljpeg -lfontconfig -lfreetype -lpng12 -lz -lm 
gcc -g -O2 -o .libs/fontconfigtest fontconfigtest.o  -L/usr/lib ./.libs/libgd.so /usr/lib/libjpeg.so /usr/lib/libfreetype.so -lfontconfig -lpng12 -lm -lz -Wl,--rpath -Wl,/usr/local/lib
creating fontconfigtest
if gcc -DHAVE_CONFIG_H -I. -I. -I.   -I/usr/include/freetype2   -g -O2 -MT gifanimtest.o -MD -MP -MF ".deps/gifanimtest.Tpo" -c -o gifanimtest.o gifanimtest.c; \
        then mv -f ".deps/gifanimtest.Tpo" ".deps/gifanimtest.Po"; else rm -f ".deps/gifanimtest.Tpo"; exit 1; fi
/bin/bash ./libtool --tag=CC --mode=link gcc  -g -O2  -L/usr/lib  -o gifanimtest  gifanimtest.o ./libgd.la  -ljpeg -lfontconfig -lfreetype -lpng12 -lz -lm 
gcc -g -O2 -o .libs/gifanimtest gifanimtest.o  -L/usr/lib ./.libs/libgd.so /usr/lib/libjpeg.so /usr/lib/libfreetype.so -lfontconfig -lpng12 -lm -lz -Wl,--rpath -Wl,/usr/local/lib
creating gifanimtest
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make[2]: se sale del directorio `/home/faktorqm/gd-2.0.35'
make[1]: se sale del directorio `/home/faktorqm/gd-2.0.35'
faktorqm@ttheedge:~/gd-2.0.35$ 

```

eso quiere decir que hizo todo bien. 

9) Hacemos "sudo make install" para terminar la instalacion del gd. Y tiene que darte algo asi:

```

faktorqm@ttheedge:~/gd-2.0.35$ sudo make install
Password:
Making install in config
make[1]: se ingresa al directorio `/home/faktorqm/gd-2.0.35/config'
make[2]: se ingresa al directorio `/home/faktorqm/gd-2.0.35/config'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
 /usr/bin/install -c 'gdlib-config' '/usr/local/bin/gdlib-config'
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/home/faktorqm/gd-2.0.35/config'
make[1]: se sale del directorio `/home/faktorqm/gd-2.0.35/config'
Making install in test
make[1]: se ingresa al directorio `/home/faktorqm/gd-2.0.35/test'
make[2]: se ingresa al directorio `/home/faktorqm/gd-2.0.35/test'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/home/faktorqm/gd-2.0.35/test'
make[1]: se sale del directorio `/home/faktorqm/gd-2.0.35/test'
make[1]: se ingresa al directorio `/home/faktorqm/gd-2.0.35'
make[2]: se ingresa al directorio `/home/faktorqm/gd-2.0.35'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ./libtool --mode=install /usr/bin/install -c  'libgd.la' '/usr/local/lib/libgd.la'
/usr/bin/install -c .libs/libgd.so.2.0.0 /usr/local/lib/libgd.so.2.0.0
(cd /usr/local/lib && { ln -s -f libgd.so.2.0.0 libgd.so.2 || { rm -f libgd.so.2 && ln -s libgd.so.2.0.0 libgd.so.2; }; })
(cd /usr/local/lib && { ln -s -f libgd.so.2.0.0 libgd.so || { rm -f libgd.so && ln -s libgd.so.2.0.0 libgd.so; }; })
/usr/bin/install -c .libs/libgd.lai /usr/local/lib/libgd.la
/usr/bin/install -c .libs/libgd.a /usr/local/lib/libgd.a
chmod 644 /usr/local/lib/libgd.a
ranlib /usr/local/lib/libgd.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /bin/bash ./libtool --mode=install /usr/bin/install -c 'annotate' '/usr/local/bin/annotate'
/usr/bin/install -c .libs/annotate /usr/local/bin/annotate
  /bin/bash ./libtool --mode=install /usr/bin/install -c 'gdparttopng' '/usr/local/bin/gdparttopng'
/usr/bin/install -c .libs/gdparttopng /usr/local/bin/gdparttopng
  /bin/bash ./libtool --mode=install /usr/bin/install -c 'gdtopng' '/usr/local/bin/gdtopng'
/usr/bin/install -c .libs/gdtopng /usr/local/bin/gdtopng
  /bin/bash ./libtool --mode=install /usr/bin/install -c 'gd2copypal' '/usr/local/bin/gd2copypal'
/usr/bin/install -c .libs/gd2copypal /usr/local/bin/gd2copypal
  /bin/bash ./libtool --mode=install /usr/bin/install -c 'gd2topng' '/usr/local/bin/gd2topng'
/usr/bin/install -c .libs/gd2topng /usr/local/bin/gd2topng
  /bin/bash ./libtool --mode=install /usr/bin/install -c 'pngtogd' '/usr/local/bin/pngtogd'
/usr/bin/install -c .libs/pngtogd /usr/local/bin/pngtogd
  /bin/bash ./libtool --mode=install /usr/bin/install -c 'pngtogd2' '/usr/local/bin/pngtogd2'
/usr/bin/install -c .libs/pngtogd2 /usr/local/bin/pngtogd2
  /bin/bash ./libtool --mode=install /usr/bin/install -c 'webpng' '/usr/local/bin/webpng'
/usr/bin/install -c .libs/webpng /usr/local/bin/webpng
  /bin/bash ./libtool --mode=install /usr/bin/install -c 'gd2togif' '/usr/local/bin/gd2togif'
/usr/bin/install -c .libs/gd2togif /usr/local/bin/gd2togif
  /bin/bash ./libtool --mode=install /usr/bin/install -c 'gdcmpgif' '/usr/local/bin/gdcmpgif'
/usr/bin/install -c .libs/gdcmpgif /usr/local/bin/gdcmpgif
  /bin/bash ./libtool --mode=install /usr/bin/install -c 'giftogd2' '/usr/local/bin/giftogd2'
/usr/bin/install -c .libs/giftogd2 /usr/local/bin/giftogd2
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
 /usr/bin/install -c 'bdftogd' '/usr/local/bin/bdftogd'
 /usr/bin/install -c 'config/gdlib-config' '/usr/local/bin/gdlib-config'
test -z "/usr/local/include" || mkdir -p -- "/usr/local/include"
 /usr/bin/install -c -m 644 'gd.h' '/usr/local/include/gd.h'
 /usr/bin/install -c -m 644 'gdfx.h' '/usr/local/include/gdfx.h'
 /usr/bin/install -c -m 644 'gd_io.h' '/usr/local/include/gd_io.h'
 /usr/bin/install -c -m 644 'gdcache.h' '/usr/local/include/gdcache.h'
 /usr/bin/install -c -m 644 'gdfontg.h' '/usr/local/include/gdfontg.h'
 /usr/bin/install -c -m 644 'gdfontl.h' '/usr/local/include/gdfontl.h'
 /usr/bin/install -c -m 644 'gdfontmb.h' '/usr/local/include/gdfontmb.h'
 /usr/bin/install -c -m 644 'gdfonts.h' '/usr/local/include/gdfonts.h'
 /usr/bin/install -c -m 644 'gdfontt.h' '/usr/local/include/gdfontt.h'
 /usr/bin/install -c -m 644 'entities.h' '/usr/local/include/entities.h'
make[2]: se sale del directorio `/home/faktorqm/gd-2.0.35'
make[1]: se sale del directorio `/home/faktorqm/gd-2.0.35'
faktorqm@ttheedge:~/gd-2.0.35$ 

```

10) Volvemos al directorio del mrtg y hacemos "./configure" again:

```

faktorqm@ttheedge:~/mrtg-2.15.2$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for groff... /usr/bin/groff
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for inttypes.h... (cached) yes
checking for unsigned long long... yes
checking for long long... yes
checking for strtoll... yes
checking for printf long long format specifier... %lld
checking for pow in -lm... yes
checking for gdImageGif in -lgd... yes
checking for gdImagePng in -lgd... yes
checking for gdImagePng_jpg in -lgd... no
checking for gdImagePng_jpg_ft in -lgd... no
checking for gdImageGd in -lgd... yes
checking gd.h usability... yes
checking gd.h presence... yes
checking for gd.h... yes
checking the weather... (cached) it's fine
checking if we can use GCC-specific compiler options... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
ordering CD from http://people.ee.ethz.ch/~oetiker/wish .... just kidding ;-)

----------------------------------------------------------------
Config is DONE!

Type 'make' to compile the software

       ... that wishlist mentioned above does really exist. So if
you feel like showing your appreciation for MRTG, this is the
place to go. I just love CDs and DVDs

                            -- Tobi Oetiker <oetiker@ee.ethz.ch>
----------------------------------------------------------------
faktorqm@ttheedge:~/mrtg-2.15.2$ 

```

Bueno, como veras termino todo bien,

11) le damos al make entonces: (para mi sorpresa fue una salida re corta)

```

faktorqm@ttheedge:~/mrtg-2.15.2$ make
gcc -DGFORM_GD=gdImagePng -g -O2 -Wall -Wpointer-arith -Wcast-align -Wmissing-declarations -Wnested-externs -Winline -W -DHAVE_CONFIG_H -c ./src/rateup.c -o bin/rateup.o
LD_RUN_PATH= gcc bin/rateup.o -o bin/rateup   -Wl,-Bstatic -lgd -lpng -lz -Wl,-Bdynamic  -lm 
/usr/bin/perl -0777 -p -i~ -e "s'^#!\s*/\S*perl'#! /usr/bin/perl'" ./bin/cfgmaker ./bin/indexmaker ./bin/mrtg
/usr/bin/perl -0777 -p -i~ -e 's@GRAPHFMT="...";@GRAPHFMT="png";@' ./bin/mrtg ./bin/indexmaker
faktorqm@ttheedge:~/mrtg-2.15.2$ 

```

12) le damos al sudo make install:

```

faktorqm@ttheedge:~/mrtg-2.15.2$ sudo make install
/usr/bin/perl -0777 -p -i~ -e "s'^#!\s*/\S*perl'#! /usr/bin/perl'" ./bin/cfgmaker ./bin/indexmaker ./bin/mrtg
/usr/bin/perl -0777 -p -i~ -e 's@GRAPHFMT="...";@GRAPHFMT="png";@' ./bin/mrtg ./bin/indexmaker
/bin/sh ./mkinstalldirs /usr/local/mrtg-2/bin
mkdir /usr/local/mrtg-2
mkdir /usr/local/mrtg-2/bin
for x in ./bin/mrtg ./bin/cfgmaker ./bin/indexmaker ./bin/mrtg-traffic-sum; do \
          /usr/bin/install -c -m 755 $x /usr/local/mrtg-2/bin; done
for x in bin/rateup; do \
          /usr/bin/install -c -m 755 $x /usr/local/mrtg-2/bin; done
/bin/sh ./mkinstalldirs /usr/local/mrtg-2/lib/mrtg2/Pod
mkdir /usr/local/mrtg-2/lib
mkdir /usr/local/mrtg-2/lib/mrtg2
mkdir /usr/local/mrtg-2/lib/mrtg2/Pod
for x in ./lib/mrtg2/*.pm; do \
          /usr/bin/install -c -m 644 $x /usr/local/mrtg-2/lib/mrtg2; done
for x in ./lib/mrtg2/Pod/*.pm; do \
          /usr/bin/install -c -m 644 $x /usr/local/mrtg-2/lib/mrtg2/Pod; done
/bin/sh ./mkinstalldirs /usr/local/mrtg-2/share/mrtg2/icons
mkdir /usr/local/mrtg-2/share
mkdir /usr/local/mrtg-2/share/mrtg2
mkdir /usr/local/mrtg-2/share/mrtg2/icons
for x in ./images/*.gif ./images/*.png; do \
          /usr/bin/install -c -m 644 $x /usr/local/mrtg-2/share/mrtg2/icons; done
/bin/sh ./mkinstalldirs /usr/local/mrtg-2/share/doc/mrtg2
mkdir /usr/local/mrtg-2/share/doc
mkdir /usr/local/mrtg-2/share/doc/mrtg2
(cd .; for x in COPYING COPYRIGHT README CHANGES THANKS doc/*.pod doc/*.txt doc/*.png; do \
          /usr/bin/install -c -m 644 $x /usr/local/mrtg-2/share/doc/mrtg2; done)
/bin/sh ./mkinstalldirs /usr/local/mrtg-2/man/man1
mkdir /usr/local/mrtg-2/man
mkdir /usr/local/mrtg-2/man/man1
for x in ./doc/*.1; do \
          /usr/bin/install -c -m 644 $x /usr/local/mrtg-2/man/man1; done
faktorqm@ttheedge:~/mrtg-2.15.2$ 

```

13) Esperaba que esta cosa al menos me haga un link en Aplicaciones, pero ni eso, asi que para probarlo probalo vos por que dice que hay que hacer un archivo de configuracion con el comando "cfgmaker" y despues correr el programa indicandole el path y demas... y la verdad ya fue demasiado por esta mañana para mi.

Como siempre, espero que te haya servido, abrazo y salu2!!

p.d.: me olvide de algo, para compilar todo esto necesitas ```
sudo aptitude install build-essential
``` si te faltan cosas, postea y lo vemos. Salu2!!

---

