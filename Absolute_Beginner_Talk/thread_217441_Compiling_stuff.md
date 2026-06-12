---
title: "Compiling stuff"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-07-17
What does this mean? Im trying to install a filter for gimp but have to make it first. Ive tried this kind of thing before but it never seems to work:


Where is the $path and what is the default c/c++ compiler that comes packaged with ubuntu dapperdan@linuxpc:

/tmp/gimp-texturize$ ./configure && make && sudo make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.


Linux is always telling me to check a log of some kind, but never tells me where the log is located!

](*,)

---

### Post by lixx on 2006-07-17
make sure build-essentials is installed. 
the C compiler can usually be found at /usr/bin or /usr/local/bin

as for config.log, you can find it at /var/log because this is the directory where log files are usually placed. and for checking what the default compiler is, you can type at the console: X -version

at the bottom part, you should see information similar to this:

OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005

---

### Post by mogelhead on 2006-07-17
The default compiler is gcc.

Have you installed the build-essential package? It contains gcc and g++ (GNU C++ compiler) and a few other.

Since the log file is said to be "config.log", I would guess that it is located in the present working directory - which seems to be /tmp/gimp-texturize.

$PATH is an environment variable, its current content can be displayed with the following command:
```
echo $PATH
```

---

### Post by Sef on 2006-07-17
> Have you installed the build-essential package?

To install build-essential, open the terminal (Applications > Accessories > Terminal) and type this code in

```
sudo aptitude install build-essential
```

---

### Post by dgrafix on 2006-07-17
Its saying no candidate version found:



user@linuxpc:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for build-essential
The following packages have been kept back:
  app-install-data-commercial cupsys cupsys-bsd cupsys-client gimp
  gimp-data gimp-python language-pack-en language-pack-gnome-en
  libcupsimage2 libcupsys2 libgimp2.0 libgnomecups1.0-1 libsmbclient
  libxine-main1 linux-386 linux-image-386 linux-restricted-modules-386
  linux-restricted-modules-common login nvidia-glx openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-en-us openoffice.org-math
  openoffice.org-writer passwd pmount ppp python-uno samba samba-common
  smbclient ttf-opensymbol xserver-xorg-core xserver-xorg-input-mouse
0 packages upgraded, 0 newly installed, 0 to remove and 45 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


Doesnt seem to have done anything

---

