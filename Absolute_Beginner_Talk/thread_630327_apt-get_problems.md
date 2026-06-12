---
title: "apt-get problems"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by simon303 on 2007-12-03
i decided to try the realtime kernel and KDE recently, the kernel didn't work and I preferred GNOME.
but whenever i try to run apt-get now i get a dpkg error (code 1) and trying
```
simon@simon-desktop:~$ sudo apt-get remove linux-ubuntu-modules-2.6.22-14-rt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-ubuntu-modules-2.6.22-14-rt
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 11.4MB disk space will be freed.
Do you want to continue [Y/n]? y    
(Reading database ... 137598 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-rt ...
FATAL: Could not open '/boot/System.map-2.6.22-14-rt': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
dpkg: error processing linux-ubuntu-modules-2.6.22-14-rt (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
doesn't work, now not even update manager will work
any ideas??

---

### Post by PmDematagoda on 2007-12-03
Try this:-

```
sudo apt-get remove linux-rt
```

---

### Post by simon303 on 2007-12-03
i get
```
simon@simon-desktop:~$ sudo apt-get remove linux-rt
[sudo] password for simon:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-rt is not installed, so not removed
The following packages will be REMOVED
  linux-ubuntu-modules-2.6.22-14-rt
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 11.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 137598 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-rt ...
FATAL: Could not open '/boot/System.map-2.6.22-14-rt': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
dpkg: error processing linux-ubuntu-modules-2.6.22-14-rt (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by PmDematagoda on 2007-12-03
Try installing the real time kernel using:-

```
sudo apt-get install linux-rt
```

and remove it using the command I gave earlier.

---

### Post by simon303 on 2007-12-03
i again get a load of errors
```

simon@simon-desktop:~$ sudo apt-get install linux-rt
[sudo] password for simon:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-2.6.22-14-rt linux-image-rt
  linux-restricted-modules-2.6.22-14-rt linux-restricted-modules-rt
Suggested packages:
  linux-doc-2.6.22 linux-source-2.6.22 nvidia-glx nvidia-glx-legacy
  nvidia-glx-new avm-fritz-firmware-2.6.22-14
The following NEW packages will be installed
  linux-image-2.6.22-14-rt linux-image-rt
  linux-restricted-modules-2.6.22-14-rt linux-restricted-modules-rt linux-rt
0 upgraded, 5 newly installed, 0 to remove and 4 not upgraded.
4 not fully installed or removed.
Need to get 34.4MB of archives.
After unpacking 124MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com gutsy/universe linux-image-2.6.22-14-rt 2.6.22-14.46 [17.6MB]
Get: 2 http://gb.archive.ubuntu.com gutsy/universe linux-ubuntu-modules-2.6.22-14-rt 2.6.22-14.37 [3034kB]
Get: 3 http://gb.archive.ubuntu.com gutsy/universe linux-image-rt 2.6.22.14.21 [25.4kB]
Get: 4 http://gb.archive.ubuntu.com gutsy-updates/multiverse linux-restricted-modules-2.6.22-14-rt 2.6.22.4-14.10 [13.7MB]
Get: 5 http://gb.archive.ubuntu.com gutsy/multiverse linux-restricted-modules-rt 2.6.22.14.21 [25.4kB]
Get: 6 http://gb.archive.ubuntu.com gutsy/multiverse linux-rt 2.6.22.14.21 [25.4kB]
Fetched 34.4MB in 40s (853kB/s)                                                
Selecting previously deselected package linux-image-2.6.22-14-rt.
(Reading database ... 137599 files and directories currently installed.)
Unpacking linux-image-2.6.22-14-rt (from .../linux-image-2.6.22-14-rt_2.6.22-14.46_amd64.deb) ...
Done.
Selecting previously deselected package linux-ubuntu-modules-2.6.22-14-rt.
Preparing to replace linux-ubuntu-modules-2.6.22-14-rt 2.6.22-14.37 (using .../linux-ubuntu-modules-2.6.22-14-rt_2.6.22-14.37_amd64.deb) ...
Unpacking replacement linux-ubuntu-modules-2.6.22-14-rt ...
Selecting previously deselected package linux-image-rt.
Unpacking linux-image-rt (from .../linux-image-rt_2.6.22.14.21_amd64.deb) ...
Selecting previously deselected package linux-restricted-modules-2.6.22-14-rt.
Unpacking linux-restricted-modules-2.6.22-14-rt (from .../linux-restricted-modules-2.6.22-14-rt_2.6.22.4-14.10_amd64.deb) ...
Selecting previously deselected package linux-restricted-modules-rt.
Unpacking linux-restricted-modules-rt (from .../linux-restricted-modules-rt_2.6.22.14.21_amd64.deb) ...
Selecting previously deselected package linux-rt.
Unpacking linux-rt (from .../linux-rt_2.6.22.14.21_amd64.deb) ...
Setting up linux-image-2.6.22-14-rt (2.6.22-14.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-rt (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-rt:
 linux-ubuntu-modules-2.6.22-14-rt depends on linux-image-2.6.22-14-rt; however:
  Package linux-image-2.6.22-14-rt is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-14-rt (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-fonts-recommended (2007-10) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-fonts-recommended (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of kdvi:
 kdvi depends on texlive-fonts-recommended; however:
  Package texlive-fonts-recommended is not configured yet.
dpkg: error processing kdvi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdegraphics:
 kdegraphics depends on kdvi (>= 4:3.5.8-0ubuntu1); however:
  Package kdvi is not configured yet.
dpkg: error processing kdegraphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-rt:
 linux-image-rt depends on linux-image-2.6.22-14-rt; however:
  Package linux-image-2.6.22-14-rt is not configured yet.
 linux-image-rt depends on linux-ubuntu-modules-2.6.22-14-rt; however:
  Package linux-ubuntu-modules-2.6.22-14-rt is not configured yet.
dpkg: error processing linux-image-rtE: Sub-process /usr/bin/dpkg returned an error code (1)
simon@simon-desktop:~$ sudo apt-get remove linux-rt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-rt
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 53.2kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140093 files and directories currently installed.)
Removing linux-rt ...
Setting up linux-image-2.6.22-14-rt (2.6.22-14.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-rt (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-rt:
 linux-ubuntu-modules-2.6.22-14-rt depends on linux-image-2.6.22-14-rt; however:
  Package linux-image-2.6.22-14-rt is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-14-rt (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-fonts-recommended (2007-10) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-fonts-recommended (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of kdvi:
 kdvi depends on texlive-fonts-recommended; however:
  Package texlive-fonts-recommended is not configured yet.
dpkg: error processing kdvi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdegraphics:
 kdegraphics depends on kdvi (>= 4:3.5.8-0ubuntu1); however:
  Package kdvi is not configured yet.
dpkg: error processing kdegraphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-rt:
 linux-image-rt depends on linux-image-2.6.22-14-rt; however:
  Package linux-image-2.6.22-14-rt is not configured yet.
 linux-image-rt depends on linux-ubuntu-modules-2.6.22-14-rt; however:
  Package linux-ubuntu-modules-2.6.22-14-rt is not configured yet.
dpkg: error processing linux-image-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-14-rt:
 linux-restricted-modules-2.6.22-14-rt depends on linux-image-2.6.22-14-rt; however:
  Package linux-image-2.6.22-14-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.22-14-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-rt:
 linux-restricted-modules-rt depends on linux-restricted-modules-2.6.22-14-rt; however:
  Package linux-restricted-modules-2.6.22-14-rt is not configured yet.
dpkg: error processing linux-restricted-modules-rt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-rt
 linux-ubuntu-modules-2.6.22-14-rt
 texlive-fonts-recommended
 kdvi
 kdegraphics
 linux-image-rt
 linux-restricted-modules-2.6.22-14-rt
 linux-restricted-modules-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ajopaul on 2007-12-03
just check if this helps [http://ohioloco.ubuntuforums.org/showthread.php?p=3808324](http://ohioloco.ubuntuforums.org/showthread.php?p=3808324)

---

