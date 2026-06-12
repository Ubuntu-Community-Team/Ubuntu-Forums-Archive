---
title: "Install Nvidia driver offline"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by LordxAngel on 2007-07-04
Hi there , i am wondering if there is away to install Nvidia driver offline for Feisty fawn, since i can't get my modem to work under ubuntu "for now" , i tried to do it and it went fine at first but it's asking for a missing headers ???

 i am on windows vista machine right now so i have to download those "headers" and put them on a pen memory 

can you help me ? :confused:

---

### Post by Vajra Vrtti on 2007-07-04
See my post (#3) int his thread: [http://ubuntuforums.org/showthread.php?t=491621](http://ubuntuforums.org/showthread.php?t=491621)

Use that process on you Feisty machine to generate the download script. In the script you will have the location of the packages so that you can download the in your Windows box. Then add them to Synaptic.

---

### Post by LordxAngel on 2007-07-04
thanks for the quick reply but it didn't work :(
i don't see any script ???????

this is how i was installing the driver :

alt+ctrl+f2 
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run

then i get everything going it warns me that ( there is no precompiled kernel to match mine ) i choose OK to compile a new kernel interface 

then an error appears saying that i don't have a header libc installed ????? and to install distribution's libc development package ??? 

where can i find it ? and how to install this package offline ? :confused::confused:

---

### Post by LordxAngel on 2007-07-04
this is the log of the error i got :

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Jul  4 00:48:26 2007

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
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by Vajra Vrtti on 2007-07-04
I'm sorry I can't help you right now but it's really late in my time zone. But I will surely answer you tomorrow.

---

### Post by Nythain on 2007-07-04
couldnt you just head over to
[http://packages.ubuntu.com](http://packages.ubuntu.com)
in windows... then search for nvidia-glx (or nvidia-glx-new), download the package for your version of ubuntu (feisty, edgy, dapper) and any of its dependencies you dont have installed already (probably just linux-restricted-module-common, but there could be more, and that one might already be installed)... burn them to a cd, or save them to one of your ubuntu partitions... then sudo dpkg -i anydependencies.deb then sudo dpkg -i whatevertheglxpackageisnamed.deb

not sure how many dependencies you are going to have to meet, but it shouldnt be many if any at all (most should have been installed with the base system installation)

---

### Post by mmogar on 2007-07-04
LordxAngel,

Try this- open the Synaptic and go to Edit / Add CDRom. Put in the Ubuntu CD and let it load.
Do a search in Synaptic for "build"
Look for build_essentials and install that.
That should take care of the compiling errors that you are getting

---

### Post by Vajra Vrtti on 2007-07-04
In Ubunto, do as follows:
[LIST=1]
[*]In Synaptic, mark the package **nvidia-glx** for installation.
[*]Accept the required dependencies, if any.
[*]Click *File -> Generate package download script*.
[*]Type the name of the file to hold the script.
[*]Save the file.
[*]Quit Synaptic discarding the changes.
[/LIST]
The saved file contains the list of deb files to be downloaded in Windows.
After downloading, take those files to your Ubuntu box.
Install them in Synaptic using *File -> Add downloaded packages.*

---

