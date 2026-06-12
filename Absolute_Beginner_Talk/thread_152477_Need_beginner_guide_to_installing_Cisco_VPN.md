---
title: "Need beginner guide to installing Cisco VPN"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by jlhughes on 2006-03-30
I've got the Cisco VPN software and I have reviewed the "How tos ..." here and elsewhere but I'm apparently just too new to all this.

The install script wants to know the linux version, and I've been able to figure out that uname -a returns Linux ubuntu 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686 GNU/Linux

The install script needs the kernel source and kernel headers. These are supposed to be in  /usr/src  but there is nothing there.

I have tried to use sudo apt-get install kernel-source-2.6.12 but I get the error message "Couldn't find package kernel-source-2.6.12"

Obviously I'm in over my head and I'm worried I'm going to mess something up. 

Any help would be greatly appreciated.

---

### Post by moffa on 2006-03-30
Try:

sudo apt-get install linux-headers-2.6.12-10

That will get your kernel headers. I've never used a VPN in linux, so sorry I can't help with that.

---

### Post by jlhughes on 2006-03-30
Same problem...

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-headers-2.6.12-10

Do I need to install a "development" package (as if I know what that is)?

---

### Post by moffa on 2006-03-30
Do you have all the other repositories enabled?

Take a look at:

[http://ubuntuforums.org/showthread.php?t=92672](http://ubuntuforums.org/showthread.php?t=92672)

If you are using a 64-bit computer follow that link

Make sure you use: "sudo apt-get update" after you change your list

---

### Post by aysiu on 2006-03-30
[QUOTE=jlhughes]Same problem...

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-headers-2.6.12-10

Do I need to install a "development" package (as if I know what that is)?[/QUOTE] It's not **kernel**-headers--it's **linux**-headers. Copy and paste these exact commands: ```
sudo apt-get update
sudo apt-get install linux-headers-2.6.12-10
```

---

### Post by jlhughes on 2006-03-30
Thanks. That worked for the headers. 

Now I need the kernel source.

I tried  

sudo apt-get install kernel-source-2.6.12-10

and I tried

sudo apt-get install linux-source-2.6.12-10

Both returned Couldn't find package ...

---

### Post by aysiu on 2006-03-30
Try typing ```
apt-cache search kernel-source
``` Or, better yet, use something like System > Administration > Synaptic Package Manager

---

### Post by jlhughes on 2006-03-30
I was able to get this command to work.

$ sudo apt-get install linux-source-2.6.12

It responded with Recommended packages:
  gcc-3.4 make 
The following NEW packages will be installed:
  binutils linux-source-2.6.12

 Now I have  /usr/src/linux-source-2.6.12.tar.bz2

Do I need untar this before the VPN script can use it?

---

### Post by jlhughes on 2006-03-30
[QUOTE=jlhughes]

 Now I have  /usr/src/linux-source-2.6.12.tar.bz2

Do I need untar this before the VPN script can use it?[/QUOTE]

OK. Figured out how to untar the file with tar -xf

The next problem was this error message during the vpn install:

Making module
./driver_build.sh: line 50: make: command not found
Failed to make module "cisco_ipsec.ko".

I used the command sudo apt-get install make

I then executed the command  sudo ./vpn_install

This is the output:

Making module
make -C /usr/src/linux SUBDIRS=/home/john/vpnclient modules
make[1]: Entering directory `/usr/src/linux-source-2.6.12'
Makefile:485: .config: No such file or directory
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found

  WARNING: Symbol version dump /usr/src/linux-source-2.6.12/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/john/vpnclient/linuxcniapi.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/john/vpnclient/linuxcniapi.o] Error 127
make[1]: *** [_module_/home/john/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

---

### Post by aysiu on 2006-03-30
```
sudo apt-get install build-essential
```

---

### Post by jlhughes on 2006-03-30
[QUOTE=aysiu]```
sudo apt-get install build-essential
```[/QUOTE]

Thanks.  It turns out all of my problems setting up the linux source and headers could have been solved with this single command:

sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4

That installed the source and headers in /lib/modules/2.6.12-10-386/build

---

