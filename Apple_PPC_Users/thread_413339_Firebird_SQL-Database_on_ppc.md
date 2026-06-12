---
title: "Firebird SQL-Database on ppc?"
date: 2007-04-19
forum: Apple PPC Users
---

### Post by Jehu on 2007-04-19
Hi @ all,

can't compile the Firebird Database on an Mac Mini with PPC-CPU.

```
sh autogen.sh --build=powerpc-linux --enable-superserver CC=gcc-3.4
```

configure works well, but the make-command fails afte long time running:

```
g++  -DBOOT_BUILD -I../src/include/gen -I../src/include -I../src/vulcan -I../extern/icu/source/common -I../extern/icu/source/i18n -DNAMESPACE=Vulcan -O3 -DNDEBUG -DLINUX -pipe -MMD -fPIC -fsigned-char -DPROD_BUILD -c ../src/jrd/pag.cpp -o ../temp/boot/jrd/pag.o
../src/jrd/pag.cpp:273:2: error: invalid preprocessing directive #const
make[3]: *** [../temp/boot/jrd/pag.o] Fehler 1
rm ../src/jrd/dyn_mod.cpp ../src/jrd/grant.cpp ../src/jrd/dyn.cpp ../src/jrd/dyn_def.cpp ../src/jrd/dyn_del.cpp ../src/jrd/met.cpp ../src/jrd/scl.cpp ../src/jrd/ini.cpp ../src/jrd/dpm.cpp ../src/jrd/dyn_util.cpp ../src/jrd/dfw.cpp ../src/jrd/pcmet.cpp ../src/jrd/fun.cpp
make[3]: Verlasse Verzeichnis '/usr/src/Firebird-2.0.1.12855-0/gen'
make[2]: *** [libfbstatic] Fehler 2
make[2]: Verlasse Verzeichnis '/usr/src/Firebird-2.0.1.12855-0/gen'
make[1]: *** [../gen/firebird/bin/gpre_static] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/Firebird-2.0.1.12855-0/gen'
make: *** [firebird] Fehler 2

```

Why are only the Firebird Config-Files in the Ubuntu-Repositorys (firebird2-common)?
Have anyone compiled the Firebird DB successful?

So long
Jehu

---

### Post by Jehu on 2007-04-19
Ok, now i've crosscompiled on my Athlon:

```
sh autogen.sh --host=powerpc-linux --enable-superserver --prefix=/opt/cross/firebird CC=gcc-3.4
```

This works without any errors.


Now an "make install" on the PowerPC results in an new error:

```
/bin/fbmgr.bin: Exec format error (Exec format error)

Fixing firebird's shell to /bin/sh

Starting Firebird server: start-stop-daemon: Unable to start /opt/cross/firebird/bin/fbmgr.bin: Exec format error (Exec format error)
Please enter new password for SYSDBA user: *****
/opt/cross/firebird/bin/gsec: 1: Syntax error: "&" unexpected (expecting ")")

Please enter new password for SYSDBA user: *****
/opt/cross/firebird/bin/gsec: 1: Syntax error: "&" unexpected (expecting ")")

Please enter new password for SYSDBA user: 
```

:(

---

### Post by mariuz on 2007-04-19
what version of gcc do you have ?
can you upgrade the distro on the machine and the g++ in the same time?

---

### Post by mariuz on 2007-04-19
edit this file  src/jrd/pag.cp
and at line 273 delete 
these 3 lines
#ifdef PPC
const SSHORT CLASS = CLASS_LINUX_PPC;
#endif
 
That constat is defined again later
also in my case i had to chmod +x src/misc/writeBuildNum.sh 
(i'm  on an restricted account on an ppc machine)

---

