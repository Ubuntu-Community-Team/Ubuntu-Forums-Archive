---
title: "Acronis for Linux"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-06-27
I tried to install the program but it tell I have to compile it I installed "build essential" what is the next step in order to compile it and how

---

### Post by 3rdalbum on 2007-06-27
Does it tell you how to compile it? There should be a file included with it called "INSTALL".

Usually, you use a terminal to move into the directory that contains the source code, then run:

```

./configure
make
sudo make install

```

If it complains that you are missing something, try searching through the repositories in Synaptic Package Manager to find the library - for instance, if it says that you are missing wxGTK, you'd install "libwxgtk2.6-0" and "libwxgtk2.6-0-dev".

---

### Post by jmfa59 on 2007-06-27
I couldn't figure out how to do it this the Howto file your help is appriciated
Table of content

Introduction
I. Common procedure for build and install kernel module
II. Installing on Mandrake 9.2 with kernel 2.4.X
III. Installing on Mandrake 10 with kernel 2.6.3-4mdk
IV. Installing on Mandrake 10.1 with kernel 2.6.8
V. Installing on Mandrake 8.0
VI. Installing on Debian (sarge) with kernel 2.4.25-1-386
VII. Installing on Debian (sarge) with kernel 2.6.7
VIII. Installing on Debian 3.0 Woody with kernel 2.4.18-1-686-smp
IX. Installing on SuSE 8.0 and SuSE 8.1
X. Installing on RedHat 7.3
XI. Installing on RedHat 8.0
XII. Installing on TurboLinux 8.0
XIII. Installing on Fedora Core 3
XIV. Installing on Redhat Advanced Server 4.0

Introduction
Sometimes Acronis True Image Server 8.0 for Linux setup can
not compile the necessary kernel modules or prepare required
execution environment for trueimage and trueimagecmd
utilities. Usually it prompts you about such problem and
refers you to this file.

Section I describes common "how to build and install module"
procedure. Most offten you will have to read it if you have
custom kernel or non-stantard kernel sources location.

Sections II, III and others provide necessary information
for specific distributions.

Please note that Redhat 9.0, Fedora Core 1, Fedora Core 2,
Redhat Advanced Server 3.0, SuSE 8.2, 9.0, 9.1, 9.2, 9.3,
Mandrake 10, Slackware 10, ASPLinux 9.2, ASPLinux 10, ASPLinux
Server II and Gentoo with stock kernels do not have problems with
Acronis True Image Server 8.0 for Linux and are not mentioned
below.

I. Building and installing kernel module in general case

If the setup could not compile the necessary kernel module
you  will have to do it manually. Please install kernel
sources, apropriate config file and all required for kernel
build packages (like  gcc,  glibc-devel, etc.). You will be
prompted about necessary packages while kernel sources
install.

Most often the snapapi kernel module should be built and
installed by "dkms" command. It may be done by the following
commands:
# dkms build -m <MODULE_NAME> -v <MODULE_VERSION> \
> --config <CONFIG_FILE> --arch <KERNEL_ARCH> \
> --kernelsourcedir <PATH_TO_KERNEL_SOURCES>
# dkms install -m <MODULE_NAME> -v <MODULE_VERSION> \
> --config <CONFIG_FILE> --arch <KERNEL_ARCH> \
> --kernelsourcedir <PATH_TO_KERNEL_SOURCES>

<MODULE_NAME> must be "snapapi" for 2.4.x kernels or
"snapapi26" for 2.6.x kernels.

<MODULE_VERSION> could be detected by
# ls /usr/src/snapapi-*
for 2.4.x kernels or by 
# ls /usr/src/snapapi26-*
for 2.6.x kernels.

<CONFIG_FILE> is your kernel config filename. Usually
this file may be found in /boot directory.

<KERNEL_ARCH> may be detected by
# rpm -q --queryformat "%{ARCH}\n" kernel
for RPM based distrubutions or by
# uname -m
for non-RPM based distributions.

For details please refer to dkms man page.

After succesful module build and install you may try to launch
trueimage or trueimagecmd utilities and check their functionality.
Appropriate kernel modules will be loaded automatically.

II. Installing on Mandrake 9.2 with kernel 2.4.X

1. Please install kernel sources and prepare kernel to build by:
# make -C /usr/src/linux-2.4.22-37mdk/ mrproper
# cp /boot/config-2.4.22-37mdksmp /usr/src/linux-2.4.22-37mdk/.config
# make -C /usr/src/linux-2.4.22-37mdk/ oldconfig
# make -C /usr/src/linux-2.4.22-37mdk/ dep

2. Please build and install snapapi module by the following
commands:
# dkms build -m snapapi -v 0.6.4 -k 2.4.22-37mdksmp --arch i686 \
> --config /boot/config-2.4.22-37mdksmp --kernelsourcedir \
> /usr/src/linux-2.4.22-37mdk/ --no-prepare-kernel
# dkms install -m snapapi -v 0.6.4 -k 2.4.22-37mdksmp \ 
> --arch i686

It is supposed that you have kernel 2.4.22-37mdksmp,
kernel architecture is i686 and module version is 0.6.4.

2. Activate devfs support by commands:
# mkdir /devfs
# mount -t devfs devfs /devfs

3. Make devfs support permanent by adding
"devfs /devfs devfs defaults 0 0" to your /etc/fstab file.

III. Installing on Mandrake 10 with kernel 2.6.3-4mdk

Mandrake Linux kernel 2.6.3-4 is not supported by Acronis True
Image Server 8.0 for Linux. Please upgrade kernel up to 2.6.3-7mdk
or later and repeate install.
Some Mandrake 10 kernels (i.e. 2.6.3-19mdk) have broken "build"
and "source" link in /lib/modules/... directory so dkms can not
build snapapi26 kernel module. In such a case please locate
kernel sources or includes in /usr/src directory and build
snapapi26 kernel module manually according section I.


IV. Installing on Mandrake 10.1 with kernel 2.6.8
Please install libstdc++5-3.3.4-1mdk.i586.rpm from the
first CD by:
# rpm -ihv libstdc++5-3.3.4-1mdk.i586.rpm

V. Installing on Mandrake 8.0

1. Please update stock kernel (2.4.3-20mdk) to 2.4.18-8.2mdk
or higher from Mandrake site.

2. Run trueimage-setup

VI. Installing on Debian (sarge) with kernel 2.4.25-1-386

1. Install kernel sources.

2. Build and install kernel module.
# dkms build -m snapapi -v 0.6.4 -k 2.4.25-1 \
> --config /boot/config-2.4.25-1-386 --arch i686 \
> --kernelsourcedir /usr/src/kernel-sources-2.4.25
# dkms install -m snapapi -v 0.6.4 -k 2.4.25-1 \
> --config /boot/config-2.4.25-1-386 --arch i686 \
> --kernelsourcedir /usr/src/kernel-sources-2.4.25

It is supposed that you have kernel 2.4.25-1,
kernel architecture is i686 and module version is 0.6.4.

3. Most probably raw-devices were not created during Debian 3.0
installation/configuring. Following simple script can be used
to check and create the devices if needed (root permissions
required):
#!/bin/bash
mkdir -p /dev/raw/
if [ ! -e /dev/rawctl ] ;then 
	mknod /dev/rawctl c 162 0
fi
for i in `seq 1 128`; do
	if [ ! -e /dev/raw/raw${i}  ] ;then
		mknod /dev/raw/raw${i} c 162 ${i}
	fi
done

4. Activate devfs support by commands:
# mkdir /devfs
# mount -t devfs devfs /devfs

5. Make devfs support permanent by adding
"devfs /devfs devfs defaults 0 0" to your /etc/fstab file.

VII. Installing on Debian (sarge) with kernel 2.6.7
Please build and install snapapi26 module as described in
section I. Devfs should not be mounted.

VIII. Installing on Debian 3.0 Woody with kernel 2.4.18-x

Please follow section VI (Installing on Debian (sarge) with kernel
2.4.25-1-386) and do not forget to use your kernel version instead
of 2.4.25-1-386.

IX. Installing on SuSE 8.0 and SuSE 8.1

If X Window application trueimage launch ends with 
"trueimage internal error" message please set environment variables by:
# export LC_ALL="en_US.UTF8"
# export LANG="en_US.UTF8"

If you have installation with another language please set above
variables in analogous manner.

We'd recommend to make these variables values permanent by edit
/etc/sysconfig/language configuration file.

X. Installing on RedHat 7.3
1. If X Window application trueimage launch ends with 
"trueimage internal error" message please set environment variables by:
# export LC_ALL="en_US.UTF8"
# export LANG="en_US.UTF8"

If you have installation with another languge please set above
variables in analogous manner.

We'd recommend to make these variables values permanent by edit
/etc/sysconfig/i18n configuration file.

2. On stock RedHat 7.3 kernel(2.4.18-3) trueimage or trueimagecmd do
not show any disks. It is recommended to upgrade kernel up to 2.4.20-28.7
(or higher) located on RedHat site in updates for RedHat 7.3.
If you want to keep old kernel you can remove or rename /dev/rawctl
file to restore True Image Server 8.0 for Linux functionality.

XI. Installing on RedHat 8.0
On stock RedHat 8.0 kernel(2.4.18-14) installer can't build kernel
module. It is recommended to upgrade kernel up to 2.4.20-28.8
(or higher) located on RedHat site in updates for RedHat 8.0.

If you want to keep old kernel you can follow section II ("Installing
on Mandrake 9.2 with kernel 2.4.X") subsections 1 and 2 and build kernel
module.

XII. Installing on TurboLinux 8.0
On stock TurboLinux 8.0 if trueimage-setup can't build kernel
modules please build them manually:

1. Install kernel-source-2.4.18-5.i586.rpm kernel-headers-2.4.18-5.i586.rpm
gcc-2.96-9.i586.rpm cpp-2.96-9.i586.rpm glibc-devel-2.2.5-13.i586.rpm rpms
located on CD 2 if they are have not been installed earlier.

2. Detect your kernel release by 
# uname -r

3. Build snapapi modules by
# dkms build -m snapapi -v 0.6.4 --config \
> /usr/src/linux/configs/kernel-2.4.18-5smp-i586.config
Please use correct config file according your kernel release.
In our example kernel release was 2.4.18-5smp.

If you have Acronis True Image Server 8.0 for Linux Japanese
build you should do the following steps to activate Japanese
support in X window application(trueimage):
4. Download and install TrueType Japanese fonts rpm
ttfonts-ja-1.2-8.noarch.rpm. It may be downloaded from
[http://www.rpmfind.net//linux/RPM/redhat/7.3/i386/ttfonts-ja-1.2-8.noarch.html](http://www.rpmfind.net//linux/RPM/redhat/7.3/i386/ttfonts-ja-1.2-8.noarch.html)
To install the rpm please run:
# rpm -Uhv ttfonts-ja-1.2-8.noarch.rpm --nodeps

5. To activate new fonts please add
FontPath        "/usr/share/fonts/ja/TrueType/"
record into Section "Files" of /etc/X11/XF86Config file
and restart X server.

XIII. Installing on Fedora Core 3
If installer complains that libstdc++.so.5 is required for trueimage
rpm please install compat-libstdc++-8-3.3.4.2.i386.rpm from the first
Fedora Core 3 CD by:
# rpm -ihv compat-libstdc++-8-3.3.4.2.i386.rpm

And repeate install.

XIV. Installing on Redhat Advanced Server 4.0
If installer complains that libstdc++.so.5 is required for trueimage
rpm please install compat-libstdc++-33-3.2.3-47.3.i386.rpm from the
second Redhat Advanced Server 4.0 CD by:
# rpm -ihv compat-libstdc++-33-3.2.3-47.3.i386.rpm

---

