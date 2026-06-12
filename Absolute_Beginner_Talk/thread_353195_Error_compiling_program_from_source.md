---
title: "Error compiling program from source"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by KentS on 2007-02-04
I'm trying to install [ROOT]("http://root.cern.ch/") from source. I've been following [these]("http://root.cern.ch/root/Install.html") instructions. When I try to build it using the first 'make'-command (instead of 'gmake'), I get the following message:

> bin/rmkdepend -R -fgraf/src/TTF.d -Y -w 1000 -- -pipe -Wall -W -Woverloaded-virtual -fPIC -Iinclude -DR__HAVE_CONFIG -pthread -Ifreetype/src/freetype-2.1.9/include -D__cplusplus -- graf/src/TTF.cxx
bin/rmkdepend: error:  cannot open ""
make: *** [graf/src/TTF.o] Error 1


Does anyone understand what the problem is? I'm running Ubuntu Dapper Drake.

I followed the instructions under "Getting the source" exactly (not the part about CVS). I skipped the part on "Getting ready to build" (libX* should be installed already). I chose installation method 2. I didn't follow the recommendations. Under point 2.2 I typed './configure --prefix=/usr/bin'.

---

### Post by ComplexNumber on 2007-02-04
> Under point 2.2 I typed './configure --prefix=/usr/bin'.theres part of your problem. that will be trying to look in /usr/bin/lib/pkgconfig (ie no such directory) to see if the right packages are installed, for example. it should be:
./configure --prefix=/usr

or

./configure





you misunderstood. what it actually said is that /usr/bin is where the binary will be installed.

---

### Post by KentS on 2007-02-04
Thanks for the suggestion, but it doesn't seem to help. I've tried to use both './configure' as well as './configure --prefix=/usr' and './configure --prefix=/usr/local'. Every time I get
> bin/rmkdepend: error:  cannot open ""
make: *** [graf/src/TTF.o] Error 1

I've typed the commands 'make uninstall' and 'sudo make uninstall' between each try.

---

### Post by lamego on 2007-02-04
Have you checked that ./configure does not return an error ?
I have tried and I had to install the following packages:
```
libxpm-dev
libx11-dev
libxext-dev
g77

```
It is compiling now...
Btw, "make uninstall" is not related to the compile process...

---

### Post by LKRaider on 2007-02-04
Did you install the libxpm-dev package?


If that doesn't suffice, it might be the case of asking this at their mailinglist.

---

### Post by ComplexNumber on 2007-02-04
i've downloaded and have just typed in ./configure --prefix=/usr

unfortunately, i can't replicate what you get. it configured quickly with no problem whatsoever. after that i typed in make. again, no problem whatsoever. at the end of the configure process, it gave this:
> Enabled support for asimage, astiff, builtin_afterimage, builtin_freetype, builtin_pcre, builtin_zlib, cintex, exceptions, fftw3, krb5, mathcore, mathmore, mysql, opengl, pch, pgsql, python, reflex, shadowpw, shared, ssl, thread, xml, xrootd.

To build ROOT type:

   make
   make installi suggest that you have a number of packages not installed. when building packages from source, its important to install the 'dev' version of packages when satisfying the dependencies.
it may well be that the packages in dapper aren't up to date enough.

---

### Post by lamego on 2007-02-04
I have compiled it in Dapper without any problems, just look at the output from configure...

---

### Post by KentS on 2007-02-04
Thank you so much for helping.

According to the Synaptic Package Manager I have the following packages installed:
```
g77-3.4 (g77-3.4.6)
libx11-dev (2:1.0.0*)
libxext-dev (2:1.0.0*
libxpm-dev (1:3.5.4.2)

```
As far as I can see, they are the latest versions available through the Ubuntu repositories.

When I run ./configure it looks like there are some packages/libraries missing (like xml2-config and gsl-config are not found), but I'm not familiar with them. 
My output from './config' is 
> Configuring for linux
Checking for libX11 ... /usr/lib
Checking for X11/Xlib.h ... /usr/include
Checking for libXpm ... /usr/lib
Checking whether to build included libfreetype6 ... yes
Checking whether to build included libpcre ... yes
Checking whether to build included zlib ... yes
Checking for GL/gl.h ... no
Checking for libGL, or libMesaGL ... no
Checking for libGLU, or libMesaGLU ... no
Checking for mysql_config ... not found
Checking for mysql.h ... no
Checking for libmysqlclient_r, libmysqlclient, or mysqlclient ... no
Checking for occi.h ... no
Checking for libclntsh, or oci ... no
Checking for libocci, or oraocci10 ... no
Checking for libpq-fe.h ... no
Checking for libpq ... no
Checking for sql.h ... no
Checking for libsqlod ... no
Checking for sqlext.h ... no
Checking for libiodbc, libodbc, or odbc32 ... no
Checking for rfio_api.h ... no
Checking for librfio, libshift, shiftmd, or shift ... no
Checking for rfio_api.h ... no
Checking for stager_api.h ... no
Checking for libshift, shiftmd, or shift ... no
Checking for gfal_api.h ... no
Checking for libgfal ... no
Checking for G4Navigator.hh ... no
Checking for libG4navigation ... no
Checking for CLHEP/Vector/Rotation.h ... no
Checking for ApMon.h ... no
Checking for libapmoncpp ... no
Checking for monalisawsclient.h ... no
Checking for libmonalisawsclient ... no
Checking for fftw3.h ... no
Checking for libfftw3, or libfftw3-3 ... no
Checking for libpacklib_noshift, libpacklib, packmd, or packlib ... no
Checking for libkernlib_noshift, libkernlib, kernmd, or kernlib ... no
Checking for libPythia6 ... no
Checking for dcap.h ... no
Checking for libdcap ... no
Checking for chirp_client.h ... no
Checking for libchirp_client ... no
Checking for gapiUI.h ... no
Checking for libgapiUI ... no
Checking for jpeglib.h ... no
Checking for png.h ... no
Checking for tiffio.h ... no
Checking for gif_lib.h ... no
Checking for libjpeg ... no
Checking for libtiff ... no
Checking for libungif ... no
Checking for libz ... no
Checking for libpng ... no
Checking whether to build included libAfterImage ... yes
Checking for ldap.h ... no
Checking for libldap ... no
Checking for python/Python.h, python2.5/Python.h, python2.4/Python.h, python2.3/Python.h, python2.2/Python.h, or Python.h ... no
Checking for libpython, libpython2.5, libpython2.4, libpython2.3, libpython2.2, python25, python24, python23, or Python ... no
Checking for xml2-config ... not found
Checking for libxml/tree.h ... no
Checking for libxml2_a, or libxml2 ... no
Checking whether to build xrootd ... yes
Checking for for globusdir ... no
Checking for GLOBUS_LOCATION ... no
Checking for libssl ... no
Checking for t_server.h ... no
Checking for libsrp ... no
Checking for libgmp ... no
Checking for libmisc ... no
Checking for pwauth.h ... no
Checking for krb5.h ... no
Checking for libk5crypto ... no
Checking whether we're using MIT Kerberos ... no
Checking for libkrb5 ... no
Checking for kinit ... no
Checking for shadow passwords ... yes
Checking for gsl/gsl_version.h ... no
Checking for gsl-config ... not found
Checking whether to build libMathMore ... no
Checking whether to build libMathCore ... yes
Checking whether to build CINT7 ... no
Checking whether to build libCintex ... yes
Checking whether to build libReflex ... yes
Checking whether to build libRooFit ... no
Checking whether to build libMinuit2 ... no
Checking whether to build libUnuran ... no
Checking whether to build libGdml ... no
Checking whether to build libTable ... no
Checking for Clarens support ... no
Checking for PEAC support ... no
Generating cint dictionaries.
Checking whether setresuid declared in /usr/include/unistd.h ... yes
Writing config/Makefile.config ... done
Writing include/RConfigure.h ... done
Writing bin/root-config ... done
Writing etc/system.rootrc ... done
Writing etc/system.rootauthrc ... done
Writing etc/system.rootdaemonrc ... done
Writing etc/root.mimes ... done
Writing etc/daemons/rootd.rc.d ... done
Writing etc/daemons/rootd.xinetd ... done
Writing etc/daemons/proofd.rc.d ... done
Writing etc/daemons/proofd.xinetd ... done
Writing etc/daemons/xrootd.rc.d ... done
Writing etc/daemons/olbd.rc.d ... done
Writing bin/memprobe ... done
Writing build/misc/root-help.el ... done
Writing macros/html.C ... done
Writing bin/thisroot.sh ... done
Writing bin/thisroot.csh ... done
Writing config.status ... done

Enabled support for asimage, astiff, builtin_afterimage, builtin_freetype, builtin_pcre, builtin_zlib, cintex, exceptions, mathcore, pch, reflex, shadowpw, shared, thread, xrootd.

To build the ROOT OpenGL add-on library see README/INSTALL.


To build ROOT type:

   make
   make install



Output from 'make' is as previous stated.

'make install' appears to be working perfectly. (I wrote a script that took care of the installation the first time I tried. That's how I know this. Also, output from 'root' is 'bash: root: command not found')

---

### Post by ComplexNumber on 2007-02-04
> 'make install' appears to be working perfectly. (I wrote a script that took care of the installation the first time I tried. That's how I know this. Also, output from 'root' is 'bash: root: command not found')
its case sensitive. if it isntalled correctly, type in 'ROOT' instead.

---

### Post by KentS on 2007-02-04
I've managed to install the packages that was "not found" when I ran './configure'.
Still many lines says "Checking * ... no".
Still the same error from 'make'
I found the following errors when running 'sudo make install':
```
make[1]: Leaving directory `/home/kent/root'
Installing binaries in /bin
cp: cannot stat «bin/xrdgsiproxy»: No such file or directory

Installing misc docs in
mkdir: Missing operand

cp: missing destination file operand after «LICENSE»

cp: target «README/README.SELECTOR» is not a directory

```

Output from 'root' (small letters) is now
```
rootx xpm error: XpmOpenFailed
root: can't start ROOT -- check that /usr/bin/bin/root.exe exists!

```
/usr/bin/bin/root.exe does not exist.

Output from './config' is now
> 
kent@kent-laptop:~/root$ ./configure
Configuring for linux
Checking for libX11 ... /usr/lib
Checking for X11/Xlib.h ... /usr/include
Checking for libXpm ... /usr/lib
Checking whether to build included libfreetype6 ... yes
Checking whether to build included libpcre ... yes
Checking whether to build included zlib ... yes
Checking for GL/gl.h ... no
Checking for libGL, or libMesaGL ... no
Checking for libGLU, or libMesaGLU ... no
Checking for mysql_config ... /usr/bin/mysql_config
Checking for libmysqlclient version >= 3.23.* ... ok
Checking for occi.h ... no
Checking for libclntsh, or oci ... no
Checking for libocci, or oraocci10 ... no
Checking for libpq-fe.h ... no
Checking for libpq ... no
Checking for sql.h ... no
Checking for libsqlod ... no
Checking for sqlext.h ... no
Checking for libiodbc, libodbc, or odbc32 ... no
Checking for rfio_api.h ... no
Checking for librfio, libshift, shiftmd, or shift ... no
Checking for rfio_api.h ... no
Checking for stager_api.h ... no
Checking for libshift, shiftmd, or shift ... no
Checking for gfal_api.h ... no
Checking for libgfal ... no
Checking for G4Navigator.hh ... no
Checking for libG4navigation ... no
Checking for CLHEP/Vector/Rotation.h ... no
Checking for ApMon.h ... no
Checking for libapmoncpp ... no
Checking for monalisawsclient.h ... no
Checking for libmonalisawsclient ... no
Checking for fftw3.h ... no
Checking for libfftw3, or libfftw3-3 ... no
Checking for libpacklib_noshift, libpacklib, packmd, or packlib ... no
Checking for libkernlib_noshift, libkernlib, kernmd, or kernlib ... no
Checking for libPythia6 ... no
Checking for dcap.h ... no
Checking for libdcap ... no
Checking for chirp_client.h ... no
Checking for libchirp_client ... no
Checking for gapiUI.h ... no
Checking for libgapiUI ... no
Checking for jpeglib.h ... no
Checking for png.h ... no
Checking for tiffio.h ... no
Checking for gif_lib.h ... no
Checking for libjpeg ... no
Checking for libtiff ... no
Checking for libungif ... no
Checking for libz ... /usr/lib
Checking for libpng ... no
Checking whether to build included libAfterImage ... yes
Checking for ldap.h ... no
Checking for libldap ... no
Checking for python/Python.h, python2.5/Python.h, python2.4/Python.h, python2.3/Python.h, python2.2/Python.h, or Python.h ... no
Checking for libpython, libpython2.5, libpython2.4, libpython2.3, libpython2.2, python25, python24, python23, or Python ... no
Checking for xml2-config ... /usr/bin/xml2-config
Checking for libxml2 version >= 2.4.x ... ok
Checking whether to build xrootd ... yes
Checking for for globusdir ... no
Checking for GLOBUS_LOCATION ... no
Checking for libssl ... no
Checking for t_server.h ... no
Checking for libsrp ... no
Checking for libgmp ... no
Checking for libmisc ... no
Checking for pwauth.h ... no
Checking for krb5.h ... no
Checking for libk5crypto ... no
Checking whether we're using MIT Kerberos ... no
Checking for libkrb5 ... no
Checking for kinit ... no
Checking for shadow passwords ... yes
Checking for gsl/gsl_version.h ... /usr/include
Checking for GSL version >= 1.8 ... no
Checking whether to build libMathMore ... no
Checking whether to build libMathCore ... yes
Checking whether to build CINT7 ... no
Checking whether to build libCintex ... yes
Checking whether to build libReflex ... yes
Checking whether to build libRooFit ... no
Checking whether to build libMinuit2 ... no
Checking whether to build libUnuran ... no
Checking whether to build libGdml ... no
Checking whether to build libTable ... no
Checking for Clarens support ... no
Checking for PEAC support ... no
Generating cint dictionaries.
Checking whether setresuid declared in /usr/include/unistd.h ... yes
Writing config/Makefile.config ... done
Writing include/RConfigure.h ... done
Writing bin/root-config ... done
Writing etc/system.rootrc ... done
Writing etc/system.rootauthrc ... done
Writing etc/system.rootdaemonrc ... done
Writing etc/root.mimes ... done
Writing etc/daemons/rootd.rc.d ... done
Writing etc/daemons/rootd.xinetd ... done
Writing etc/daemons/proofd.rc.d ... done
Writing etc/daemons/proofd.xinetd ... done
Writing etc/daemons/xrootd.rc.d ... done
Writing etc/daemons/olbd.rc.d ... done
Writing bin/memprobe ... done
Writing build/misc/root-help.el ... done
Writing macros/html.C ... done
Writing bin/thisroot.sh ... done
Writing bin/thisroot.csh ... done
Writing config.status ... done

Enabled support for asimage, astiff, builtin_afterimage, builtin_freetype, builtin_pcre, builtin_zlib, cintex, exceptions, mathcore, mysql, pch, reflex, shadowpw, shared, thread, xml, xrootd.

To build the ROOT OpenGL add-on library see README/INSTALL.


To build ROOT type:

   make
   make install



---

### Post by LKRaider on 2007-02-04
NEVER run "make install" if any of the previous steps failed. Each step is dependant on the other.

I recommend you build a clean chroot environment and try compiling from there, so to not receive interference from leftover env. variables or libraries.

---

