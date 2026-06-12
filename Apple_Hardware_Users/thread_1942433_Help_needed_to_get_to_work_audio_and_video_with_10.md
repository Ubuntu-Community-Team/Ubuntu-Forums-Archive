---
title: "Help needed to get to work audio and video with 10.4LTS on MBP 5.5"
date: 2012-03-17
forum: Apple Hardware Users
---

### Post by Segnale007 on 2012-03-17
Hello folks,

this is my first post here but I have used Ubuntu several years ago on my laptop before to actually decide to switch to Mac. 

However after 5 years I been using Mac I have decided to switch back to Linux for a bunch of things that I am not going to mention here this time..


Anyways, I have installed Ubuntu 10.4 LTS on my MacbookPro 5,5 and I don't seem to be able to get to work the audio card, even though according to alsamixer it is configured correctly.
I am using the kernel 2.6.38-13-generic and this is my sound card 

```

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)

```

What bother me most however is this bug with the nvidia-173 that when I weak up the macbook pro from sleep the brightness adjustment wont work, and I am stuck with the maximum of display luminosity that literally kills my eyes..

I have read of some people who have managed to get around this by installing the 195.30 nvidia driver. I downloaded it from nvidia but I cant seem to be able to install it.. Here's the log

```

creation time: Sat Mar 17 18:18:24 2012
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
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
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
-> Installing NVIDIA driver version 195.30.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.38-13-generic/build'
-> Kernel output path: '/lib/modules/2.6.38-13-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

Hopefully someone will be able to help a lost mac user who is looking forward to jump back to the safe road :)

Thanks

---

