---
title: "[SOLVED] iMac 24&amp;quot; ... not in 1920x1200"
date: 2007-11-26
forum: Apple Intel Users
---

### Post by AlainJLEB on 2007-11-26
Hi there,

I've just installed Kubuntu on a new iMac 24", but it cannot get higher than 1600*1200, while it supposed to be able to get 1920*1200 ... any idea why? One thing: it is using the vesa driver, while I was expecting something like the ATI one ... which is installed.

On the audio side, it is not working at all as well ... HDA Intel is detected, but no way to have a sound ... 

Alain

Btw: where is the pipe sign on iMac keyboard ????

---

### Post by macaholic on 2007-11-26
How did you install the ATI driver? What is the output of "fglrxinfo"? Just another thing to note, if it is the same model, this tutorial goes pretty in-depth on how to get certain things working [http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24)

---

### Post by Sawta on 2007-11-27
> **macaholic said:**
> Just another thing to note, if it is the same model, this tutorial goes pretty in-depth on how to get certain things working [http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24)

Keep in mind that he is planing on running Kubuntu and not plain old Ubuntu.  I'm not sure if it makes much of a difference, as I haven't messed around with Kubuntu yet, but I wouldn't be surprised if it did. ;)

---

### Post by cyberdork33 on 2007-11-27
> **Sawta said:**
> Keep in mind that he is planing on running Kubuntu and not plain old Ubuntu.  I'm not sure if it makes much of a difference, as I haven't messed around with Kubuntu yet, but I wouldn't be surprised if it did. ;)
It shouldn't for installing fglrx since that has nothing to do with Gnome or KDE, but rather Xorg.

---

### Post by AlainJLEB on 2007-11-27
Hi there,

I have installed fglrx ... but how can I configure X to use it? atipanel only shows a message stating I use Mesa ... 

Rgs

---

### Post by cyberdork33 on 2007-11-27
> **AlainJLEB said:**
> Hi there,

I have installed fglrx ... but how can I configure X to use it? atipanel only shows a message stating I use Mesa ... 

Rgs

Then it is not working.
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by AlainJLEB on 2007-11-27
The software is installed, but when I want to run the aticonfig program I face the following issue:

```
alain@imac:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-2
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfd06aba ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d2192b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cca050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:03 7192584    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:03 7192584    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7ca6000-b7ca7000 rw-p b7ca6000 00:00 0
b7ca7000-b7ca9000 r-xp 00000000 08:03 9044942    /lib/tls/i686/cmov/libdl-2.6.1.so
b7ca9000-b7cab000 rw-p 00001000 08:03 9044942    /lib/tls/i686/cmov/libdl-2.6.1.so
b7cab000-b7cac000 rw-p b7cab000 00:00 0
b7cac000-b7cb0000 r-xp 00000000 08:03 345438     /usr/lib/libXdmcp.so.6.0.0
b7cb0000-b7cb1000 rw-p 00003000 08:03 345438     /usr/lib/libXdmcp.so.6.0.0
b7cb1000-b7cb3000 r-xp 00000000 08:03 345427     /usr/lib/libXau.so.6.0.0
b7cb3000-b7cb4000 rw-p 00001000 08:03 345427     /usr/lib/libXau.so.6.0.0
b7cb4000-b7df8000 r-xp 00000000 08:03 9044939    /lib/tls/i686/cmov/libc-2.6.1.so
b7df8000-b7df9000 r--p 00143000 08:03 9044939    /lib/tls/i686/cmov/libc-2.6.1.so
b7df9000-b7dfb000 rw-p 00144000 08:03 9044939    /lib/tls/i686/cmov/libc-2.6.1.so
b7dfb000-b7dfe000 rw-p b7dfb000 00:00 0
b7dfe000-b7e21000 r-xp 00000000 08:03 9044943    /lib/tls/i686/cmov/libm-2.6.1.so
b7e21000-b7e23000 rw-p 00023000 08:03 9044943    /lib/tls/i686/cmov/libm-2.6.1.so
b7e23000-b7f10000 r-xp 00000000 08:03 345423     /usr/lib/libX11.so.6.2.0
b7f10000-b7f14000 rw-p 000ed000 08:03 345423     /usr/lib/libX11.so.6.2.0
b7f14000-b7f21000 r-xp 00000000 08:03 345440     /usr/lib/libXext.so.6.4.0
b7f21000-b7f22000 rw-p 0000d000 08:03 345440     /usr/lib/libXext.so.6.4.0
b7f22000-b7f23000 rw-p b7f22000 00:00 0
b7f23000-b7f2a000 r-xp 00000000 08:03 345462     /usr/lib/libXrender.so.1.3.0
b7f2a000-b7f2b000 rw-p 00006000 08:03 345462     /usr/lib/libXrender.so.1.3.0
b7f2b000-b7f30000 r-xp 00000000 08:03 345460     /usr/lib/libXrandr.so.2.1.0
b7f30000-b7f31000 rw-p 00005000 08:03 345460     /usr/lib/libXrandr.so.2.1.0
b7f34000-b7f3e000 r-xp 00000000 08:03 9011267    /lib/libgcc_s.so.1
b7f3e000-b7f3f000 rw-p 0000a000 08:03 9011267    /lib/libgcc_s.so.1
b7f3f000-b7f42000 rw-p b7f3f000 00:00 0
b7f42000-b7f5c000 r-xp 00000000 08:03 9011213    /lib/ld-2.6.1.so
b7f5c000-b7f5e000 rw-p 00019000 08:03 9011213    /lib/ld-2.6.1.so
bfcf2000-bfd07000 rw-p bfcf2000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
```

Any idea? I have created a bug report ... but is there a way of installing it in another way?

---

### Post by cyberdork33 on 2007-11-27
Please don't double post.

How did you install? I don't think the version in the repos works with your Mac yet. You need to get the newer version from the ATI website...

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by AlainJLEB on 2007-11-27
Do you mean using "Method 2: Install the Catalyst ..." ?

---

### Post by cyberdork33 on 2007-11-27
> **AlainJLEB said:**
> Do you mean using "Method 2: Install the Catalyst ..." ?
yep

---

### Post by AlainJLEB on 2007-11-28
Installing the latest driver went like a charm ... and it is now running fine.

```
alain@imac:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 2600 XT
OpenGL version string: 2.1.7059 Release

alain@imac:~$ glxgears
24652 frames in 5.0 seconds = 4930.332 FPS
25733 frames in 5.0 seconds = 5142.514 FPS
33225 frames in 5.0 seconds = 6644.809 FPS

alain@imac:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
5492 frames in 5.0 seconds = 1098.400 FPS
6511 frames in 5.0 seconds = 1302.200 FPS
8113 frames in 5.0 seconds = 1622.600 FPS
```

Last points to solve:
-) increase the resolution upto 1920*1200
-) the sound ... but there are enough threads on this
-) find the pipe sign on the keyboard

Thanks

---

### Post by cyberdork33 on 2007-11-28
> **AlainJLEB said:**
> Last points to solve:
-) increase the resolution upto 1920*1200
-) the sound ... but there are enough threads on this
-) find the pipe sign on the keyboard

Thanks
Pipe is the key above return. It also has the backslash on it.
Maybe you are on one of those new wireless keyboards?

---

