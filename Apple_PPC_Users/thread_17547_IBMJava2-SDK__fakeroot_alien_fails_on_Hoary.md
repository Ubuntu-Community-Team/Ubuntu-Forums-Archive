---
title: "IBMJava2-SDK  fakeroot alien fails on Hoary"
date: 2005-03-01
forum: Apple PPC Users
---

### Post by pismo_ubuntu on 2005-03-01
I was trying to install jdk  on my pismo/Hoary according to this [guide.](http://www.ubuntulinux.org/wiki/JavaPPC/view?searchterm=ppc%20java) 

what I´ve done was:

# fakeroot alien -d IBMJava2-SDK-ppc-1.4.2-0.0.ppc.rpm && dpkg -i ibmjava2-sdk-ppc_1.4.2-1_powerpc.deb

and result, the first step failed, and 2nd step made some funny thing to package system.

now, my apt-get upgrade says:

E: The package ibmjava2-sdk-ppc needs to be reinstalled, but I can't find an archive for it.

The thing is, I don´t know how to fix this apt-get thing. 

Could anybody help me.

I´ve tried the following command, but same results.

# apt-get remove ibmjava2-sdk-ppc

E: The package ibmjava2-sdk-ppc needs to be reinstalled, but I can't find an archive for it.

# cp ibmjava2-sdk-ppc_1.4.2-1_powerpc.deb /var/lib/apt/lists/
# cp ibmjava2-sdk-ppc_1.4.2-1_powerpc.deb /var/lib/apt/lists/partial/
# apt-get remove ibmjava2-sdk-ppc

E: The package ibmjava2-sdk-ppc needs to be reinstalled, but I can't find an archive for it.
  
here is the failed log of fakeroot alien 
> 
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/ibmjava2-sdk-ppc
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: format of libjava.so not recognized
dpkg-shlibdeps: warning: format of libjvm.so not recognized
dpkg-shlibdeps: warning: format of libhpi.so not recognized
dpkg-shlibdeps: warning: format of libdbgmalloc.so not recognized
dpkg-shlibdeps: warning: format of libjsig.so not recognized
dpkg-shlibdeps: warning: format of libawt.so not recognized
dpkg-shlibdeps: warning: format of libjvm.so not recognized
dpkg-shlibdeps: warning: format of libjava.so not recognized
dpkg-shlibdeps: warning: format of libhpi.so not recognized
dpkg-shlibdeps: warning: format of libjava.so not recognized
dpkg-shlibdeps: warning: format of libdbgmalloc.so not recognized
dpkg-shlibdeps: warning: format of libjava.so not recognized
dpkg-shlibdeps: warning: format of libawt.so not recognized
dpkg-shlibdeps: warning: format of libawt.so not recognized
dpkg-shlibdeps: warning: format of libjsig.so not recognized
dpkg-shlibdeps: warning: format of libdbgmalloc.so not recognized
dpkg-shlibdeps: warning: format of libjvm.so not recognized
dpkg-shlibdeps: warning: format of libhpi.so not recognized
dpkg-shlibdeps: warning: format of libjsig.so not recognized
dpkg-shlibdeps: warning: format of libawt.so not recognized
dpkg-shlibdeps: warning: format of libjvm.so not recognized
dpkg-shlibdeps: warning: format of libjava.so not recognized
dpkg-shlibdeps: warning: format of libdbgmalloc.so not recognized
dpkg-shlibdeps: warning: format of libjava.so not recognized
dpkg-shlibdeps: warning: format of libdbgmalloc.so not recognized
dpkg-shlibdeps: warning: format of libjsig.so not recognized
dpkg-shlibdeps: warning: format of libnet.so not recognized
dpkg-shlibdeps: warning: format of libjava.so not recognized
dpkg-shlibdeps: warning: format of libjsig.so not recognized
dpkg-shlibdeps: warning: format of libjvm.so not recognized
dpkg-shlibdeps: warning: format of libjava.so not recognized
dpkg-shlibdeps: warning: format of libjvm.so not recognized
dpkg-shlibdeps: warning: format of libdbgmalloc.so not recognized
dh_gencontrol
dh_md5sums
dh_builddeb
dpkg-deb (subprocess): data: internal gzip error: read(4096) != write(0): No space left on device
dpkg-deb: subprocess <compress> from tar -cf returned error exit status 2
dpkg-deb: building package `ibmjava2-sdk-ppc' in `../ibmjava2-sdk-ppc_1.4.2-1_powerpc.deb'.
dh_builddeb: command returned error code 512
make: *** [binary-arch] Error 1
find: IBMJava2-SDK-ppc-1.4.2: No such file or directory


by the way, Ubuntu is my first distribution which makes me feel like it´s really possible to use Linux in daily life. 
Thank´s to the Ubuntu team and it´s community.

---

### Post by pismo_ubuntu on 2005-03-01
I manually remove the entry from 

/var/lib/dpkg/status

and it seems ok.

thanks.

it was just because /tmp was too small....

---

