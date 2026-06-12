---
title: "posably &quot;/etc/X11/xorg.conf&quot; problem."
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by LostMagix on 2008-02-15
I just did a reinstall of Ubuntu on my system and i seem to be having problems with my /etc/X11/xorg.conf file.

Right now i am trying to get my Randeon 9550 to work. When I open my restricted driver manager, it says my card is enabled but not in use. I click to disable it and get the following error.... 

"Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid or does not exist."

I can try a few different ways of installing my driver but i keep having problems.


This is when i try to install the driver from ATI

```
chris@LostMagix:~$ sudo apt-get install dpkg-dev debhelper libstdc++5 dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg-dev is already the newest version.
debhelper is already the newest version.
libstdc++5 is already the newest version.
dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
chris@LostMagix:~$ ./ati-driver-installer-8-02-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.YT6222
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.455.2....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package /home/chris/xorg-driver-fglrx_8.455.2-0ubuntu1_i386.deb has been successfully generated
Package /home/chris/xorg-driver-fglrx-dev_8.455.2-0ubuntu1_i386.deb has been successfully generated
Package /home/chris/fglrx-kernel-source_8.455.2-0ubuntu1_i386.deb has been successfully generated
Package /home/chris/fglrx-amdcccle_8.455.2-0ubuntu1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install.YT6222
chris@LostMagix:~$ sudo dpkg -i fglrx-kernel-source_8.455.2-0ubuntu1_i386.deb
(Reading database ... 200503 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 8.455.2-0ubuntu1 (using fglrx-kernel-source_8.455.2-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (8.455.2-0ubuntu1) ...
Adding Module to DKMS build system

Error! DKMS tree already contains: fglrx-8.455.2
You cannot add the same module/version combo more than once.
Doing initial module build

Error! This module/version has already been built on: 2.6.22-14-generic
Directory: /var/lib/dkms/fglrx/8.455.2/2.6.22-14-generic/i686
already exists.  Use the dkms remove function before trying to build again.
Installing initial module

Error! This module/version combo is already installed
for kernel: 2.6.22-14-generic (i686)
Done.

chris@LostMagix:~$ sudo dpkg -i xorg-driver-fglrx-dev_8.455.2-0ubuntu1_i386.de
dpkg: error processing xorg-driver-fglrx-dev_8.455.2-0ubuntu1_i386.de (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx-dev_8.455.2-0ubuntu1_i386.de
chris@LostMagix:~$ sudo dpkg -i xorg-driver-fglrx-dev_8.455.2-0ubuntu1_i386.deb
(Reading database ... 200503 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx-dev 8.455.2-0ubuntu1 (using xorg-driver-fglrx-dev_8.455.2-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
Setting up xorg-driver-fglrx-dev (8.455.2-0ubuntu1) ...
chris@LostMagix:~$ sudo aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
chris@LostMagix:~$ 

```

A few outputs for you all....


```
:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

```



I run ```
sudo gedit /etc/X11/xorg.conf
``` and get a blank page.

I go into /etc/X11/ and find the file which is hidden and marked "xorg.conf~"

Im not really sure what going on here....

---

### Post by stevejesus on 2008-02-15
Create an empty file called /etc/X11/xorg.conf and then SAVE it.  Then, try again.

---

### Post by LostMagix on 2008-02-15
```
:~$ sudo aticonfig --initial
Data incomplete in file /etc/X11/xorg.conf
        At least one Device section is required.
Data incomplete in file /etc/X11/xorg.conf
        At least one Screen section is required.
aticonfig: Parsing the configuration file failed.
The above error messages are reported from XFree86 and may assist you in
diagnosing the problem with your configuration input file. Try use -f option
to generate a new configuration file.

```

---

### Post by rucadulu on 2008-02-15
Hey Steve, will that allow the xorg.conf file to be rebuilt from the xorg.conf~ file the next time the xserver is restarted? If so I had no idea that this could be done.

---

### Post by MasterJS on 2008-02-15
have you rebooted your computer since? Usually Xorg.conf rebuilds itself

---

### Post by rucadulu on 2008-02-15
An alterinative method would be to rebuild the xorg.conf file by rebooting into recover mode and running: dpkg-reconfigure xserver-xorg. You may still have to do this after creating the xorg.conf file like Steve had said to do.

---

### Post by LostMagix on 2008-02-15
I tried that but i just booted into low graphics mode and got the same error
```
:~$ sudo aticonfig --initial
Data incomplete in file /etc/X11/xorg.conf
        At least one Device section is required.
Data incomplete in file /etc/X11/xorg.conf
        At least one Screen section is required.
aticonfig: Parsing the configuration file failed.
The above error messages are reported from XFree86 and may assist you in
diagnosing the problem with your configuration input file. Try use -f option
to generate a new configuration file.

```

---

### Post by LostMagix on 2008-02-15
```
dpkg-reconfigure xserver-xorg
```

This also failed....

---

### Post by LostMagix on 2008-02-15
I got it back to the problem i had before....


```
chris@LostMagix:~$ sudo apt-get install dpkg-dev debhelper libstdc++5 dkms[sudo] password for chris:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg-dev is already the newest version.
debhelper is already the newest version.
libstdc++5 is already the newest version.
dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@LostMagix:~$ ./ati-driver-installer-8-02-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.wY6077
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.455.2....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package /home/chris/xorg-driver-fglrx_8.455.2-0ubuntu1_i386.deb has been successfully generated
Package /home/chris/xorg-driver-fglrx-dev_8.455.2-0ubuntu1_i386.deb has been successfully generated
Package /home/chris/fglrx-kernel-source_8.455.2-0ubuntu1_i386.deb has been successfully generated
Package /home/chris/fglrx-amdcccle_8.455.2-0ubuntu1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install.wY6077
chris@LostMagix:~$ sudo dpkg -i fglrx-kernel-source_8.455.2-0ubuntu1_i386.deb(Reading database ... 200503 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 8.455.2-0ubuntu1 (using fglrx-kernel-source_8.455.2-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (8.455.2-0ubuntu1) ...
Adding Module to DKMS build system

Error! DKMS tree already contains: fglrx-8.455.2
You cannot add the same module/version combo more than once.
Doing initial module build

Error! This module/version has already been built on: 2.6.22-14-generic
Directory: /var/lib/dkms/fglrx/8.455.2/2.6.22-14-generic/i686
already exists.  Use the dkms remove function before trying to build again.
Installing initial module

Error! This module/version combo is already installed
for kernel: 2.6.22-14-generic (i686)
Done.

chris@LostMagix:~$ sudo dpkg -i xorg-driver-fglrx-dev_8.455.2-0ubuntu1_i386.deb(Reading database ... 200503 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx-dev 8.455.2-0ubuntu1 (using xorg-driver-fglrx-dev_8.455.2-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
Setting up xorg-driver-fglrx-dev (8.455.2-0ubuntu1) ...
chris@LostMagix:~$ sudo aticonfig --initialUninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfd099eb ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d3592b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cde050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:01 3819259    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:01 3819259    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7cba000-b7cbb000 rw-p b7cba000 00:00 0 
b7cbb000-b7cbd000 r-xp 00000000 08:01 1163316    /lib/tls/i686/cmov/libdl-2.6.1.so
b7cbd000-b7cbf000 rw-p 00001000 08:01 1163316    /lib/tls/i686/cmov/libdl-2.6.1.so
b7cbf000-b7cc0000 rw-p b7cbf000 00:00 0 
b7cc0000-b7cc4000 r-xp 00000000 08:01 3819092    /usr/lib/libXdmcp.so.6.0.0
b7cc4000-b7cc5000 rw-p 00003000 08:01 3819092    /usr/lib/libXdmcp.so.6.0.0
b7cc5000-b7cc7000 r-xp 00000000 08:01 3819081    /usr/lib/libXau.so.6.0.0
b7cc7000-b7cc8000 rw-p 00001000 08:01 3819081    /usr/lib/libXau.so.6.0.0
b7cc8000-b7e0c000 r-xp 00000000 08:01 1163291    /lib/tls/i686/cmov/libc-2.6.1.so
b7e0c000-b7e0d000 r--p 00143000 08:01 1163291    /lib/tls/i686/cmov/libc-2.6.1.so
b7e0d000-b7e0f000 rw-p 00144000 08:01 1163291    /lib/tls/i686/cmov/libc-2.6.1.so
b7e0f000-b7e12000 rw-p b7e0f000 00:00 0 
b7e12000-b7e35000 r-xp 00000000 08:01 1163323    /lib/tls/i686/cmov/libm-2.6.1.so
b7e35000-b7e37000 rw-p 00023000 08:01 1163323    /lib/tls/i686/cmov/libm-2.6.1.so
b7e37000-b7f24000 r-xp 00000000 08:01 3819075    /usr/lib/libX11.so.6.2.0
b7f24000-b7f28000 rw-p 000ed000 08:01 3819075    /usr/lib/libX11.so.6.2.0
b7f28000-b7f35000 r-xp 00000000 08:01 3819096    /usr/lib/libXext.so.6.4.0
b7f35000-b7f36000 rw-p 0000d000 08:01 3819096    /usr/lib/libXext.so.6.4.0
b7f36000-b7f37000 rw-p b7f36000 00:00 0 
b7f37000-b7f3e000 r-xp 00000000 08:01 3819118    /usr/lib/libXrender.so.1.3.0
b7f3e000-b7f3f000 rw-p 00006000 08:01 3819118    /usr/lib/libXrender.so.1.3.0
b7f3f000-b7f44000 r-xp 00000000 08:01 3819116    /usr/lib/libXrandr.so.2.1.0
b7f44000-b7f45000 rw-p 00005000 08:01 3819116    /usr/lib/libXrandr.so.2.1.0
b7f4f000-b7f59000 r-xp 00000000 08:01 1163331    /lib/libgcc_s.so.1
b7f59000-b7f5a000 rw-p 0000a000 08:01 1163331    /lib/libgcc_s.so.1
b7f5a000-b7f5d000 rw-p b7f5a000 00:00 0 
b7f5d000-b7f77000 r-xp 00000000 08:01 1163277    /lib/ld-2.6.1.so
b7f77000-b7f79000 rw-p 00019000 08:01 1163277    /lib/ld-2.6.1.so
bfcf5000-bfd0b000 rw-p bfcf5000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

"Aborted (core dumped)"

Well theres your problem....

---

### Post by LostMagix on 2008-02-15
*bump

---

### Post by LostMagix on 2008-02-15
*bump

---

### Post by LostMagix on 2008-02-15
Last bump.

---

### Post by dstew on 2008-02-15
It seems to me you are making it hard on yourself by using source code. It might be better to use the binary packages. I think you only need to do two things: Install the fglrx driver package, and then run aticonfig --initial. These are the commands:```
sudo apt-get update 
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
```You might also try```
sudo aticonfig -f --initial
```which re-creates an xorg.conf that is to the driver's liking.

---

### Post by LostMagix on 2008-02-16
I get this....


```
:~$ sudo aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
:~$ sudo aticonfig -f --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
:~$ 

```

---

### Post by nittanylion on 2008-02-16
I see you're trying to install the latest fglrx drivers. Did you, by any chance, blacklist the repo fglrx driver? If that's the case, I don't think "sudo apt-get install xorg-driver-fglrx" will work correctly. 

If I were in your shoes, I would try to get a working xorg.conf setup first. Get rid of the new drivers and undo any changes you made in the installation attempts. Install the fglrx driver from the repo, which (unless it's been changed) should be ~version 8.37. Installing an updated fglrx driver shouldn't make any changes to the xorg.conf file other than the associating the device section, unless you force it. I never use aticonfig --initial -f just because it screws up the other sections of xorg.conf. Once everything is booting correctly, only then would I try to update fglrx.

I don't know your level of expertise, but [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually") is a great guide.

It might help to see if there are any errors in Xorg.0.log:
Errors: ```
less /var/log/Xorg.0.log |grep EE
```
Warnings: ```
less /var/log/Xorg.0.log |grep WW
```

---

### Post by LostMagix on 2008-02-16
```
:~$ less /var/log/Xorg.0.log |grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Unable to locate/open config file
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "ati" (module does not exist, 0)
(EE) open /dev/fb0: No such file or directory
(EE) AIGLX: Screen 0 is not DRI capable
:~$ less /var/log/Xorg.0.log |grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The core pointer device wasn't specified explicitly in the layout.
(WW) The core keyboard device wasn't specified explicitly in the layout.
(WW) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Warning, couldn't open module type1
(WW) Warning, couldn't open module ati
(WW) VESA(0): Unable to estimate virtual size
(WW) <default pointer>: No Device specified, looking for one...
:~$ 

```

---

### Post by LostMagix on 2008-02-16
I also tried that guide a few times.

---

### Post by LostMagix on 2008-02-16
At this point im sure it has to do with my xorg.conf file, but i dont know what could be the matter with it.....

---

### Post by LostMagix on 2008-02-16
I got some new, not sure what it all means though.....


```
chris@LostMagix:~$ less /var/log/Xorg.0.log |grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
chris@LostMagix:~$ less /var/log/Xorg.0.log |grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72

```

---

### Post by LostMagix on 2008-02-16
*bump

---

### Post by LostMagix on 2008-02-16
*bump

---

### Post by LostMagix on 2008-02-16
*bump

---

### Post by LostMagix on 2008-02-17
I have one day to get this done before i no longer have accuse to the internet.

I would really like to figure it out.

---

### Post by LostMagix on 2008-02-17
*bump

---

### Post by fmartinez on 2008-02-17
Have you had Ubuntu working on this machine before.... if so why dont you just re-install... to see if that helps? 
I know it stinks.... but it's just a suggestion.

---

### Post by LostMagix on 2008-02-17
I have had it working, i had it working for a long time.

It got to messed up to work with so i had to do a reinstall on it. I have until the 19 to get everything working. I will be without internet at that point.

I still have 30 GBs to download, i dont have the time for a reinstall.

---

### Post by LostMagix on 2008-02-17
Im really starting to freakout here, i dont even know what the problem is yet!!!

---

### Post by nittanylion on 2008-02-17
Your last output with no errors and the AIGLX warnings is precisely what I have when everything is running as it should. This line:
```
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found

```

shows that the fglrx driver is loaded, and the AIGLX warnings show that you've successfully installed the newer fglrx drivers (the fglrx driver from the repository doesn't support AIGLX). Are you absolutely sure you don't have: /etc/X11/xorg.conf ? What happens if you try to boot ubuntu normally? 

If it still says that it can't find /etc/X11/xorg.conf, could you post the output of ```
ls /etc/X11/
``` You could also try to let the fglrx driver to auto configure xorg.conf again by using ```
aticonfig --initial
``` again (you might need to use sudo, I forget at the moment) It has to be a good sign that you went from having a failure to load config file error to no errors.

---

### Post by LostMagix on 2008-02-17
```
chris@LostMagix:~$ ls /etc/X11/
app-defaults             rgb.txt     xorg.conf.failsafe      Xsession.d
cursors                  X           xorg.conf.failsafe.bak  Xsession.options
default-display-manager  xinit       xorg.conf.original-0    XvMCConfig
fonts                    xkb         Xresources              Xwrapper.config
ja_JP.eucJP              xorg.conf   xserver
ko_KR.eucKR              xorg.conf~  Xsession

```



I think i fixed it, but i dont want to call it until i get compiz working as it should

---

