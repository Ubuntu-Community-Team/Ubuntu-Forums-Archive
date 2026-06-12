---
title: "Compile kernel source - getting errors ..."
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-04-30
Using the procedure at:   [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

When I try the following command:

sudo make-kpkg --rootcmd fakeroot --initrd --append-to-version=-carl  kernel-image kernel-headers

I get these errors:

make[2]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make[1]: *** [init] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [debian/stamp-build-kernel] Error 2


What am I doing wrong?????

Thanks

Carl

---

### Post by Bachstelze on 2007-04-30
Make you the /usr/src/linux symlink points to the source tree you're compiling, for example if I'm trying to build a 2.6.21.1 kernel, I should get this :

```
mfb@ana ~ $ ls -ld /usr/src/linux
lrwxrwxrwx 1 root root 14 2007-04-29 22:03 /usr/src/linux -> linux-2.6.21.1

```

---

### Post by cwmoser on 2007-05-01
I get this:

carl@klaatu:~$ ls -ld /usr/src/linux
lrwxrwxrwx 1 root src 31 2007-04-30 21:55 /usr/src/linux -> linux-headers-2.6.20-15-generic


When I do ls -l  /usr/src, I get:

[FONT="Courier New"]
lrwxrwxrwx   1 root src        31 2007-04-30 21:55 linux -> linux-headers-2.6.20-15-generic
drwxr-xr-x  20 root root     4096 2007-04-29 19:19 linux-headers-2.6.20-15
drwxr-xr-x   5 root root     4096 2007-04-30 22:27 linux-headers-2.6.20-15-generic
drwxr-xr-x  23 root root     4096 2007-04-15 03:46 linux-source-2.6.20
-rw-r--r--   1 root root 47703988 2007-04-15 03:48 linux-source-2.6.20.tar.bz2
[/FONT]

---

### Post by cwmoser on 2007-05-01
When I do a uname -r, I get 2.6.20-15-generic.

I note your reference to 2.6.21.1 which indicates a newer kernel.  Will all the Ubuntu modifications be carried to the newer kernel?

Thanks

Carl

---

### Post by Rui Pais on 2007-05-01
> **cwmoser said:**
> I get this:

carl@klaatu:~$ ls -ld /usr/src/linux
lrwxrwxrwx 1 root src 31 2007-04-30 21:55 /usr/src/linux -> linux-headers-2.6.20-15-generic
your /usr/src/linux should point to sources, not headers.
Try ```

rm /usr/src/linux
ln -s /usr/src/inux-source-2.6.20 /usr/src/inux
```

That should correct it.

---

### Post by cwmoser on 2007-05-01
Linking to the source instead of the headers got me a lot farther.

After a lengthy question and answer session and a lengthy compile, I get the following:

echo done > debian/stamp-build-kernel
====== making target install/linux-image-2.6.20.3-ubuntu1-carl [new prereqs: ]======
This is kernel package version 10.065ubuntu5.
echo "The UTS Release version in include/linux/utsrelease.h"; echo "     \"2.6.20.3-ubuntu1-carlcarl\" "; echo "does not match current version:"; echo "     \"2.6.20.3-ubuntu1-carl\" "; echo "Please correct this."; exit 2
The UTS Release version in include/linux/utsrelease.h
     "2.6.20.3-ubuntu1-carlcarl" 
does not match current version:
     "2.6.20.3-ubuntu1-carl" 
Please correct this.
make: *** [install/linux-image-2.6.20.3-ubuntu1-carl] Error 2


Not sure I understand the naming issue.  I do remember naming my kernel "carl".

Any help is appreciated.

Thanks

Carl

---

### Post by Rui Pais on 2007-05-01
it got confused, by some reason, with the append you specified, that seems to be applied twice...
You can corrected that by clean it:
```
make-kpkg clean
```
and redo the compile command again.


________________________________

I find that HowTo you point rather complicated.
May i suggest [this one here]("http://ubuntuforums.org/showthread.php?t=311158")? It's simpler and much efficient. 
It boils down to: 


```
cp /boot/config-`uname -r` .config && make oldconfig && make xconfig
```
Make you changes (you can take some time disabling the huge usefulness quantity of stuff default kernels have on it), save, make your self root and clean for niceness:
```
sudo -s -H
make-kpkg clean
```
then compile it (change the revision flag to your taste of course):
```
make-kpkg -initrd --revision=my_cool_kernel_or_what_ever_you_like_here kernel_image kernel_headers modules_image
```
and Install:
```
cd .. && dpkg -i linux*.deb
```

it's almost boring :)

---

### Post by Bachstelze on 2007-05-01
This seems way too much hassle to me. When I build a kernel, I just

```
cd /usr/src/linux
make
make modules_install
make install

```

and I'm done :p

---

### Post by Rui Pais on 2007-05-01
> **HymnToLife said:**
> This seems way too much hassle to me. When I build a kernel, I just

```
cd /usr/src/linux
make
make modules_install
make install

```

and I'm done :p

:)

Yes, i used to do that too... specially when i go back to Ubuntu from Gentoo.
But the "advantage" i found in the "debian" way is to clean old kernels with a single apt-get. :)

Besides here everybody seems to use one way or an other to do the debs that for easiness in answering any issue i started again to do it too.

Edit: btw, an disvantage, is that  there is always a huge quantity of post referring errors with make-kpkg, specially connected with --revision and --append. Seems that it can (too) easily became problematic.

---

### Post by Bachstelze on 2007-05-01
Yeah, Ubuntu tends to forget the [KISS-principle](http://en.wikipedia.org/wiki/KISS_principle) way too often...

---

### Post by Rui Pais on 2007-05-01
> **HymnToLife said:**
> Yeah, Ubuntu tends to forget the [KISS-principle](http://en.wikipedia.org/wiki/KISS_principle) way too often...

yes, in this case Debian, 'cause the idea starts there. 
(btw, i didn't knew that KISS acronym :lol: )

---

### Post by cwmoser on 2007-05-02
I got the Kernel to compile - my new kernel is linux-2.6.21.1 - thanks to all who helped.

It appears in the Grub boot menu but when booting I got an X-window error. 
Had to edit /etc/X11/xorg.conf and change "nvidia" to "nv" in the Section "Device"

Do I have to go to Synaptic and reinstall the linux-restricted-modules?

If I reinstall those modules, will it affect my other Fiesty Linux 2.6.15?  I don't want this kernel to get messed up as its my fall back kernel.

Are all installed applications migrated to new kernels?

Thanks

Carl

---

### Post by Rui Pais on 2007-05-03
Glad it worked :)

nv is the open source driver for nvidia cards that came with Linux kernel, so it's immediately available. If you compiled. 

Now about the famous nvidia... is a closed driver (you got it probably with restricted package).
It's when the HymnToLife comment about simpleness most apply :(

If you want to use restricted-modules package you need to compile that too, (i think, i dont' use it) against your new kernel sources. You can check how in your previous link:
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

Myself, i prefer to user directly the nvidia drivers installer from NVidia site.
After reboot a new kernel, and got a X failure window, i run from the console the  downloaded:
```
sudo sh /NVIDIA-Linux-x86-1.0-9755-pkg1.run
``` 
and then restart the X+gdm:
```
sudo /etc/init.d/gdm restart
```
thats all.

(with a running X, with nv or vesa e.g., one needs to previously stop it with *sudo /etc/init.d/gdm stop*, before run Nvidia installer)

---

### Post by cwmoser on 2007-05-05
Got my new Kernel (2.6.21.1) to boot.  But, I cannot get the NVIDIA drivers to work.
My older Feisty kernel (2.6.20-15-generic) works great.
I got Beryl to work with the older kernel.
Evidentually I forgot how to install the NVIDIA drivers.

When I do the following wit the new kernel ...

sudo apt-get install nvidia-glx
sudo nvidia-xconfig --add-argb-glx-visuals --composite

... and then reboot, the new Kernel emits errors about a GDM misconfiguration and I get a login prompt.  I can go to /etc/X11/xorg.conf and change a Driver setting from "nvidia" back to "nv" and I can get a login but a low resolution an obviously not with the Nvidia drivers.

You guys have helped me get close to building a kernel and I would appreciate any help in dealing with this Nvidia problem.

Carl

---

### Post by Bachstelze on 2007-05-05
You can't use Ubuntu packages wih a non-Ubuntu kernel. You'll have to use the installer from nvidia.

---

### Post by cwmoser on 2007-05-05
Thanks.  I downloaded the Nvidia drivers and ran them like you suggested:

sudo sh /NVIDIA-Linux-x86-1.0-9755-pkg1.run

I get a "Unable to build the NVIDIA kernel module" message.  It might be how I ran them.
First I tried it directly from a terminal session.  Then I tried via the recovery console.  There is something I am not doing properly.

Carl

---

### Post by Rui Pais on 2007-05-05
Not from a recovery mode.
Boot normaly. 
Close any gnome session, press Ctrl+Alt+F1
login and enter:
```
sudo /etc/init.d/gdm stop
sh sudo sh /NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo /etc/init.d/gdm restart
```

should work.




(edit: my 1000 post, must give you luck :) 
it's late here check this tomorrow or maybe HymnToLife may help if any issue appear)

---

### Post by Bachstelze on 2007-05-05
Also, make sure you removed the Ubuntu packages for the nvidia driver and installed all the tools required to build them :

```
sudo apt-get remove nvidia-glx* linux-restricted-modules*
sudo apt-get install pkg-config xorg-dev
```

---

### Post by cwmoser on 2007-05-05
I did the above.  

2 issues:

1- when I open a login via Ctrl+Alt+F1, there  are continuous messages like "sdd: assuming drive cache write through" that annoying continually post on the screen.

2- when I did issue the command to loand the NVIDIA driver, it started well and asked a few questions but then posted "ERROR:  Unable to build the NVIDIA kernel module".

My /var/log/nvidia-installer.log is:

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat May  5 19:57:02 2007

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.21.1/source'
-> Kernel output path: '/lib/modules/2.6.21.1/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv
   -vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h Modules.symvers
   rm -f -rf .tmp_versions
   rm -f Makefile
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.21.1/source
   SYSOUT=/lib/modules/2.6.21.1/build'...
   sh ./conftest.sh "cc" "cc" /lib/modules/2.6.21.1/source /lib/modules/2.6.21.
   1/build cc_sanity_check full_output
   sh ./conftest.sh "cc" "cc" /lib/modules/2.6.21.1/source /lib/modules/2.6.21.
   1/build select_makefile full_output
   make --no-print-directory -f Makefile module
   
   NVIDIA: calling KBUILD...
   make CC=cc KBUILD_OUTPUT=/lib/modules/2.6.21.1/build KBUILD_VERBOSE=1 -C /li
   b/modules/2.6.21.1/source SUBDIRS=/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755
   -pkg1/usr/src/nv modules
   make -C /lib/modules/2.6.21.1/build \
   	KBUILD_SRC=/usr/src/linux-2.6.21.1 \
   	KBUILD_EXTMOD="/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv" 
   -f /usr/src/linux-2.6.21.1/Makefile modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/.tmp_ver
   sions
   rm -f /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/.tmp_versio
   ns/*
   make -f /usr/src/linux-2.6.21.1/scripts/Makefile.build obj=/tmp/selfgz14559/
   NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz14559/NV
   IDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL
   __ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.21.1/include -include include/l
   inux/autoconf.h  -I/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/n
   v -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno
   -common -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-s
   tack-boundary=2 -march=i686 -mtune=pentium4 -mtune=generic -ffreestanding -m
   accumulate-outgoing-args -I/usr/src/linux-2.6.21.1/include/asm-i386/mach-def
   ault -Iinclude/asm-i
   386/mach-default -fomit-frame-pointer -g -fno-stack-protector -Wdeclaration-
   after-statement -Wno-pointer-sign  -I/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9
   755-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-
   subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -fno-comm
   on -msoft-float -MD -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL
   _NAMES -D__KERNEL__ -DMODULE -DNVRM -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=
   0 -DNV_PATCHLEVEL=9755 -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DN
   V_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX
   _MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -
   DNV_VM_INSERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMAP_PF
   N_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT -DMODULE -
   D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KB
   UILD_STR(nvidia)" -c -o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/
   src/nv/.tmp_nv.o /tmp/selfgz14559/NV
   IDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv.c: At top leve
   l:
   /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv.c:110: warning
   : ‘kmem_cache_t’ is deprecated
   /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv.c: In function
   ‘__nv_setup_pat_entries’:
   /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv.c:955: warning
   : comparison between signed and unsigned
   /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv.c: In function
   ‘__nv_restore_pat_entries’:
   /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv.c:981: warning
   : comparison between signed and unsigned
   /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv.c: In function
   ‘nv_kern_cpu_callback’:
   /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv.c:1287: warnin
   g: comparison between signed and unsigned
   /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv.c:1294: warnin
   g: comparison between signed and unsigned
     cc -Wp,-MD,/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KER
   NEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.21.1/include -include includ
   e/linux/autoconf.h  -I/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -
   fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2 -march=i686 -mtune=pentium4 -mtune=generic -ffrees
   tanding -maccumulate-outgoing-args -I/usr/src/linux-2.6.21.1/include/asm-i38
   6/mach-default -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g -fno-
   stack-protector -Wdeclaration-after-statement -Wno-pointer-sign  -I/tmp/self
   gz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-
   type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-
   multichar -Werror -O -fno-common -msoft-float -MD -Wsign-compare -Wno-cast-q
   ual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNVRM -DNV_MAJOR
   _VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=9755 -UDEBUG -U_DEBUG -DNDEB
   UG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET
   _CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -
   DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BR
   EAKPOINT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT 
   -DNV_VMAP_4_PRESENT -DMODULE -D"KBUI
   LD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUIL
   D_STR(nvidia)" -c -o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src
   /nv/.tmp_nv-vm.o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/
   nv-vm.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KE
   RNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.21.1/include -include inclu
   de/linux/autoconf.h  -I/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/s
   rc/nv -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing 
   -fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferr
   ed-stack-boundary=2 -march=i686 -mtune=pentium4 -mtune=generic -ffreestandin
   g -maccumulate-outgoing-args -I/usr/src/linux-2.6.21.1/include/asm-i386/mach
   -default -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g -fno-stack-
   protector -Wdeclaration-after-statement -Wno-pointer-sign  -I/tmp/selfgz1455
   9/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -
   Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multic
   har -Werror -O -fno-common -msoft-float -MD -Wsign-compare -Wno-cast-qual -W
   no-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNVRM -DNV_MAJOR_VERSI
   ON=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=9755 -UDEBUG -U_DEBUG -DNDEBUG -DN
   V_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS
   _PRESENT -DNV_SYSCTL
   _MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESE
   NT -DNV_VM_INSERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMA
   P_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT -DMODU
   LE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MO
   DNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-p
   kg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1
   /usr/src/nv/os-agp.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include 
   -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.21.1/include -include
   include/linux/autoconf.h  -I/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/
   usr/src/nv -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-alia
   sing -fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpr
   eferred-stack-boundary=2 -march=i686 -mtune=pentium4 -mtune=generic -ffreest
   anding -maccumulate-outgoing-args -I/usr/src/linux-2.6.21.1/include/asm-i386
   /mach-default -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g -fno-s
   tack-protector -Wdeclaration-after-statement -Wno-pointer-sign  -I/tmp/selfg
   z14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-t
   ype -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-m
   ultichar -Werror -O -fno-common -msoft-float -MD -Wsign-compare -Wno-cast-qu
   al -W
   no-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNVRM -DNV_MAJOR_VERSI
   ON=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=9755 -UDEBUG -U_DEBUG -DNDEBUG -DN
   V_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS
   _PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PC
   I_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPOI
   NT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_V
   MAP_4_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os
   _interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz14559/N
   VIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz1455
   9/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -
   D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.21.1/include -include 
   include/linux/autoconf.h  -I/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/
   usr/src/nv -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-alia
   sing -fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpr
   eferred-stack-boundary=2 -march=i686 -mtune=pentium4 -mtune=generic -ffreest
   anding -maccumulate-outgoing-args -I/usr/src/linux-2.6.21.1/include/asm-i386
   /mach-default -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g -fno-s
   tack-protector -Wdeclaration-after-sta
   tement -Wno-pointer-sign  -I/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/
   usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscript
   s -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -fno-common -msoft
   -float -MD -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D
   __KERNEL__ -DMODULE -DNVRM -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PA
   TCHLEVEL=9755 -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPL
   E_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUN
   T_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_IN
   SERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMAP_PFN_RANGE_P
   RESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT -DMODULE -D"KBUILD_
   STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KB
   UILD_STR(nvidia)" -c -o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/
   src/nv/.tmp_os-registry.o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/us
   r/src/nv/os-registry.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv/os-registry.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/.nv-
   i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KE
   RNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.21.1/include -include inclu
   de/linux/autoconf.h  -I/tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/s
   rc/nv -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing 
   -fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mprefer
   red-stack-boundary=2 -march=i686 -mtune=pentium4 -mtune=generic -ffreestandi
   ng -maccumulate-outgoing-args -I/usr/src/linux-2.6.21.1/include/asm-i386/mac
   h-default -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g -fno-stack
   -protector -Wdeclaration-after-statement -Wno-pointer-sign  -I/tmp/selfgz145
   59/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type 
   -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multi
   char -Werror -O -fno-common -msoft-float -MD -Wsign-compare -Wno-cast-qual -
   Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNVRM -DNV_MAJOR_VERS
   ION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=9755 -UDEBUG -U_DEBUG -DNDEBUG -D
   NV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLAS
   S_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_P
   CI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPO
   INT_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_
   VMAP_4_PRESENT -DMODULE -D"KBUILD_ST
   R(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_ST
   R(nvidia)" -c -o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/
   .tmp_nv-i2c.o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv-
   i2c.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -m elf_i386 -m elf_i386  -r -o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-97
   55-pkg1/usr/src/nv/nvidia.o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/
   usr/src/nv/nv-kernel.o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/s
   rc/nv/nv.o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv-vm.
   o /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/os-agp.o /tmp/s
   elfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/os-interface.o /tmp/sel
   fgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/os-registry.o /tmp/selfgz
   14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nv-i2c.o
     Building modules, stage 2.
   make -f /usr/src/linux-2.6.21.1/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-2.6.21.1/Module.symvers -I /tm
   p/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/Module.symvers -o /t
   mp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/Module.symvers -w v
   mlinux /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv/nvidia.o
   WARNING: vmlinux - Section mismatch: reference to .init.text:start_kernel fr
   om .text between 'is386' (at offset 0xc0101171) and 'check_x87'
   WARNING: vmlinux - Section mismatch: reference to .init.text: from .text bet
   ween 'rest_init' (at offset 0xc0101448) and 'try_name'
   WARNING: vmlinux - Section mismatch: reference to .init.text:__alloc_bootmem
   from .text between 'init_gdt' (at offset 0xc010a76b) and 'cpu_init'
   WARNING: vmlinux - Section mismatch: reference to .init.text:__alloc_bootmem
   from .text between 'init_gdt' (at offset 0xc010a781) and 'cpu_init'
   WARNING: vmlinux - Section mismatch: reference to .init.text:sysenter_setup 
   from .text between 'identify_cpu' (at offset 0xc010add3) and 'display_cachei
   nfo'
   WARNING: vmlinux - Section mismatch: reference to .init.text:mtrr_bp_init fr
   om .text between 'identify_cpu' (at offset 0xc010ade1) and 'display_cacheinf
   o'
   WARNING: vmlinux - Section mismatch: reference to .init.text: from .text bet
   ween 'iret_exc' (at offset 0xc02f264e) and '_etext'
   WARNING: vmlinux - Section mismatch: reference to .init.data:initkmem_list3 
   from .text between 'set_up_list3s' (at offset 0xc0174daf) and 's_start'
   WARNING: vmlinux - Section mismatch: reference to .init.text:eisa_root_regis
   ter from .text between 'virtual_eisa_root_init' (at offset 0xc02702ff) and '
   cpufreq_unregister_driver'
   WARNING: vmlinux - Section mismatch: reference to .init.text: from .text bet
   ween 'iret_exc' (at offset 0xc02f2ce8) and '_etext'
   WARNING: could not find /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz14559/NVIDIA-Linux-x86-1.0-9755-pkg1/
   usr/src/nv/nv-kernel.o
   FATAL: modpost: GPL-incompatible module nvidia.ko uses GPL-only symbol 'para
   virt_ops'
   make[4]: *** [__modpost] Error 1
   make[3]: *** [modules] Error 2
   make[2]: *** [modules] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by cwmoser on 2007-05-06
Could the above mean that my Kernel was not made properly?

Carl

---

### Post by Bachstelze on 2007-05-06
No, it seems to mean that the installer refuses to install the nvidia module (which is non-GPL) because it contains bits of GPL'ed code. That's very weird, I've never seen that before...

---

### Post by Rui Pais on 2007-05-06
Carl 

give a look at this thread:
[http://ubuntuforums.org/showthread.php?p=2306826](http://ubuntuforums.org/showthread.php?p=2306826)
to see if it helps.

good luck.

---

### Post by cwmoser on 2007-05-06
That fixed it -- turning Paravirtualization Support off.

I'm not sure if I remember all the steps I took to finally reach a complete build of my new Kernel but the following is what I think I did.  If I have missed a step, please let me know.

Thanks again to HymnToLife and RuiPais for all the help.  This has been a memorable learning experience - might not sound like much to experts like you but for me to build my first Linux Kernel is a very memorable event.

Carl




Procedure I used to Make A New Ubuntu Linux Kernel:
-------------------------------------------------------------------------


I. Build the new Kernel:
	Ref:  [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

   1. Install the utilities needed to configure the kernel and move to /usr/src
      
      sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev && cd /usr/src

   2. Now we are going to download the kernel and unpack it.
      
      sudo wget [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.20.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.20.tar.bz2) && sudo tar -xvjf linux-2.6.20.tar.bz2

   3. Now we are going to remove the link to the linux directory, make a new link to the new kernel, and move to the Linux directory:
      
      sudo rm -rf linux && sudo ln -s /usr/src/linux-2.6.20 linux && cd /usr/src/linux

      NOTE: IF YOU WILL BE PATCHING THE KERNEL FOR A PROGRAM (ex. fbsplash, bootsplash) APPLY THE PATCH AND SKIP TO STEP 6. IF NOT, GO AHEAD TO THE NEXT STEP.
   4. Now download the latest kernel patch and become root: (Do NOT do this or the step below if you are using a different patch like beyond, emission, etc.)
      
      sudo wget [http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.20.7.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.20.7.bz2) && sudo -s -H

   5. Apply the new patch: (Do NOT do this if you are using a different patch like beyond, emission, etc.)
      
      bzcat patch-2.6.20.7.bz2| patch -p1

   6. Now import your current kernel configuration and configure the kernel:
      sudo cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make xconfig
      Or for servers:
      sudo cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make menuconfig

      IMPORTANT: READ THIS POST OR THE KERNEL MAY NOT COMPILE!
      Hint: When make oldconfig is asking you questions, it is easiest to just hold down enter until it is finished.

   7. Make yourself root if you are not already:
      sudo -s -H

   8. Now time to build the kernel: Make sure that you are in /usr/src/linux with full root access. This will build a debian file that you can install.

    Now in the terminal do this:
      make-kpkg clean
      make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image

      Note: You can replace "386" with anything you want. Like "k7" or "686." The kernel will now compile for 1-3 hours, depending on the speed of your processor. If you have an extremely slow processor, you may have to wait 3-4 hours for the kernel to compile. In the meantime, I would go out to a movie or do something else while the kernel is compiling.[/i]

   9. Install the .deb files in /usr/src. There should be 2. One should be an image .deb file and the other a header .deb file. In terminal do:
      
      cd .. && dpkg -i linux*.deb

      IMPORTANT: IF YOU HAVE AN NVIDIA GRAPHICS CARD, YOU WILL HAVE TO REINSTALL THE DRIVERS FOR IT. DOWNLOAD YOUR DRIVERS .

  10. Now reboot and you will have a faster system!


II.  Install NVIDIA GPL Drivers:
Edit /etc/X11/xorg.conf and change the Device from “nvidia” to “nv”
Boot the new Kernel


Now install the proprietary nvidia drivers:
Press Ctl + Alt + F1 to open up a command prompt logon session
sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo /etc/init.d/gdm restart


If you get an nvidia error that causes the custom Kernel compile to fail:

1. Go to your source location and run make menuconfig
2. Under "Processor type and features" turn "Paravirtualization Support" OFF
3. Exit and save the config.
4. Run make prepare
5. Re-run the NVIDIA Installer

---

### Post by Rui Pais on 2007-05-06
> **cwmoser said:**
> ... This has been a memorable learning experience - might not sound like much to experts like you but for me to build my first Linux Kernel is a very memorable event.

Carl

Glad to know its working.

It is always a fantastic sensation the first times one successfully compiles a kernel or when finally we get though one new kernel with some fresh unknown issue.

Just a little more "share" of my (deep ;)) knowledge... 
Experts?... i wish. 
Well, like HymnToLife, i too never heard about that error problem. 
Just copied the first warning message where your compilation failed and made a search on Google. That pointed to a incomprehensible (to me) German forum where lucky someone post a link to an Ubuntu thread, the one i pointed you.

Web search engines and a sharing information society are the wonders of the modern days :lol:


Have fun around. 
:)

---

### Post by cwmoser on 2007-05-06
Just a note my new Kernel, 2.6.21.1, seems more responsive than the older 2.6.15 kernel.
In the configuration, I did select the CPU type as P4 instead of 386.   If that is the reason, I wonder if there are some other tweaks?

Carl

---

### Post by Bachstelze on 2007-05-06
Try playing aroud with the different options, especially in the "Processor types and features" section. Don't be afraid to recompile many times with different options to see how they affect the kernel, that's how you learn ;)

---

### Post by Rui Pais on 2007-05-07
Another 2 suggestions:

pre-packages kernel came with a lot of stuff enabled (they are made to be used for all kind of users, so no specialization at all) that is useless for most of us. 
Disable it can make kernel either lighter and faster to compile.

Here some suggestion that you can probability turn of if you don't use it (old or unusual stuff):
[LIST]
[*]isa support (OLD)
[*]mca support
[*]pci hotplug 
[*]Amateur radio
[*]IrDA support
[*]Misc Devices
[*]Old CDROM drivers
[*]RAID and LVM (If you wont use it, of course)
[*]Fusion MTP
[*]Macintosh device drivers 
[*]Ethernet (10 or 100Mbit) (<-OLD)
[*]Ethernet (10000 Mbit) (do you have any of those?)
[*]FDDI support 
[*]PLIP ans SLIP support
[*]Telephony Support
[*]SPI support
[*]Dallas's 1-wire bus
[*]Multimedia devices usually have a lot of stuff users usually don't have
[*]HID Devices
[*]LED devices
[*]InfiniBand support
[*]EDAC report
[*]Instrumentation support
etc... 
and,
[*]any (EXPERIMENTAL) flagged stuff that you don't have or your box

[*]File systems you don't use, like Amiga, Apple, BeOS, QNX4, UFS, etc.
[/LIST]
Testing/Logging and debug stuf:
[LIST]
[*]Network testing
[*]Network console logging 
[*]SCSI logging and verbose mode
[*]Kernel hacking and debugging (this is for develops, disable won't prevent the usual kernel/boot logs)
[/LIST]

huge list of stuff make your kernel bigger and compilation times longer ;)

Another thing is the "built-in" way vs. "modules" way. 
Ubuntu (or any distro with packaged kernel) use build all modules as... modules, since they will be loaded by users as needed. Build inside kernel would be a nonsense waste or a lot of stuff would have to be non-supported.

But if you build your own kernel you can build them inside kernel, since you know what you will need. This is suppose to improve responsiveness at cost of some miliseconds of kernel load time. From the moment it loads, all will be in memory. Do a lsmod and check what you have always loaded any session, not dependen on hardware that can be unplugged. Then move those for <m> to <y>. 
Becarefull only with filesystem modules. Would  be better not touch those under ubunut, cause either initrd config and usplash need them as modules.

Have fun playing with it 
:)

---

