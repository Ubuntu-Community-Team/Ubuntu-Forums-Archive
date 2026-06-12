---
title: "How to install Vmware Tools On Dapper"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by hypnoticspectar on 2006-11-24
In the vmware console click on install vmware tools.
 
A cd icon will appear on the desktop. 

Copy the file VMwareTools-1.0.1-29996.tar.gz to your home directory.

tar -xzf VMwareTools-1.0.1-29996.tar.gz 

sudo apt-get install gcc 

sudo apt-get install build-essentail

uname -r 

sudo apt-get install linux-headers-(result of the uname -r)

cd into the vmware tools dir (vmware-tools-distrib)

sudo ./vmware-install.pl

answer the defaults for all of the questions [I]

[I]In which directory do you want to install the binary files?
[/usr/bin][/I]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/usr/sbin]

In which directory do you want to install the library files?
[/usr/lib/vmware-tools]

The path "/usr/lib/vmware-tools" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the documentation files?
[/usr/share/doc/vmware-tools]

The path "/usr/share/doc/vmware-tools" does not exist currently. This program
is going to create it, including needed parent directories. Is this what you
want? [yes]

The installation of VMware Tools 1.0.1 build-29996 for Linux completed
successfully. You can decide to remove this software from your system at any
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want
this program to invoke the command for you now? [yes]


Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:                                      done
   Guest filesystem driver:                                            done
 * Deconfiguring network interfaces...                                   [ ok ]
   Guest vmxnet fast network device:                                   done
Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-26-386/build/include]

Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmhgfs-only'
make -C /lib/modules/2.6.15-26-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /tmp/vmware-config1/vmhgfs-only/cpName.o
  CC [M]  /tmp/vmware-config1/vmhgfs-only/cpNameLinux.o
  CC [M]  /tmp/vmware-config1/vmhgfs-only/dev.o
  CC [M]  /tmp/vmware-config1/vmhgfs-only/driver.o
  CC [M]  /tmp/vmware-config1/vmhgfs-only/hgfsUtil.o
  CC [M]  /tmp/vmware-config1/vmhgfs-only/main.o
  CC [M]  /tmp/vmware-config1/vmhgfs-only/staticEscape.o
  LD [M]  /tmp/vmware-config1/vmhgfs-only/vmhgfs.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config1/vmhgfs-only/vmhgfs.mod.o
  LD [M]  /tmp/vmware-config1/vmhgfs-only/vmhgfs.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
cp -f vmhgfs.ko ./../vmhgfs.o
make: Leaving directory `/tmp/vmware-config1/vmhgfs-only'
The module loads perfectly in the running kernel.

Extracting the sources of the vmxnet module.

Building the vmxnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmxnet-only'
make -C /lib/modules/2.6.15-26-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /tmp/vmware-config1/vmxnet-only/vmxnet.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config1/vmxnet-only/vmxnet.mod.o
  LD [M]  /tmp/vmware-config1/vmxnet-only/vmxnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
cp -f vmxnet.ko ./../vmxnet.o
make: Leaving directory `/tmp/vmware-config1/vmxnet-only'
The module loads perfectly in the running kernel.



Detected X.org version 7.0.


Please choose one of the following display sizes (1 - 13):

[1]  "640x480"
[2]  "800x600"
[3]  "1024x768"
[4]  "1152x864"
[5]  "1280x800"
[6]  "1152x900"
[7]  "1280x1024"
[8]  "1376x1032"
[9]  "1400x1050"
[10]  "1680x1050"
[11]  "1600x1200"
[12]  "1920x1200"
[13]  "2364x1773"
Please enter a number between 1 and 13:

[3]
Starting VMware Tools services in the virtual machine:
   Switching to guest configuration:                                   done
   Guest filesystem driver:                                            done
   Guest vmxnet fast network device:                                   done
   DMA setup:                                                          done
   Guest operating system daemon:                                      done

The configuration of VMware Tools 1.0.1 build-29996 for Linux for this running
kernel completed successfully.

You must restart your X session before any mouse or graphics changes take
effect.

You can now run VMware Tools by invoking the following command:
"/usr/bin/vmware-toolbox" during an X session.

To use the vmxnet driver, restart networking using the following commands:
/etc/init.d/networking stop
rmmod pcnet32
rmmod vmxnet
depmod -a
modprobe vmxnet
/etc/init.d/networking start

Enjoy,

--the VMware team[/I]

Then restart X

---

