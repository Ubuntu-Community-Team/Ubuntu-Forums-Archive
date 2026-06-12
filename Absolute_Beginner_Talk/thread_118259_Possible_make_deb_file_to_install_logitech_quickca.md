---
title: "Possible make deb file to install logitech quickcam messenger  ?"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-01-16
Hi, 

I am so crap in linux with drivers:  I cannot manage to install this logitech quickcam messenger.
Isnt it possible to make a deb file for this installation ?
  
Just a newbie question ..; 
  
Thank you,
  
Patrick

---

### Post by patrick295767 on 2006-01-16
```
-=- Logitech QuickCam USB camera driver installer -=-
Hello! I am the (hopefully) easy-to-use, fully automated
qc-usb driver installation script.
At the moment, this is experimental, and if it doesn't work,
don't hesitate to quit this with Ctrl+C and install the
driver manually.

The driver is provided in source code form, so it has to be
compiled. This should happen automatically, but it does mean
that there are some steps required before installation.

You also need to know "root" user password to test and
install the driver.

Basically you need only to keep hitting Enter whenever you
see this prompt: --->. Sometimes you're asked root password.
Pay special attention to lines beginning with [!].
It means that some trouble has been detected.

To most important location is the path to your kernel source
or headers. This can be guessed, but you can specify it by
giving it as an argument to this script like this:
        ./quickcam.sh LINUX_DIR=/usr/src/linux

If you haven't done it yet, now it would be a good moment to
take a look at file README.

Next I'm going to check if you have some important programs installed
and if they and the kernel are of suitable version.
Press Ctrl+C to quit, Enter to continue --->

./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
Warning: gcc missing
Warning: gcc missing
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
Warning: xawtv missing
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
[!] Some important programs can not be found on default path.
Probably they aren't installed.
You should install them, for example, by using apt-get or rpm.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

/bin/readlink
gcc version:
gcc version:
Make version: GNU Make 3.80
Linker version: GNU ld version 2.16.1 Debian GNU/Linux
Kernel compiler: gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)
[!] Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
        export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

Looking for more necessary programs...
Found program /sbin/depmod
Found program /sbin/insmod
Found program /sbin/rmmod
Found program /sbin/modprobe
Found program /bin/mount
Found program /usr/sbin/lsusb
depmod version: module-init-tools 3.2-pre7
insmod version: module-init-tools version 3.2-pre7
rmmod version: module-init-tools version 3.2-pre7
modprobe version: module-init-tools version 3.2-pre7
Checking whether we're root... root
[!] Running script as root.
You shouldn't run this script as root. It should work,
but is unsafe. Please run this as an ordinary user.
When root access is really needed, you will be prompted
for the root password.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

Checking for driver source code...
Checking for write permission...

Previous round done. Now checking if you have kernel source installed.
Press Ctrl+C to quit, Enter to continue --->

Kernel source directory: /lib/modules/2.6.12-9-386/build
Detected kernel version is 2.6.x.
Kernel version name: 2.6.12-9-386
Kernel source version code: 132620
Driver file name: quickcam.ko
Module install directory: /lib/modules/2.6.12-9-386
Driver source directory (PWD):         /root/qc-usb-messenger-1.0
Kernel source directory (LINUX_DIR):   /lib/modules/2.6.12-9-386/build
Module install directory (MODULE_DIR): /lib/modules/2.6.12-9-386
Utility install directory (PREFIX):    /usr/local
User options (USER_OPT):
Driver file name (use with insmod):    quickcam.ko
Kernel version code:                   132620

The QuickCam driver requires other drivers from kernel.
I'll now check if those seem to be loaded.
Press Ctrl+C to quit, Enter to continue --->       
```

---

