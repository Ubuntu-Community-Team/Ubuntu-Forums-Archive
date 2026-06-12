---
title: "A whole paddock of frustrations"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by meeekael on 2005-07-18
Well.  I recently installed Linux.  I was enjoying it.  The installation was a breeze, it looked nice, and the terminal is very nice.  But I have been begining to encounter problems.  Well not really problems, but utter frustrations.

[b]Using Ubuntu 5.04 Hoary Hedgehog
i386 CD Install
Kernel: 2.6.10-5-386[/b]


**1st Problem**
Trying to install the Nvidia drivers from the Ubuntu CD
```
meeekael@meeekael:~/r32/alsa-driver-1.0.9rc4a$ cd /
meeekael@meeekael:/$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
meeekael@meeekael:/$ sudo apt-get install nvidia-settings
meeekael@meeekael:/$ sudo apt-get install nvidia-settings
Reading package lists... Done
Building dependency tree... Done
Package nvidia-settings is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-settings has no installation candidate
meeekael@meeekael:/$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
meeekael@meeekael:/$ sudo nvidia-glx-config enable

A backup of xorg.conf has been stored as:
/var/backups/xorg.conf.2005-07-19-14:14:03.
If the new configuration will not work you will be able to
revert the changes simply using this command:
cp /var/backups/xorg/xorg.conf.2005-07-19-14:14:03 /etc/X11/xorg.conf


Warning: your X configuration has been succesfully changed.
In order to take full advantage of the changes, X needs to
be restarted.

meeekael@meeekael:/$ sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
meeekael@meeekael:/$
```

meeekael@meeekael:/$ sudo apt-get install nvidia-glx: I have already done that line sucessfully, that's why it say 0 need updating...blah blah.  Just the NVIDIA settings is the problem.  It just does that.../looks at code *sigh*  The Nvidia logo comes up on start up, but that it it.

**Problem Two**
**Problem Two A)** Got no internet connection, because of my loverly winmodem.
I downloaded the Linux Driver from the Nvidia Website.
I opened ubantu in the terminal only mode, with X closed. Loaded up the run file, and here is how it went...

[COLOR=Blue]Page1:[/COLOR] Warning: Skipping run level check (Utility failed to run) - OK

[COLOR=Blue]Page2:[/COLOR] Terms and Conditions - ACCEPT

[COLOR=Blue]Page3:[/COLOR] **No precompiled kernel interface was found to match your kernel, should the installer download the kernel from FTP** - NO

[COLOR=Blue]Page4:[/COLOR] **No precompiled kernel interface was found to match your kernel; the installer will need to compile a new interface - OK**

[COLOR=Blue]Page5:[/COLOR] **[COLOR=Red]ERROR[/COLOR]: Inable to find kernel source tree for the currently running kernel.  Please make sure you have installed the kernel source files for your kernel; if you know the correct kernel source files are installed, you may specify the kernel source path with the `--kernel-source-path' command line option.**

What is the kernel source path command line option?

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Jul 19 14:25:59 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
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
WARNING: Skipping the runlevel check (the utility `runlevel` failed to run).
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

**Problem 3**
Tried to install the newest realtek ac'97 drivers....that didnt go well....
```
meeekael@meeekael:~$ cd home/meeekael
bash: cd: home/meeekael: No such file or directory
meeekael@meeekael:~$ cd/ home/meeekael
bash: cd/: No such file or directory
meeekael@meeekael:~$ c /home/meeekael
bash: c: command not found
meeekael@meeekael:~$ cd /home/meeekael
meeekael@meeekael:~$ cd /home/meeekael/r32/alsa-driver-1.0.9rc4a
meeekael@meeekael:~/r32/alsa-driver-1.0.9rc4a$ ./configure
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/meeekael/r32/alsa-driver-1.0.9rc4a
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
```

The first time it did that it installed a whole heap of files in a directory (was expecting that to happen), but i buffed up the copy.


So, in conclusion, I think there is something funky with my kernel.  I wouldn't have a clue how to fix it or how to do anything.  It jsut seems that the kernel is mentioned in every single error i get.  I will only buy a modem if it is a guaranteed way to fix my kernel.  So, please help a nub :).  When I say download, I mean I download in windows, then load the files onto my FAT32 drive then mount that into linux....I can do some things ;>

---

### Post by Knome_fan on 2005-07-19
Hi,

Problem 1:
Not really a problem at all. If the nvidia logo comes up, the nvidia driver is working just fine.
Nividia-settings is just a little tool that let's you tweak your nvidia card a bit, but it isn't really needed, so don't worry to much. I think the whole problem is that nvidia-settings isn't on the CD.

About your other problems, I think you simply need to install linux-headers-2.6.10-5-386 (note, I don't know if they are included on the CD), which should give you the kernel sources (or rather headers) you need to compile stuff with the kernel and build-essentials so that you can compile stuff.

---

