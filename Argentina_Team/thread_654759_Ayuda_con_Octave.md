---
title: "Ayuda con Octave"
date: 2007-12-31
forum: Argentina Team
---

### Post by lordpuppet on 2007-12-31
Hola, desde la noticia de la publicación de la nueva versión de Octave, la 3.0 estoy intentando instalarla.

Tengo Ubuntu 7.10. Cuando busco "Octave" en el Synaptic me aparece la versión 2.9 asi que decidí bajar y compilar el tar, algo que detesto hacer por que siempre me falta algo en el sistema para compilar, siempre hay un error en el .configure o en el install y esta vez no fue la excepción.

Buscando en la pagina de Downloads de Octave hay una mención hacia instaladores binarios, pero no hay ningun link y no encontré nada buscando en internet.

Donde puedo encontrar un binario de esta ultima versión, o hacer algo para actualizar el synaptic para que me aparezca la 3.0? por que compilar es lo último que pienso hacer.

---

### Post by faktorqm on 2007-12-31
no se que es octave, pero compilar es muy simple. no veo por que es lo ultimo que queres hacer...
si queres te ayudo a eso, como tantos otros aca en el foro que seguro tienen ganas de hacerlo....
postea basicamente la salida del ./configure y a partir de ahi lo vemos. no siempre hay .deb's para todo..... 
por favor, si lo haces acordate de poner la salida entre tags de code. salu2!

---

### Post by nemodot on 2007-12-31
Lo que me molesta de compilar es que siempre falta algo, he pasado dias enteros instalando cosas para hacer andar otras cosas que despues apenas funcionan.

Y también no me gusta que quede la carpeta que descomprimi, el tar.gz en mi Home, después no se puede eliminar, y se junta ahi.

Pero de todos modos pongo el error que me muestra el terminal:

```
esteban@esteban-desktop:~$ cd octave-3.0.0
esteban@esteban-desktop:~/octave-3.0.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for AIX... no
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking for library containing strerror... none required
defining man1dir to be $(mandir)/man1
defining man1ext to be .1
defining infofile to be $(infodir)/octave.info
defining octincludedir to be $(includedir)/octave-$(version)
defining fcnfiledir to be $(datadir)/octave/$(version)/m
defining localfcnfiledir to be $(datadir)/octave/site/m
defining localapifcnfiledir to be $(datadir)/octave/site/$(api_version)/m
defining localverfcnfiledir to be $(datadir)/octave/$(version)/site/m
defining octlibdir to be $(libdir)/octave-$(version)
defining archlibdir to be $(libexecdir)/octave/$(version)/exec/$(canonical_host_type)
defining localarchlibdir to be $(libexecdir)/octave/site/exec/$(canonical_host_type)
defining localapiarchlibdir to be $(libexecdir)/octave/$(api_version)/site/exec/$(canonical_host_type)
defining localverarchlibdir to be $(libexecdir)/octave/$(version)/site/exec/$(canonical_host_type)
defining octfiledir to be $(libexecdir)/octave/$(version)/oct/$(canonical_host_type)
defining localoctfiledir to be $(libexecdir)/octave/site/oct/$(canonical_host_type)
defining localapioctfiledir to be $(libexecdir)/octave/site/oct/$(api_version)/$(canonical_host_type)
defining localveroctfiledir to be $(libexecdir)/octave/$(version)/site/oct/$(canonical_host_type)
defining imagedir to be $(datadir)/octave/$(version)/imagelib
configure: defining __NO_MATH_INLINES avoids buggy GNU libc exp function
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for C++ support for new friend template declaration... yes
checking if C++ library is ISO compliant... yes
checking for broken C++ reinterpret_cast... no
checking for nm... nm
checking C++ ABI version used by g++... gnu_v3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking whether gcc accepts -mieee-fp... yes
configure: adding -mieee-fp to XTRA_CFLAGS
checking whether g++ accepts -mieee-fp... yes
configure: adding -mieee-fp to XTRA_CXXFLAGS
checking whether g++ prepends an underscore to external names... no
checking for sin in -lm... yes
checking qhull/qhull_a.h usability... no
checking qhull/qhull_a.h presence... no
checking for qhull/qhull_a.h... no
configure: WARNING: Qhull library not found --- This will result in loss of functionality of some geometry functions.
checking for pcre-config... no
checking whether pcre.h defines the macros we need... no
configure: WARNING: PCRE library not found.  This will result in some loss of functionality for the regular expression matching functions.
checking for regexec... yes
checking for regexec... (cached) yes
checking for gzclearerr in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for H5Pcreate in -lhdf5... no
configure: WARNING: HDF5 library not found.  Octave will not be able to save or load HDF5 data files.
checking fftw3.h usability... no
checking fftw3.h presence... no
checking for fftw3.h... no
FFTW library not found.  Octave will use the (slower) FFTPACK library instead.
checking glpk/glpk.h usability... no
checking glpk/glpk.h presence... no
checking for glpk/glpk.h... no
checking glpk.h usability... no
checking glpk.h presence... no
checking for glpk.h... no
checking for curl_easy_escape in -lcurl... no
checking for IEEE 754 data format... yes
checking for ranlib... ranlib
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
checking how to get verbose linking output from ... configure: WARNING: compilation failed

checking for Fortran 77 libraries of ... 
checking for dummy main to link with Fortran 77 libraries... none
checking for Fortran 77 name-mangling scheme... configure: error: cannot compile a simple Fortran program
See `config.log' for more details.

```

PD: Octave es un programa estilo matlab para cálculo numerico, y segun dicen, es el mejor en linux.

---

### Post by faktorqm on 2007-12-31
viste que era facil? bastaba con hacer ```
aptitude search fortran
``` y ver que hay un paquete que se llama "fortran77-compiler" (o compilador de fortran 77)....  el .configure te dice que te falta el compilador de fortran 77...... tenes un paquete por instalar :D

hacete ```
sudo aptitude install fortran77-compiler
```

feliz año!!

---

### Post by lordpuppet on 2008-01-01
Despues de un rato de intentar instalar ese paquete, encontré que se llamaba, en realidad g77. Lo instalé y después de un larguisimo checking con muchos "si", pero algunos "no" salio este error:

```
configure: WARNING: I couldn't find -ltermcap, -lterminfo, -lncurses, -lcurses, or -ltermlib!
checking for rl_set_keyboard_input_timeout in -lreadline... no
configure: WARNING: I need GNU Readline 4.2 or later
configure: error: this is fatal unless you specify --disable-readline

```

---

### Post by Hei Ku on 2008-01-01
ponele:

sudo apt-get install libreadline5-dev

y proba de vuelta. Y si, muchas veces es un poco de prueba y error hasta enganchar todas las bibliotecas y paquetes necesarios.

---

### Post by lordpuppet on 2008-01-02
Después de instalar todas las librerias y programas que parecen faltar me sale estos "WARNING" pero no se de que librerias se tratan.

No deberían indicar en la pagina de donde uno baja el tar.gz qué librerias hay que instalar antes de compilar el programa?

```
configure: WARNING: I didn't find gperf, but it's only a problem if you need to reconstruct oct-gperf.h
configure: WARNING: I didn't find flex, but it's only a problem if you need to reconstruct lex.cc
configure: WARNING: I didn't find bison, but it's only a problem if you need to reconstruct parse.cc
configure: WARNING: UMFPACK not found.  This will result in some lack of functionality for sparse matrices.
configure: WARNING: COLAMD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CCOLAMD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CHOLMOD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CXSparse not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: FFTW library not found.  Octave will use the (slower) FFTPACK library instead.
configure: WARNING: GLPK library not found.  The glpk function for solving linear programs will be disabled.
configure: WARNING: HDF5 library not found.  Octave will not be able to save or load HDF5 data files.
configure: WARNING: PCRE library not found.  This will result in some loss of functionality for the regular expression matching functions.
configure: WARNING: Qhull library not found --- This will result in loss of functionality of some geometry functions.
configure: WARNING: I didn't find makeinfo, but it's only a problem if you need to reconstruct the Info version of the manual
configure: WARNING: I didn't find texi2dvi, but it's only a problem if you need to reconstruct the DVI version of the manual
configure:

NOTE: libraries may be skipped if a library is not found OR
      if the library on your system is missing required features.

```

---

### Post by faktorqm on 2008-01-02
Hola, busca cada cosa con "aptitude search":

```

faktorqm@theship:~$ aptitude search gperf
i   gnome-icon-theme-gperfection2   - icon theme for GTK+ 2.x                   
p   gperf                           - Perfect hash function generator           
p   gperf-ace                       - ACE perfect hash function generator       
p   gtk-clearlooks-gperfection2-the - gtk theme for the clearlooks engine       
faktorqm@theship:~$ aptitude search flex
p   cl-flexi-streams                - Flexi-streams: Flexible bivalent streams f
p   flex                            - A fast lexical analyzer generator.        
p   flex-doc                        - Documentation for flex (a fast lexical ana
p   flex-old                        - The old version of the fast lexical analyz
p   flex-old-doc                    - Documentation for an old flex (a fast lexi
p   flexbackup                      - Flexible backup tool for small to medium s
p   flexloader                      - utility to configure SRAM based ALTERA dev
v   flexmem                         -                                           
p   flexml                          - generate fast validating XML processors an
p   jflex                           - lexical analyzer generator for Java       
p   libcflexplugin                  - MuscleCard Cryptoflex PlugIn              
p   libslbreflex-dev                - Reflex 62/64 smartcard reader CT-API devel
p   libslbreflex2                   - Reflex 62/64 smartcard reader PCSC and CT-
faktorqm@theship:~$ aptitude search bison
p   bison                           - A parser generator that is compatible with
p   bison++                         - Generate a parser in c or c++ from BNF not
p   bison-1.35                      - A parser generator that is compatible with
p   bison-doc                       - Documentation for the Bison parser generat
p   bisonc++                        - Bison-style parser generator for C++      
faktorqm@theship:~$ aptitude search fftw
p   fftw-dev                        - library for computing Fast Fourier Transfo
p   fftw-docs                       - documentation for fftw                    
v   fftw-double-dev                 -                                           
v   fftw-single-dev                 -                                           
p   fftw2                           - library for computing Fast Fourier Transfo
v   fftw2-double                    -                                           
v   fftw2-single                    -                                           
i A fftw3                           - library for computing Fast Fourier Transfo
p   fftw3-dev                       - library for computing Fast Fourier Transfo
p   fftw3-doc                       - documentation for fftw version 3          
p   k6fftwgel-dev                   - library for computing Fast Fourier Transfo
p   k6fftwgel2                      - library for computing Fast Fourier Transfo
p   k7fftwgel-dev                   - library for computing Fast Fourier Transfo
p   k7fftwgel2                      - library for computing Fast Fourier Transfo
p   mffm-fftw-dev                   - A C++ wrapper for the fftw.org C library (
p   mffm-fftw1c2                    - A C++ wrapper for the fftw.org C library (
p   p4fftwgel-dev                   - library for computing Fast Fourier Transfo
p   p4fftwgel2                      - library for computing Fast Fourier Transfo
p   sfftw-dev                       - library for computing Fast Fourier Transfo
p   sfftw2                          - library for computing Fast Fourier Transfo
faktorqm@theship:~$ aptitude search umfpack
v   libumfpack                      -                                           
p   libumfpack4                     - set of routines for solving unsymmetric sp
p   libumfpack4-dev                 - set of routines for solving unsymmetric sp
p   libumfpack4-doc                 - set of routines for solving unsymmetric sp

```

y despues agarras y seguis buscando las otras y despues vas haciendo por ejemplo:

```
sudo aptitude install flex bison fftw3 libumfpack4
```

y asi todo todo hasta que el configure ande bien. fftw por ejemplo es para hacer la transformada rapida de fourier. salu2!

---

### Post by lordpuppet on 2008-01-02
Gracias por la ayuda, aunque tuve más exito buscando con el synaptic, el aptitude search no me encontraba nada a veces por que "colamd" por ejemplo, no es una libreria en si, son las iniciales que describen un tipo de librerias para el calculo de matrices.

---

### Post by faktorqm on 2008-01-02
buenisimo, siempre me mando la misma .... con el synaptic es mejor buscar... salu2! y suerte con eso.

---

### Post by lordpuppet on 2008-01-04
Bueno, instalé casi todo lo que faltaba, lo único que me faltó y no encontré eran unas cosas para leer el manual de octave asi que no le di bola.

Hice sudo make y me tiro 2 errores, copio la parte final de make por que es muy larga:

```
make[2]: se sale del directorio `/home/esteban/octave-3.0.0/examples'
make -C doc ../INSTALL.OCTAVE
make[2]: se ingresa al directorio `/home/esteban/octave-3.0.0/doc'
make -C interpreter ../../INSTALL.OCTAVE
make[3]: se ingresa al directorio `/home/esteban/octave-3.0.0/doc/interpreter'
make -C ../../src DOCSTRINGS
make[4]: se ingresa al directorio `/home/esteban/octave-3.0.0/src'
making defaults.h from defaults.h.in
defaults.h is unchanged
making oct-conf.h from oct-conf.h.in
oct-conf.h is unchanged
making DOCSTRINGS
DOCSTRINGS is unchanged
make[4]: se sale del directorio `/home/esteban/octave-3.0.0/src'
make -C ../../scripts DOCSTRINGS
make[4]: se ingresa al directorio `/home/esteban/octave-3.0.0/scripts'
make[4]: `DOCSTRINGS' está actualizado.
make[4]: se sale del directorio `/home/esteban/octave-3.0.0/scripts'
making install.texi from install.txi
install.texi is unchanged
rm -f INSTALL
../../missing makeinfo -D INSTALLONLY \
          --no-validate --no-headers --no-split --output INSTALL \
          -I.. -I. -I./.. install.texi
make[3]: ../../missing: No se encontró el programa
make[3]: [../../INSTALL.OCTAVE] Error 127 (no tiene efecto)
mv INSTALL ../../INSTALL.OCTAVE
mv: no se puede efectuar `stat' sobre `INSTALL': No existe el fichero ó directorio
make[3]: *** [../../INSTALL.OCTAVE] Error 1
make[3]: se sale del directorio `/home/esteban/octave-3.0.0/doc/interpreter'
make[2]: *** [../INSTALL.OCTAVE] Error 2
make[2]: se sale del directorio `/home/esteban/octave-3.0.0/doc'
make[1]: *** [INSTALL.OCTAVE] Error 2
make[1]: se sale del directorio `/home/esteban/octave-3.0.0'
make: *** [all] Error 2
```

La verdad que no tengo ni idea que error existe.

---

### Post by faktorqm on 2008-01-04
che es como que dice que no encontro el programa missing. la verdad ni idea, pero tengo 2 teorias, o que es alguno de estos paquetes (o los tres)(missingh-doc ó libghc6-missingh-dev ó libghc6-hdbc-missingh-dev) o que el programa missing debe venir nombrado en el makefile pero no en el source, como no lo encuentra sale con error y es bug que tenes que reportar a la gente de octave. Es mas seguro que sea la primera opcion. como estas compilando? te recuerdo que para la mayoria de las distribuciones debian o basadas en debian las compilaciones se hacen como (en general)

```
./configure --prefix=/usr
```
```
make --prefix=/usr
```
```
sudo make install
```

Salu2 y dale gas que ya sale eh!! :D

---

### Post by lordpuppet on 2008-01-04
Simplemente estoy haciendo sudo ./configure y luego sudo make, no se que es eso con prefix.

Bueno, este es el problema a que me refiero con compilar, es muy largo y tedioso y la mayor de las veces frustrante, le di para adelante por que en los repositorios no estaba el binario del octave 3 (estaba el del 2.9). Asi que voy a esperar un poco y cuando lo pongan me va a bastar hacer:

sudo apt-get install octave:popcorn:


Gracias por la ayuda igual.

---

### Post by Hei Ku on 2008-01-05
al hacer configure tenes que agregarle el prefix, nada mas:


./configure --prefix=/usr


proba eso, y despues make, a ver q pasa.
Pensa q no es solo por vos, sino tambien por otros que quieran compilarlo. :)

---

