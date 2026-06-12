---
title: "help,,, nvidia"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by BAHammer on 2007-02-05
help im trying to install the drivers from the nvidia site and i have got past most of the errors but im stuck now 

im geting > nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Feb  4 22:17:59 2007

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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: Skipping the runlevel check (the utility `runlevel` failed to run).
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

im runing v 6.06 amd64 set.  
my card is a 6600 nvida card. 

far as i can tell i have the kernel source and devel instaed but im not sure if i did the right ones

---

### Post by Titus A Duxass on 2007-02-05
I can't help you with your problem directly however I can recommend that you try using Automatix to install the nvidia drivers, I find it the quickest and most straightforward method.

---

### Post by Contrid on 2007-02-05
Yes, automatix is the best solution.
[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by BAHammer on 2007-02-05
hmmm if its so good why is it not part of the standed install?

would this not be a good thing to have in the add remove program by defalt..

anyway giving it a try.

---

### Post by Perfect Storm on 2007-02-05
It's because it's a 3rd party project. Anyway if you want to do it manually (installing the drivers from the nvidia site):

Download the driver to your Desktop, then
```
cd ~/Desktop
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-XXXX-pkg1.run
sudo /etc/init.d/gdm start
```

or the drivers via apt-get/aptitude/synaptic:
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install nvidia-glx
sudo nano /etc/X11/xorg.conf
```

Change the card driver from "nv" to "nvidia"
Save and exit restart X <ctrl>+<alt>+<backspace>

If it fail you can edit the xorg.conf back to "nv"

---

### Post by BAHammer on 2007-02-05
it did not like what automatix did.. got my anwer there...
also looking at what it did seem to install the nvidia-glx not the drivers from the nvidia site wich i would think anyway would be better... 


going to give what ai said to do a try now

---

