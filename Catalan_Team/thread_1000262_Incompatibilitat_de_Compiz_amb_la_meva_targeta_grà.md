---
title: "Incompatibilitat de Compiz amb la meva targeta gràfica?"
date: 2008-12-02
forum: Catalan Team
---

### Post by mcako on 2008-12-02
Hola,
He instal·lat compiz però al canviar els Efectes Visuals des de Aparença em diu que "No s'han pogut habilitar els efectes d'escriptori"
De la mateixa manera em surt el següent al executar compiz per terminal:
```

~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

Representa que he d'instal·lar algo de Xgl? Desinstal·lant compiz em sembla que m'he carregat algo de l'OpenGL..

Cal dir que la targeta gràfica que tinc és de l'any de la picor, una ELSA ERAZOR X GeForce 256 de Nvidia. 

Respecte els drivers de la targeta:
```

~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV10 [GeForce 256 SDR] (rev 10)

```

He provat de instal·lar-me algun altre driver amb l'Envy però s'ha liat i ho he tornat a deixar com abans.

No sé que fer, potser millor oblidar-me de posar xorradetes amb la targeta gràfica que tinc, no?

---

### Post by tanreb20 on 2008-12-03
Quina versio de ubuntu fas servir?

[http://www.theinquirer.es/2008/05/05/comprueba_si_tu_equipo_soporta_compiz_antes_de_instalarlo.html](http://www.theinquirer.es/2008/05/05/comprueba_si_tu_equipo_soporta_compiz_antes_de_instalarlo.html)

Prova de anar a aquest link

et dira que et descarreguis un script, que un coop executat et comprovará si la teva grafica es compatible.

SORT!

---

### Post by mcako on 2008-12-04
He executat l'script com m'has dit i em surt el següent:
```

$ ./compiz-check

Gathering information about your system...

 Distribution:          **Ubuntu 8.10**
 Desktop environment:   **GNOME**
 Graphics chip:         **nVidia Corporation NV10 [GeForce 256 SDR] (rev 10)**
 Driver in use:         **nv**
 Rendering method:      **[COLOR="Red"]None[/COLOR]**

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 [COLOR="Orange"]Error[/COLOR]: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The nv driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y

```

Al dir-li que em busqui un driver se m'obre la finestra de "Controladors de maquinari" però no em surt cap driver disponible i es queda tant panxo.
Alguna idea?

---

### Post by tanreb20 on 2008-12-04
Uhmm segons aixo no tens renderitzacio.

Pot ser que la teva tarjeta no admeti aceleracio 3D! És una pena?

---

### Post by PatrickVogeli on 2008-12-05
pasa que la teva tarjeta es tan vella que els drivers que hi han a l'ubuntu ja no la suporten. Per tenir acceleració 3D hauries de fer servir aquests drivers:

[http://www.nvidia.com/object/linux_display_amd64_71.86.06.html](http://www.nvidia.com/object/linux_display_amd64_71.86.06.html) 64 bits
[http://www.nvidia.com/object/linux_display_x86_71.86.06.html](http://www.nvidia.com/object/linux_display_x86_71.86.06.html) 32 bits

el problema es que aquestes versions no incorporen els canvis per fer anar compiz ells sols, i hauries d'utilitzar, a més, les extensions XGL, que porten altres problemes i el rendiment no és massa bo. Si a més aquesta gràfica tampoc es gaire cosa... jo passaria de compiz, dubto que t'anés massa bé.

salut

---

### Post by CarlesOriol on 2008-12-06
O via apt/aptitude/synaptic canviar els drivers pels nvidia-glx-71 que suporten les velles nvidia (fins i tot les tnt).

Amb això probablement podras usar el controlador privatiu nvidia en comptes del nv cosa que et permetrà que alguns programes tipus reproductors de video, jocs ... vagin amb més fluidesa. I si tens prou memòria gràfica a la targeta ( o aquesta gestiona correctament -i veloçment sinò no anem bé- l'agp podras usar el compiz.

NOTA:Aquesta operació és un pel delicada. Asegura't de tenir experiència usant la linia de comandes ja que les proves fallides et duran a un sistema on sols et funcionarà el terminal i l'hauras de recuperar manualment.
Jo personalment quan faig aquestes coses conecto a l'ordinador on faig els tests a un altre via ssh (amb l'opció -X) en entorn gràfic on m'hi trobo més cómode. (en papapep aquí m'excomulga de l'esglesia de la santa tecla)

---

### Post by mcako on 2008-12-10
Gràcies per les respostes, he provat les 2 coses que m'heu dit però tot i així no hi ha hagut sort. Cal dir que no en tinc gaire idea del tema així que molt probablement no m'expliqui gaire bé.

He provat d'instal·lar el driver nvidia-glx-71 però m'ha dit que ja el tenia instal·lat, així que no he sabut gaire que fer. A la web de Nvidia m'he descarregat el nvidia-xconfig que m'ha configurat els drivers de la meva targeta però em sembla que no li han acabat d'agradar a l'Ubuntu.
Tot i així també he provat d'instal·lar els drivers que m'ha dit el PatrickVogeli però m'ha dit que des de X server no podia instal·lar-los, així que he sortit del sistema per intentar entrar en mode consola i poder instal·lar-los i m'ha dit que no li molaven els drivers que li havia posat des del nvidia-xconfig, i m'ha donat les opcions de restaurar l'estat anterior o córrer en baixa resolució, li he dit de córrer en baixa resolució i s'ha quedat mig penjat. Li he donat a ctrl-alt-F4 per obrir una consola virtual i he intentat instal·lar els drivers que no em deixava instal·lar des de X server i llavors m'ha dit que necessitava un kernel d'interficie precompilat, que si volia que se'l descarregués del ftp d'Nvidia (tot això que explico es veu al log que he posat mes avall), li he dit que sí i llavors ha dit que no havia trobat cap kernel i que intentaria compilar-lo ell, però m'ha donat un "ERROR: Unable to build the NVIDIA kernel module.", degut a errors de compilació. Curiosament avui també he intentat crear un modul de kernel per la webcam que volia instal·lar i també m'ha donat errors de compilació quasi clavats, concretament:
```

 : error: asm/semaphore.h: No such file or directory

```

Vist tot això, he restaurat el fitxer xorg.conf i he fet startx per tornar a tenir-ho tot com abans.

Així que no sé que fer, em sembla que ho deixaré estar, perquè com heu dit, encara que ho fes funcionar m'aniria bastant lent segurament.

Us poso el log de l'instal·lador per si us serveix d'algo:
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Dec 10 21:06:01 2008
installer version: 1.0.7

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
  no cc version check     : false
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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 71.86.06.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27-9-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-9-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-9-generi
   c/build SYSOUT=/lib/modules/2.6.27-9-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-9-generic/build SUBDIRS=
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz29621/NVIDIA-Linux-x86-71.86.0
   6-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.27-9-generic/arch/x86/include -i
   nclude include/linux/autocon
   f.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-
   strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -
   msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -ma
   rch=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchro
   nous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/
   mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibl
   ing-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz2
   9621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mul
   tichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_
   NAMES -D__KERNEL__ -DMODULE -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__K
   ERNEL__ -DMODULE -DNV_VERSION_STRING=\"71.86.06\" -DNV_UNIX -DNV_LINUX -DNV_
   INT64_OK -DNVCPU_X86 -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s"
   -D"KBUILD_BASENAME=KBUILD_STR(nv)" 
    -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz29621/NVIDIA-Linux-x
   86-71.86.06-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz29621/NVIDIA-Linux-x86-71.8
   6.06-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm/bitops.h: In function &#8216;set_bit&#8217;:
   include/asm/bitops.h:60: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
   include/asm/bitops.h:97: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:1971: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:983,
                    from /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv/nv-linux.h:83,
                    from /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv-linux.h:104:27
   : error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv/nv-linux.h:106,
                    from /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv-linux.h: In fu
   nction &#8216;nv_execute_on_all_cpus&#8217;:
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv-linux.h:595: e
   rror: too many arguments to function &#8216;on_each_cpu&#8217;
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c: In function
   &#8216;__nv_setup_pat_entries&#8217;:
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:887: warning
   : comparison between signed and unsigned
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c: In function
   &#8216;__nv_restore_pat_entries&#8217;:
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:913: warning
   : comparison between signed and unsigned
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c: In function
   &#8216;nv_kern_cpu_callback&#8217;:
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1239: warnin
   g: comparison between signed and unsigned
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1242: error:
   too many arguments to function &#8216;smp_call_function&#8217;
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1246: warnin
   g: comparison between signed and unsigned
   /tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1249: error:
   too many arguments to function &#8216;smp_call_function&#8217;
   make[3]: *** [/tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.
   o] Error 1
   make[2]: *** [_module_/tmp/selfgz29621/NVIDIA-Linux-x86-71.86.06-pkg1/usr/sr
   c/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

---

