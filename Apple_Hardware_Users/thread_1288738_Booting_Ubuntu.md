---
title: "Booting Ubuntu"
date: 2009-10-11
forum: Apple Hardware Users
---

### Post by T4tav on 2009-10-11
Hi all. Im here to make everyone's brains work again...

I have a MBP 5,1.
Im trying to install Ubuntu Studio 9.04 onto my Macbook Pro.
I have completed the installation, however when it gets to install grub, it fails. I have tried lilo, but that didn't help either. 

Im now moving on to try and install Grub2 64 bit, but I can't compile it, and also have no idea what to do now!

I am actually confused :/

Can anyone shed some light on this ? 
(Thanks)

EDIT
I found the binary for the efi file in another thread. But now I don't know how to set the config up :/

Here is the output from diskutil list

```

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *320.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            265.3 GB   disk0s2
   3:       Microsoft Basic Data BOOTCAMP                34.2 GB    disk0s3
   4:       Microsoft Basic Data                         19.4 GB    disk0s4
   5:                 Linux Swap                         891.6 MB   disk0s5


```
4 is the root for linux
5 is the swap

Here is my current grub.cfg (I don't think it's correct though)

```

menuentry "MacOSX" {
  # Search the root device for Mac OS X's loader.
  search --set /usr/standalone/i386/boot.efi
  # Load the loader.
  chainloader /usr/standalone/i386/boot.efi
}

menuentry "GNU/Linux" {
  # Set the root device for GNU/Linux.
  search --set /boot/vmlinuz
  # Load the kernel and initrd.
  linux /boot/vmlinuz video=vesafb agp=off acpi=force libata.atapi_enabled=1 init=/linuxrc root=/dev/sda4 pcboot=cdrom gpt
  initrd /boot/initrd
}

menuentry "Ubuntu Studio sda4" {
	fakebios
	root=hd0,4
	linux /vmlinuz root=/dev/sda4 noefi
	initrd /initrd.img
}
menuentry "MBR1" {
   appleloader HD
}
menuentry " REBOOT" {
reboot
}

```


Trying to boot to linux for that cfg I get the following :
```

ROM image present.
Error : You need to load the kernel first 

```
Or something along those lines

---

### Post by coolbeans777 on 2009-10-11
what did you use to boot the disk, did you use refit? cuz if you have an intel mac then refit will work, im not sure about ppc though

---

### Post by jeremyswalker on 2009-10-11
> **T4tav said:**
> ```
menuentry "Ubuntu Studio sda4" {
	fakebios
	root=**hd0,4**
	linux /vmlinuz root=**/dev/sda4** noefi
	initrd /initrd.img
}


```


One thought: "root=hd0,4" does not equal "/dev/sda4". "root=hd0,3" would equal "/dev/sda4"

---

### Post by T4tav on 2009-10-12
I'm back after a tiresome night *yawn*.

I installed Ubuntu Studio via refit just went through the standard install.
Im using a 32 bit install, not 64 bit.

OLD As for changing "root=hd0,4" to "root=hd0,3". I still get the following error. OLD

Here is my new grub.cfg that appears to be working...

```

menuentry "MacOSX" {
  # Search the root device for Mac OS X's loader.
  search --set /usr/standalone/i386/boot.efi
  # Load the loader.
  chainloader /usr/standalone/i386/boot.efi
}

menuentry "Ubuntu Studio sda4" {
	fakebios
	root=hd1,4
	linux /vmlinuz root=/dev/sda4 noefi
	initrd /initrd.img
}

```

But now it freezes when loading. I'm going to post the error in a second. Need to write it down.

```

ROM image present.
    [Linux-bzImage, setup=8x30000, ize=0x35ca90]
Video Mode: 1440x900-32
Frame buffer base: 0xb0030000
Video line length 8192
    [Initrd, addr=0x3f89c000, size=0x7531bf]

```

```

This is all old now
[code]
ROM image present.
Error : You need to load the kernel first

```

Here is my current cfg

```

menuentry "MacOSX" {
  # Search the root device for Mac OS X's loader.
  search --set /usr/standalone/i386/boot.efi
  # Load the loader.
  chainloader /usr/standalone/i386/boot.efi
}

menuentry "GNU/Linux" {
  # Set the root device for GNU/Linux.
  search --set /boot/vmlinuz
  # Load the kernel and initrd.
  linux /boot/vmlinuz video=vesafb agp=off acpi=force libata.atapi_enabled=1 init=/linuxrc root=/dev/sda4 pcboot=cdrom gpt
  initrd /boot/initrd
}

menuentry "Ubuntu Studio sda4" {
	fakebios
	root=hd0,3
	linux /vmlinuz root=/dev/sda4 noefi
	initrd /initrd.img
}

menuentry "MBR1" {
   appleloader HD
}
menuentry " REBOOT" {
reboot
}

```

The only thing that works in that is the MBR load (Windows) and the reboot command :/

I thought I better post the ls of the directory too.

```

macbook-pro:Untitled Tavis$ ls
bin		home		mnt		selinux		var
boot		initrd.img	opt		srv		vmlinuz
cdrom		lib		proc		sys
dev		lost+found	root		tmp
etc		media		sbin		usr

```
[/code]

Somethings not right here methinks :confused:

---

### Post by pxwpxw on 2009-10-12
For grub2 (efi or pc) hd0,4 is partition 4 and should have loaded the kernel for the originl menuentry -

```

menuentry "Ubuntu Studio sda4" {
	fakebios
	root=hd0,4
	linux /vmlinuz root=/dev/sda4 noefi
	initrd /initrd.img
}

```

But if you use the other entries with search, you need this search format, with the -f , example for OSX (when using grub.efi)
```

menuentry "MacOSX" {
  search --set -f /usr/standalone/i386/boot.efi
  chainloader /usr/standalone/i386/boot.efi
}

```

To confirm, just use the grub command line to check - (for grub-pc or grub-efi)
```

grub:sh> search -f /vmlinuz

```
 The GNU/linux menuentry is crap. You have vmlinuz in / and the kernel commandline options here are mostly wrong, may have been for some other distro.  But you can use the search to find and set the grub root -
```

menuentry "GNU/Linux" {
  search --set -f /vmlinuz
  linux /vmlinuz video=efifb acpi=force root=/dev/sda4
  initrd /initrd
}

```

With efi boot,  if you lose video after loading the kernel, with Nvidia graphics you may need to add 

vidoe=efifb single 

to your linux /vmlinuz line to reach a root console to sort out the problem.

---

### Post by T4tav on 2009-10-12
Ok. If I use this

```

menuentry "GNU/Linux" {
  search --set -f /vmlinuz
  linux /vmlinuz video=vesafb agp=off acpi=force libata.atapi_enabled=1 init=/linuxrc root=/dev/sda4 pcboot=cdrom gpt
  initrd /initrd.img
}

```

Ok, It loads now. But xorg says that there are no displays/screens :/

Keyboard doesn't work either.

Also I see a error when ubuntu is loading about init=/linuxrc

---

### Post by pxwpxw on 2009-10-12
> **T4tav said:**
> Ok. If I use this

```

menuentry "GNU/Linux" {
  search --set -f /vmlinuz
  linux /vmlinuz video=vesafb agp=off acpi=force libata.atapi_enabled=1 init=/linuxrc root=/dev/sda4 pcboot=cdrom gpt
  initrd /initrd.img
}

```

Ok, It loads now. But xorg says that there are no displays/screens :/

Keyboard doesn't work either.

Also I see a error when ubuntu is loading about init=/linuxrc

Try it this way, I don't know what all those linux options do, you would have to ask the originator, 
```

menuentry "ubuntu 904" {
  fakebios
  search --set -f /vmlinuz
  linux /vmlinuz root=/dev/sda4 video=efifb noefi single   
  initrd /initrd.img
}

```

See where that gets you.

---

### Post by T4tav on 2009-10-12
Thanks, That got it booted nicely. Still can't get my keyboard to work, so I can't see if x.org is working :/

---

### Post by pxwpxw on 2009-10-12
> **T4tav said:**
> Thanks, That got it booted nicely. Still can't get my keyboard to work, so I can't see if x.org is working :/
Try adding acpi=force in the linux options.

---

### Post by T4tav on 2009-10-12
Woo. I got the keyboard back. Thanks.

Just got to battle with x.org now. Still say's that I have no display/screen

---

### Post by pxwpxw on 2009-10-12
> **T4tav said:**
> Woo. I got the keyboard back. Thanks.

Just got to battle with x.org now. Still say's that I have no display/screen

You may need to do this for xorg when using video=efifb (but some other MBP5x users may not)

grub2 efi bootloader 
Post #2 part 2. about editing /etc/X11/xorg.conf 

Section "Device"
Identifier "fbdev device"
Driver "fbdev"
EndSection

---

### Post by T4tav on 2009-10-13
> **pxwpxw said:**
> You may need to do this for xorg when using video=efifb (but some other MBP5x users may not)

grub2 efi bootloader 
Post #2 part 2. about editing /etc/X11/xorg.conf 

Section "Device"
Identifier "fbdev device"
Driver "fbdev"
EndSection

Thanks, That got x started for me. 
I managed to get the nvidia drivers installed too. But Now I get "Failed to load the NVIDIA module" or something like that.

Here's the log 
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Oct 13 23:47:28 2009
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
-> You appear to be running in runlevel 1; this may cause problems.  For exampl
   e: some distributions that use devfs do not run the devfs daemon in runlevel
   1, making it difficult for `nvidia-installer` to correctly setup the kernel 
   module configuration files.  It is recommended that you quit installation no
   w and switch to runlevel 3 (`telinit 3`) before installing.
   
   Quit installation now? (select 'No' to continue installation) (Answer: No)
-> License accepted.
-> Installing NVIDIA driver version 185.18.36.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-3-rt/build'
-> Kernel output path: '/lib/modules/2.6.28-3-rt/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.28-3-rt/bui
   ld SYSOUT=/lib/modules/2.6.28-3-rt/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.28-3-rt/build SUBDIRS=/home
   /tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_version
   s ; rm -f /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_versio
   ns/*
   make -f scripts/Makefile.build obj=/home/tavis/NVIDIA-Linux-x86-185.18.36-pk
   g1/usr/src/nv
     cc -Wp,-MD,/home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nv.o.d 
   -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL__  -
   Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -include inc
   lude/linux/autoconf.h -Iubuntu/include  -Wall -W
   undef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -W
   error-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-
   struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-m
   tune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwi
   nd-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach
   -default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-
   calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I/home/tavis/
   NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -W
   switch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multich
   ar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__K
   ERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -
   DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D
   "KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /home/tavis/NVIDIA-Linux-x86-185.
   18.36-pkg1/usr/src/nv/.tmp_nv.o /hom
   e/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:19,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n 'set_bit':
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type 'void *' used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n 'clear_bit':
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type 'void *' used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:19,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv.c:14:
   include/linux/prefetch.h: In function 'prefetch_range':
   include/linux/prefetch.h:57: warning: pointer of type 'void *' used in arith
   metic
   In file included from include/linux/utsname.h:35,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:19,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv.c:14:
   include/linux/sched.h: In function 'object_is_on_stack':
   include/linux/sched.h:2124: warning: pointer of type 'void *' used in arithm
   etic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:86,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv.c:14:
   include/linux/scatterlist.h: In function 'sg_virt':
   include/linux/scatterlist.h:199: warning: pointer of type 'void *' used in a
   rithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:87,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv.c:14:
   include/linux/irq.h: In function 'irq_to_desc':
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:113,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv.c:14:
   include/linux/highmem.h: In function 'zero_user_segments':
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
     cc -Wp,-MD,/home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nv-vm.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL_
   _  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -include
   include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes
   -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-de
   claration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-
   stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestand
   ing -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mm
   x -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protec
   tor -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-
   statement -Wno-pointer-sign -fwrapv -I/home/tavis/NVIDIA-Linux-x86-185.18.36
   -pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-sub
   scripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop 
   -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMOD
   ULE -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG -DMOD
   ULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MO
   DNAME=KBUILD_STR(nvidia)"  -c -o /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1
   /usr/src/nv/.tmp_nv-vm.o /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src
   /nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:19,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-vm.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n 'set_bit':
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type 'void *' used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n 'clear_bit':
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type 'void *' used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:19,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-vm.c:14:
   include/linux/prefetch.h: In function 'prefetch_range':
   include/linux/prefetch.h:57: warning: pointer of type 'void *' used in arith
   metic
   In file included from include/linux/utsname.h:35,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:19,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-vm.c:14:
   include/linux/sched.h: In function 'object_is_on_stack':
   include/linux/sched.h:2124: warning: pointer of type 'void *' used in arithm
   etic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:86,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-vm.c:14:
   include/linux/scatterlist.h: In function 'sg_virt':
   include/linux/scatterlist.h:199: warning: pointer of type 'void *' used in a
   rithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:87,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-vm.c:14:
   include/linux/irq.h: In function 'irq_to_desc':
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:113,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-vm.c:14:
   include/linux/highmem.h: In function 'zero_user_segments':
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
     cc -Wp,-MD,/home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.os-agp.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -includ
   e include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototyp
   es -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function
   -declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferr
   ed-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreest
   anding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno
   -mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-pro
   tector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-aft
   er-statement -W
   no-pointer-sign -fwrapv -I/home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wpa
   rentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_S
   TRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" 
   -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)
   "  -c -o /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_os-agp.
   o /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:19,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /os-agp.c:24:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n 'set_bit':
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type 'void *' used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n 'clear_bit':
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type 'void *' used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:19,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /os-agp.c:24:
   include/linux/prefetch.h: In function 'prefetch_range':
   include/linux/prefetch.h:57: warning: pointer of type 'void *' used in arith
   metic
   In file included from include/linux/utsname.h:35,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:19,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /os-agp.c:24:
   include/linux/sched.h: In function 'object_is_on_stack':
   include/linux/sched.h:2124: warning: pointer of type 'void *' used in arithm
   etic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:86,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /os-agp.c:24:
   include/linux/scatterlist.h: In function 'sg_virt':
   include/linux/scatterlist.h:199: warning: pointer of type 'void *' used in a
   rithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:87,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /os-agp.c:24:
   include/linux/irq.h: In function 'irq_to_desc':
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:113,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /os-agp.c:24:
   include/linux/highmem.h: In function 'zero_user_segments':
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
     cc -Wp,-MD,/home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.os-inte
   rface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__
   KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -
   include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-pr
   ototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fu
   nction-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2 -marc
   h=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-co
   mpare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow
   -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-poi
   nter -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-
   sign -fwrapv -I/home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv -Wall 
   -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -
   Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno
   -cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185
   .18.36\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_B
   ASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c
   -o /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_os-interface.
   o /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:19,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /os-interface.c:26:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n 'set_bit':
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type 'void *' used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n 'clear_bit':
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type 'void *' used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:19,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /os-interface.c:26:
   include/linux/prefetch.h: In function 'prefetch_range':
   include/linux/prefetch.h:57: warning: pointer of type 'void *' used in arith
   metic
   In file included from include/linux/utsname.h:35,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:19,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /os-interface.c:26:
   include/linux/sched.h: In function 'object_is_on_stack':
   include/linux/sched.h:2124: warning: pointer of type 'void *' used in arithm
   etic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:86,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /os-interface.c:26:
   include/linux/scatterlist.h: In function 'sg_virt':
   include/linux/scatterlist.h:199: warning: pointer of type 'void *' used in a
   rithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:87,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /os-interface.c:26:
   include/linux/irq.h: In function 'irq_to_desc':
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nv-linux.h:113,
                    from /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /os-interface.c:26:
   include/linux/highmem.h: In function 'zero_user_segments':
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:136: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   include/linux/highmem.h:139: warning: pointer of type 'void *' used in arith
   metic
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c: In fu
   nction 'os_alloc_sema':
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c:130: e
   rror: incompatible types in assignment
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c: In fu
   nction 'os_acquire_sema':
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c:174: w
   arning: passing argument 1 of '_spin_lock_irqsave' from incompatible pointer
   type
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c:178: w
   arning: passing argument 1 of '_spin_unlock_irqrestore' from incompatible po
   inter type
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c:185: w
   arning: passing argument 1 of '_spin_unlock_irqrestore' from incompatible po
   inter type
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c: In fu
   nction 'os_cond_acquire_sema':
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c:208: w
   arning: passing argument 1 of '_spin_lock_irqsave' from incompatible pointer
   type
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c:211: w
   arning: passing argument 1 of '_spin_unlock_irqrestore' from incompatible po
   inter type
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c:218: w
   arning: passing argument 1 of '_spin_unlock_irqrestore' from incompatible po
   inter type
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c: In fu
   nction 'os_release_sema':
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c:242: w
   arning: passing argument 1 of '_spin_lock_irqsave' from incompatible pointer
   type
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c:253: w
   arning: passing argument 1 of '_spin_unlock_irqrestore' from incompatible po
   inter type
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c: In fu
   nction 'os_acquire_spinlock':
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c:1322: 
   warning: passing argument 1 of '_spin_lock_irqsave' from incompatible pointe
   r type
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c: In fu
   nction 'os_release_spinlock':
   /home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.c:1333: 
   warning: passing argument 1 of '_spin_unlock_irqrestore' from incompatible p
   ointer type
   make[3]: *** [/home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-inte
   rface.o] Error 1
   make[2]: *** [_module_/home/tavis/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   ] Error 2
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

