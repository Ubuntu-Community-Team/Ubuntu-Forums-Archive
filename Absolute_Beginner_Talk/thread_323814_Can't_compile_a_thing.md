---
title: "Can't compile a thing"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by albesan on 2006-12-22
hello team,

I'm very ussuccesfully trying to compile a driver or two, and I keep getting this error:

gcc -O2 -Wall -I/home/alberto/dmx4linux-2.5+dfsg.orig/include -I/lib/modules/2.6.15-27-powerpc/build/include -Wstrict-prototypes -D__KERNEL__ -DMODULE -DDMXVERSION=\"2.5\" -DMODVERSIONS -include /lib/modules/2.6.15-27-powerpc/build/include/linux/modversions.h -DDMXOUTMINOR=223 -DDMXINMINOR=224 -DVERSIONMAJOR=2 -DVERSIONMINOR=5   -c -o dmx_dev.o dmx_dev.c
cc1: error: /lib/modules/2.6.15-27-powerpc/build/include/linux/modversions.h: No such file or directory



Idid a search for the directory and apparently doesn't exist.

I did specify the path : /lib/modules/2.6.15-27-powerpc/build/include , when I was promted by ./configure

can someone translate this please.

thanks.

---

### Post by macogw on 2006-12-22
Well your compile command specifies: 
-DMODVERSIONS -include /lib/modules/2.6.15-27-powerpc/build/include/linux/modversions.h 

which apparently doesn't exist on your computer, so you may want to specify that it go somewhere else, but I don't know where.  Where'd you find that command?

---

### Post by albesan on 2006-12-22
Hello, thanks for the quick response.

I did a search and found these:

 locate modversions.h
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/modversions.h
/usr/src/linux-headers-2.6.15-26/include/config/modversions.h
/usr/src/linux-headers-2.6.15-27-powerpc/include/linux/modversions.h:
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/modversions.h
/usr/src/linux-headers-2.6.15-27/include/config/modversions.h

I tried changing the path but I got the same error

?

a.

---

### Post by az on 2006-12-22
What module are you trying to build?

Some upstream source is not smart enough to use just the kernel headers.

---

### Post by albesan on 2006-12-22
I'm not sure what is the module being built, I'm trying to compile dmx4linux which are dmx drivers for linux, dmx being the lighting adrressing protocol.

---

### Post by az on 2006-12-23
> **albesan said:**
> I'm not sure what is the module being built, I'm trying to compile dmx4linux which are dmx drivers for linux, dmx being the lighting adrressing protocol.

This page:
[http://llg.cubic.org/dmx4linux/](http://llg.cubic.org/dmx4linux/)
implies that the driver is not yet fully working with 2.6 kernels.

"Roadmap

The 2.5 version will be the last release for the Linux 2.4 series. Apart from bugfixes we won't do any further development with this code. We plan to make a quick 'n dirty port of dmx4linux 2.5 to the Linux 2.6 series (v2.9). After that we'll make a complete redesign of the driver architecture which will eventually be released as dmx4linux 3.0 and support Linux 2.6 and later kernels."

---

### Post by albesan on 2006-12-23
Yes I know,

But I found these and I thought I'd give them a go:


[http://www.opendmx.net/news.php?readmore=6](http://www.opendmx.net/news.php?readmore=6)


They are supposed to be ok for 2.6 kernels

thanks

a.

---

### Post by albesan on 2006-12-23
hello again,

There have been some developments.

I found out about some hidden dependencies and sorted them out, I managed to make and make install without errors.

The next step, according to the documentation is :

"ldconfig"

then

"make devinodes # to create device inodes in /dev"


Now, when I run "make devinodes" I get this output:

 sudo make devinodes
cd drivers ; make devinodes
make[1]: Entering directory `/home/alberto/dmx4linux-2.9-ba-061001/drivers'
./setup_devs install
cp: cannot stat `/etc/modules.conf': No such file or directory
./setup_devs: line 10: /etc/modules.conf.bak: No such file or directory
cp: cannot stat `/etc/modules.conf': No such file or directory
make[1]: Leaving directory `/home/alberto/dmx4linux-2.9-ba-061001/drivers'

So if I'm getting any of this it can not find "/etc/modules.conf".

I checked whether the file exists on my system and I get this:

 locate modules.conf
/var/lib/dpkg/info/libpam-modules.conffiles
/var/lib/dpkg/info/perl-modules.conffiles
/etc/gnome-vfs-2.0/modules/ssl-modules.conf
/etc/gnome-vfs-2.0/modules/mapping-modules.conf
/etc/gnome-vfs-2.0/modules/default-modules.conf
/etc/modules.conf

So the directory path and file exists, does his happen much? What can I do about it?
Any coments appreciated, thanks


a.

---

### Post by az on 2006-12-23
Ubuntu uses /etc/modprobe.d instead of modules.conf

---

### Post by albesan on 2006-12-23
oh I see... many thanks for the reply.

And do youknow how to go about rectifying that? Or could you please point me in the direction where I could find the process described?.

Thanks

a.

---

### Post by albesan on 2006-12-24
I'm still hunting this one down any help would be greatly appreciated.

Right, so I got as far as make installing QLC.

When I try to run it I get this output:

:~$ qlc
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
open /dev/rtc: No such file or directory
open /dev/misc/rtc: No such file or directory


A search for /rtc outputs:
locate  /rtc
/lib/modules/2.6.15-26-powerpc/kernel/drivers/i2c/chips/rtc8564.ko
/lib/modules/2.6.15-27-powerpc/kernel/drivers/i2c/chips/rtc8564.ko
/usr/include/linux/rtc.h
/usr/src/linux-headers-2.6.15-26-powerpc/include/linux/rtc.h
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/gen/rtc
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/gen/rtc/module.h
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/gen/rtc/x.h
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/sensors/rtc8564
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/sensors/rtc8564/module.h/usr/src/linux-headers-2.6.15-26-powerpc/include/config/rtc
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/rtc/x1205
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/rtc/x1205/i2c
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/rtc/x1205/i2c/module.h
/usr/src/linux-headers-2.6.15-26/include/asm-alpha/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-arm/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-cris/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-generic/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-i386/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-m32r/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-m68k/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-mips/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-parisc/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-powerpc/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-ppc/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-sh/cpu-sh3/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-sh/cpu-sh4/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-sh/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-sparc/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-sparc64/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-x86_64/rtc.h
/usr/src/linux-headers-2.6.15-26/include/linux/rtc.h
/usr/src/linux-headers-2.6.15-26/include/config/gen/rtc.h
/usr/src/linux-headers-2.6.15-26/include/config/gen/rtc
/usr/src/linux-headers-2.6.15-26/include/config/gen/rtc/x.h
/usr/src/linux-headers-2.6.15-26/include/config/sensors/rtc8564.h
/usr/src/linux-headers-2.6.15-26/include/config/rtc
/usr/src/linux-headers-2.6.15-26/include/config/rtc/x1205
/usr/src/linux-headers-2.6.15-26/include/config/rtc/x1205/i2c.h
/usr/src/linux-headers-2.6.15-27-powerpc/include/linux/rtc.h
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/gen/rtc
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/gen/rtc/module.h
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/gen/rtc/x.h
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/sensors/rtc8564
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/sensors/rtc8564/module.h/usr/src/linux-headers-2.6.15-27-powerpc/include/config/rtc
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/rtc/x1205
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/rtc/x1205/i2c
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/rtc/x1205/i2c/module.h
/usr/src/linux-headers-2.6.15-27/include/asm-alpha/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-arm/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-cris/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-generic/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-i386/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-m32r/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-m68k/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-mips/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-parisc/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-powerpc/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-ppc/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-sh/cpu-sh3/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-sh/cpu-sh4/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-sh/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-sparc/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-sparc64/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-x86_64/rtc.h
/usr/src/linux-headers-2.6.15-27/include/linux/rtc.h
/usr/src/linux-headers-2.6.15-27/include/config/gen/rtc.h
/usr/src/linux-headers-2.6.15-27/include/config/gen/rtc
/usr/src/linux-headers-2.6.15-27/include/config/gen/rtc/x.h
/usr/src/linux-headers-2.6.15-27/include/config/sensors/rtc8564.h
/usr/src/linux-headers-2.6.15-27/include/config/rtc
/usr/src/linux-headers-2.6.15-27/include/config/rtc/x1205
/usr/src/linux-headers-2.6.15-27/include/config/rtc/x1205/i2c.h


I've read the Real Time Clock is normally enabled by default, but it doesn't seem so.
If anyone can give me a hand would be great.

a.

---

### Post by albesan on 2006-12-27
bump

---

