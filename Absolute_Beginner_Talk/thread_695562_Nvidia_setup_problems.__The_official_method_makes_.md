---
title: "Nvidia setup problems.  The official method makes my screen go to sleep by itself."
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2008-02-13
**(Gutsy Nvidia problem, Nvidia+Automatix worked fine on Dapper and Feisty on this machine previously!)**
Asus EN6200LE  - Nvidia GeForce 6200 LE 64 MB



I followed this official method to setup Nvidia the first time but it makes my screen go to sleep whenever I press something on the menu.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-26d824c59899f7a5692f83a8ffb1100498bd1ee1](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-26d824c59899f7a5692f83a8ffb1100498bd1ee1)

Then I read about this guys Nvidia problems and it seems he tried every method out there so I choose the method that finally fixed the problem for him.  But I got stuck with that method now I need some help please?!
[http://ubuntuforums.org/showthread.php?t=613269](http://ubuntuforums.org/showthread.php?t=613269)



Is this the official Nvidia setup method?  I can't keep up anymore been using ATI for years NVIDIA is still unknown territory for me.

```

0. Download this file
http://www.nvidia.com/object/linux_display_ia32_100.14.19.html

1. sudo /etc/init.d/gdm stop
2. ps ax | grep gdm  ; kill this process

3. sudo apt-get remove nvidia-glx-new
4. sh NVIDIA-Linux-x86-100.14.19-pkg1.run

5. /etc/rc.local  ; add this
modprobe -r nvidia
```


I got stuck at step 4 it wants me to install libc development package in order to install the Kernel header something before Nvidia can work properly.  So I tried this.
```
sudo apt-get install libc
sudo apt-cache search libc 

```
No results and no luck with the libc search.  Here's the error.log file.  What now?

> **nvidia-installer log file '/var/log/nvidia-installer.log'**
creation time: Tue Feb 12 22:32:08 2008

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
[COLOR="Red"]**ERROR: You do not appear to have libc header files installed on your system. **
       Please install your distribution's libc development package.
**ERROR: Installation has failed.  Please see the file**
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
[/COLOR]

---

### Post by dca on 2008-02-13
For nVidia drivers I either use the 'Add/Remove' under the Applications menu or I install Envy...   
 
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
 
Also, in Gutsy, there's always the 'Restricted Drivers' service under the 'System -> Administration' menu provided during install the card is recognized as nvidia or Riva TNT or etc...

---

### Post by djbsteart1 on 2008-02-13
i had a similer problem, but with envy it worked fine. here is the link to the guide in the forums, the link to envy is at the bottom of the first post.

[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by jingo811 on 2008-02-13
**Envy + "dpkg-reconfigure -phigh" combination**
Envy alone didn't solve things I still had to do the "dpkg-reconfigure -phigh xserver-xorg" in order to enable my correct 1280x1024 resolution.  I'm not sure if nVIDIA got installed right by doing so it seems like it overrided the Envy configurations by doing so.  Maybe someone can explain what happens with this combination in detail?

```
sudo apt-get install -f
sudo dpkg -i envy*.deb
sudo envy -t
```

&#65279;```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure -phigh xserver-xorg
```

X hasn't crashed for some hour now so maybe it's ok......

---

### Post by takuhii on 2008-02-13
envy does all the hard work these days, even updates xorg.conf

---

### Post by jingo811 on 2008-02-13
I'm guessing that after every new kernel update then you just do these commands again to bring nVIDIA back online?
```
sudo dpkg -i envy*.deb
sudo envy -t
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by djbsteart1 on 2008-02-14
as i recall from envy that is the case, although i did read somewhere that envy updates automatically, or it may have been the other way around. well hope x stays up and good.

---

