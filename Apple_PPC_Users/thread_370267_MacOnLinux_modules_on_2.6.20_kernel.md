---
title: "MacOnLinux modules on 2.6.20 kernel"
date: 2007-02-25
forum: Apple PPC Users
---

### Post by Shock_ on 2007-02-25
Aiya!

I'm going to compile kernel 2.6.20 (at the time I have 2.6.19-rc5) on my iMac G5 with Edgy, and I want Mac-on-Linux working in it. I've installed mol-modules-source, I've exported these vars:
KSRC="/usr/src/linux-2.6.20"
KVERS="linux-2.6.20"
KEMAIL="myemail"
KMAINT="Shock"
as said on [https://help.ubuntu.com/community/MOLModulesHowto]("https://help.ubuntu.com/community/MOLModulesHowto")
, I've untar mol-modules.tar.gz and I've debian/rules build, but it shows me this:
```

m4 -DKVERS="2.6.20" -DKSRC="/usr/src/linux-2.6.20" -DKEMAIL="shockunown@gmail.com" -DKMAINT="Shock" -DKDREV="ubuntu0" -DDEBDATE="Sun, 25 Feb 2007 21:11:54 +0100" debian/control.m4 > debian/control
m4 -DKVERS="2.6.20" -DKSRC="/usr/src/linux-2.6.20" -DKEMAIL="shockunown@gmail.com" -DKMAINT="Shock" -DKDREV="ubuntu0" -DDEBDATE="Sun, 25 Feb 2007 21:11:54 +0100" debian/changelog.m4 > debian/changelog
touch configure-stamp
dh_testdir
/usr/bin/make
make[1]: se ingresa al directorio `/usr/src/modules/mol'
/usr/bin/make -C src/kmod
make[2]: se ingresa al directorio `/usr/src/modules/mol/src/kmod'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/usr/src/modules/mol/src/kmod'
/usr/bin/make -C src/netdriver
make[2]: se ingresa al directorio `/usr/src/modules/mol/src/netdriver'
  CC [M]  /usr/src/modules/mol/src/netdriver/build/kuname.o
/usr/src/modules/mol/src/netdriver/build/kuname.c:17:26: error: linux/config.h: No existe el fichero ó directorio
/usr/src/modules/mol/src/netdriver/build/kuname.c:39: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;UTS_RELEASE&#8217;
make[4]: *** [/usr/src/modules/mol/src/netdriver/build/kuname.o] Error 1
make[3]: *** [_module_/usr/src/modules/mol/src/netdriver/build] Error 2
make[2]: se sale del directorio `/usr/src/modules/mol/src/netdriver'
make[1]: se sale del directorio `/usr/src/modules/mol'
touch build-stamp

```

What is the problem? Do I must compile before the kernel? It's anything bad? I really would love install Mac On Linux! Thanks.

---

### Post by calum on 2007-02-26
> **Shock_ said:**
> Aiya!

What is the problem? Do I must compile before the kernel? It's anything bad? I really would love install Mac On Linux! Thanks.

I don't know what the problem is, but personally I would ignore any MOL packages in the Ubuntu repositories, and just build it yourself from [the latest tarball]("http://sourceforge.net/project/showfiles.php?group_id=179078") which includes several build fix patches for newer kernels.

I'm running 2.6.20 installed from the Feisty repositories, and MOL builds and runs just fine this way.  (No environment variables required, provided /usr/src/linux is symlinked to the appropriate kernel header files.)

---

### Post by min_max9000 on 2007-02-27
> **calum said:**
> I don't know what the problem is, but personally I would ignore any MOL packages in the Ubuntu repositories, and just build it yourself from [the latest tarball]("http://sourceforge.net/project/showfiles.php?group_id=179078") which includes several build fix patches for newer kernels.

I'm running 2.6.20 installed from the Feisty repositories, and MOL builds and runs just fine this way.  (No environment variables required, provided /usr/src/linux is symlinked to the appropriate kernel header files.)I've gone and downloaded this... what do I do with it now? I'm very new to linux.

---

### Post by Shock_ on 2007-03-07
Aiya!

I've installed the kernel from the feisty repositories, but it outputs the same error. I've compiled 2.6.20, now I'm using it, but it doesn't work too. 

I tried to compile MOL from sources but, when doing ./autogen.sh, it outputs:
> shock@yavenim:~/mol/mol2$ sudo ./autogen.sh
==================================================
 Invoking autoheader and autoconf.
/usr/bin/m4: unrecognized option `--debugfile=autom4te.cache/traces.0t'
Try `/usr/bin/m4 --help' for more information.
autom4te: /usr/bin/m4 failed with exit status: 1
autoheader: '/usr/bin/autom4te' failed with exit status: 1
autoheader failed


I tried with ./configure and it was OK, but, when I make, it outputs:
> 
shock@yavenim:~/mol/mol2$ make
+ Entering lxdialog
+ Entering kconfig
#
# using defaults found in config/defconfig-ppc64
#


# End of "Mac-on-Linux" configuration.
# The next step is probably 'make'.

config.status: creating unconfig
config.status: creating Makefile.defs
config.status: creating config.h
config.status: config.h is unchanged
= Building mol-0.9.72 [mar 7 2007 21:20]
+ Entering scripts
    Compiling    asfilter.o
= Building asfilter
    Compiling    kver_approx.o
= Building kver_approx
+ Entering src
+ Entering lib
    Compiling    extralib.o
    Compiling    llseek.o
    Compiling    elfload.o
En el fichero incluído de elfload.c:34:
../../src/include/byteorder.h:27:31: cpu/mol_byteorder.h: No existe el fichero ó directorio
make[3]: *** [../../obj-ppc64/build/src/lib/elfload.o] Error 1
make[2]: *** [sub-lib-all] Error 2
make[1]: *** [sub-src-all] Error 2
make: *** [auto-bootstrap] Error 2


Nobody can help me?

---

### Post by ajmorris on 2007-05-27
> **Shock_ said:**
> Aiya!

I've installed the kernel from the feisty repositories, but it outputs the same error. I've compiled 2.6.20, now I'm using it, but it doesn't work too. 

I tried to compile MOL from sources but, when doing ./autogen.sh, it outputs:


I tried with ./configure and it was OK, but, when I make, it outputs:


Nobody can help me?

i know you posted this ages ago but, the problem is that if you look in the folder where elfload.o is supposed to be, it is not, that is what the compilation is complaining about.

---

