---
title: "help install nvidia beta"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-12-20
can someone plz help me?
i tried the following way:
installed kernel-headers ( sudo apt-get install kernel-headers-$(uname -r) )
downloaded beta driver from nvidia site
stopped kdm
entered sudo sh NVIDIA...
but it gives me an error
this is the log of nvidia-installer
> 
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
-> Kernel source path: '/lib/modules/2.6.17-10-generic/build'
-> Kernel output path: '/lib/modules/2.6.17-10-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
ERROR: Unable to determine the NVIDIA kernel module filename.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).



i've been trying to install compiz on edgy kde with nvidia for a month now ](*,)

---

### Post by useResa on 2006-12-20
I have installed the beta driver by following the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=259913").

Maybe it will help you also with the installation.
Good luck.

---

### Post by bodhi.zazen on 2006-12-20
Easiest way is here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Latest Beta is available here: [http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

_Note_: These are now .deb :p

---

### Post by useResa on 2006-12-20
> **bodhi.zazen said:**
> Latest Beta is available here: [http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

_Note_: These are now .deb :p

Do you know which nvidia driver is installed from here.
Currently I am using the 1.0-9742 driver which I got from [here](http://www.nzone.com/object/nzone_downloads_linux_display_x86_1.0-9742.html).

---

### Post by bodhi.zazen on 2006-12-20
> **useResa said:**
> Do you know which nvidia driver is installed from here.
Currently I am using the 1.0-9742 driver which I got from [here](http://www.nzone.com/object/nzone_downloads_linux_display_x86_1.0-9742.html).

As far as I know it is the 1.0-9631 driver, but I am not sure how often the script is updated.

The biggest advantage is that it now (in theory) can be updated via aptitude (or synaptic), although one would likely need to drop out of X. I am not sure as I just started using this with Feisty and beryl 1.3. I do not update feisty daily and have not yet updated the nvidia driver :)

It looks that this is the way Ubuntu will be going though if I understand the goals of Feisty :)

I'll keep you posted :)

---

### Post by useResa on 2006-12-20
> **bodhi.zazen said:**
> As far as I know it is the 1.0-9631 driver, but I am not sure how often the script is updated.
Would you happen to know where this information can be obtained.

Since indeed it seems an easier way to get your nvidia driver updated, however once you have done it a few times (and unfortunately I have ;)), you get used to the "hard way".

---

### Post by bodhi.zazen on 2006-12-20
> **useResa said:**
> Would you happen to know where this information can be obtained.

Since indeed it seems an easier way to get your nvidia driver updated, however once you have done it a few times (and unfortunately I have ;)), you get used to the "hard way".

LOL I know EXACTLY what you mean.

---

### Post by ChineseDriver on 2006-12-21
I have the exact same problem he does

so far ive tried all these links, 
it wont install through the ways the links show
i still get the same error the good old fashioned way

---

