---
title: "I need advice how to install tar.gz file via gnome terminal"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by RoBo5050 on 2008-02-15
Hello forum members,
 
  I was wondering if it is possible to install a tar.gz file via gnome terminal without
extracting it first??
If not,what commands would one use to safely install this file as well as creating a roll-back point if necessary,and if the tar file needs to be extracted first,what would the commands be to install the extracted source files???:confused:

Thanks in advance for a reply to this absolute beginner at Linux,Ubuntu!!

---

### Post by spiderbatdad on 2008-02-15
extracting it to your desktop by right clicking on it is fine. Then you can click on the new folder and look for a readme file or install file. Often they contain helpful information. Generally, once the file is extracted you open a terminal Applications>>Accessories>>Terminal. In the terminal, you change directory to where the file is located. In this case the desktop. In Linux the desktop directory begins with a  capital "D". So now your terminal is open you type one command at a time, and press enter after each command.```
cd Desktop/filename
``` where filename is the name of the folder that extracting the package produced. Next: ```
./configure
make
sudo make install
```

You may get errors saying some dependencies are unmet. You will need to note what is missing, and try to get the relevant dependencies. 

Before trying to compile packages, Linux requires some tools. The build-essential package in synaptic package manager is vital. So before doing anything else: ```
sudo apt-get install build-essential
```

Compiling can be tricky. It is always best to look for what you want in synaptic first, if it isn't there, look for a .deb version of the package. These can be installed with a simple click, and will usually provide all necessary dependencies. After you have installed the package, you can trash the package and the folder.

Extracting the package does not make any changes to your system. In fact nothing changes until you have successfully installed the package. To remove an installed program, you can use: ```
sudo dpkg -r program_name
```
If you want to remove a program you installed via apt-get or synaptic, you can use: ```
sudo apt-get remove --purge program_name
```

I will now go back and edit all my typos.:)

---

### Post by kpkeerthi on 2008-02-15
You may use **checkinstall** instead of **make install** so it is easier to remove later if you want to.
See [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by PeterJS on 2008-02-15
Come on man I'm beggining, **PLEASE** I don't know how much more emphatic I can be on this point. Read the documentation, linux is not windows, things aren't that difficult, they're just different. Eventually you're going to have to understand why you're doing things, or you're going to comeback here everytime you try to do something, folks here will be glad to help, but you've got better things to do with your time, and they could be helping people more willing to learn for themselves.

This covers everything you'd want to know about installing anything in any format.
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

If you're looking to have a set up from a tar ball that will cleanly uninstall you want to use checkinstall.

---

### Post by RoBo5050 on 2008-02-15
Hello forum members,
   I finally used "aptitude install checkinstal"l to install the missing command from my Ubuntu 7.1 installation,but as of yet have not used it to install the ATI Linux drivers.

I did try sh ,sudo apt-get, then ./configure and got this result:

rom@rom-desktop:~$ cd ~/Desktop
rom@rom-desktop:~/Desktop$ sh xf86-video-ati-6.6.3
rom@rom-desktop:~/Desktop$ sudo apt-get install xf86-video-ati.6.6.3
Reading package lists... Done
Building dependency tree       Reading state information... Done
E: Couldn't find package xf86-video-ati.6.6.3
rom@rom-desktop:~/Desktop$ cd xf86-video-ati-6.6.3
rom@rom-desktop:~/Desktop/xf86-video-ati-6.6.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if XINERAMA is defined... no
checking if RANDR is defined... no
checking if RENDER is defined... no
checking if XV is defined... no
checking if XF86MISC is defined... no
checking if DPMSExtension is defined... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... configure: error: Package requirements (xorg-server xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

So it looks like the missing piece to the Linux driver puzzle is the x.org files-v6.8 or newer?? If this is the case,I have downloaded these files(there were 7 tar.gz files in that version) so how would I go about installing the X.Org files to successfully install the ATI LInux driver package???

P.S.I had Synaptic download the X.Org files for the ATI driver,but since there was no makefile found after getting the error message from typing the command make,I would like another solution that doesn't require an IT!!

---

### Post by kpkeerthi on 2008-02-15
> checking for XORG... configure: error: Package requirements (xorg-server xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found


You need the **dev** packages installed from synaptic. **xproto-dev**, for example.

---

### Post by RoBo5050 on 2008-02-15
hello forum members,

   I used Synaptic Package Manager to install a few _DEV -packages today,but could not locate the x,proto(??) file package; hopefully it will not be an essential one for installing the ATI Linux distribution package downloaded from the ATI website yesterday!!

---

### Post by kpkeerthi on 2008-02-15
It probably is [this]("http://packages.ubuntu.com/gutsy/x11/x11proto-core-dev")

---

### Post by RoBo5050 on 2008-02-15
Hello forum members,
  
   I found and installed the missing X11proto files from the link posted,but after using the ,/configure command I still come up with missing X.ORG files;the problem I am having is that I need to know how to get Ubunutu to recognize the missing files and possibly integrate them into the ATI source files!?

I need to know what commands are necessary to get gnome terminal to create a makefile so I can use make install or Checkinstall (preferably) to install the needed ATI Radeon driver files!!

Thanks in advance for any links,forum help that comes in the next reply!!

P.S.I know windows X P has a way of integrating certain add ons and required files into the windows folder,but since I am a newbie to Linux in general,and 
Ubuntu specifically,I hope there is a way to integrate the needed files to install the video drivers.

---

### Post by oldos2er on 2008-02-15
Like [kpkeerthi]("http://ubuntuforums.org/member.php?u=123376") said, you need the dev packages to satisfy the "not found" dependencies. Search in Synaptic Package Manager for "xorg dev, " for example.

---

### Post by RoBo5050 on 2008-02-15
Hello forum members,
  
  I found an article on the ubuntuguide.org site that solved my
problem about unable to install ati drivers via gnome terminal;
the following is the steps,method I used to install the video drivers:
 ATI users and Compiz

Some ATI cards don't need their proprietary drivers to work with Compiz as the open-sourced driver (radeon) also has support for 3D acceleration. However, the open-sourced driver isn't as fast as the closed-sourced (fglrx) one, so if you need the proprietary one you'll have to tinker around in the terminal a little.


1. After you've installed the driver, either through the proprietary manager or directly from ATI's site, you'll have to setup the Xorg configuration file to work with your new driver. Always remember to back up the original file before altering, in case something goes wrong. 1.Open up a terminal and enter:

 ```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
  sudo aticonfig --initial --input=/etc/X11/xorg.conf
```


This will disable the default radeon driver and replace it with ATI's own. 

2.Run this command to edit the Compiz startup-script:
 ```
  gksudo gedit /usr/bin/compiz
```

Search for Driver whitelist and add fglrx to the end of the line, like this:

 # Driver whitelist
 WHITELIST="nvidia intel ati radeon i810 fglrx"

3. Reboot your computer, login and enable Compiz as mentioned above et voilà! Behold Compiz and ATI hugging.

This is edited text of what I used to reinstall/re-enable my ATI driver in
Ubuntu 7.10;the result was that I now have a high resolution capable video card that may be better in performance than some PCI-e cards!!

Now if I only could find the gnome-magnifier?!:)

---

### Post by spiderbatdad on 2008-02-15
A nice tutorial. It should be noted that the command aticonfig is part of the xorg-driver-fglrx package. If that  package is not installed.   sudo aticonfig --initial --input=/etc/X11/xorg.conf  will return:" bash: command aticonfig not found."

---

