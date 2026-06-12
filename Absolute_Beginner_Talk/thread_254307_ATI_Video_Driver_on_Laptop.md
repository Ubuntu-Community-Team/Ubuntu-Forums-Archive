---
title: "ATI Video Driver on Laptop"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by awseft on 2006-09-09
Ok I've read a lot of help pages. I've downloaded the ATI Driver from ATI's site. 
Run: sudo sh ./ati-driver-installer-8.28.8.run
"Install Driver 8.28.8 on X.Org 7.0.x"
"I agree"
"automatic"
Then it says backup your xorg.conf file (Done)
Then run aticonfig (or aticonfig --initial)
And I get this: 
"
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
"
So I look in the log and see:
"
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.
"

What do I do? This has worked for me before, what changed?

---

### Post by awseft on 2006-09-09
Anyone need any more info to help me?

---

### Post by awseft on 2006-09-09
This must be a big thing if no one is answering. :frown:

---

### Post by jordanmthomas on 2006-09-09
I'm not sure of the problem, but don't worry.  It doesn't look like too big of a deal.
Have you installed your kernel-headers?

---

### Post by awseft on 2006-09-09
Just saw that somewhere. Installed restarting. I'll let you know.

---

### Post by awseft on 2006-09-09
I get this now:

"

make.sh: line 39: gcc: command not found
make.sh: line 45: [: !=: unary operator expected
You must be logged in as root to run this script.
awseft@awseft:/lib/modules/fglrx/build_mod$ sode sh make.sh
bash: sode: command not found
awseft@awseft:/lib/modules/fglrx/build_mod$ sudo sh make.sh
Password:
make.sh: line 39: gcc: command not found
make.sh: line 45: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
doing Makefile based build for kernel 2.6.x and higher
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
ln: creating symbolic link `./libfglrx_ip.a.GCC' to `../libfglrx_ip.a.GCC': File exists
make: *** [libfglrx_ip.a.GCC] Error 1
build failed with return value 2
"

---

### Post by jordanmthomas on 2006-09-09
```
sudo apt-get install build-essential
```
Then try again

---

### Post by awseft on 2006-09-09
Ok that seemed to work fine. Went throught the rest of what I was told. Restarted and nothing :(

Here's what I did:
su
apt-get install alien
alien -d fglrx_4_3_0-8.16.20-1.i386.rpm
dpkg -i fglrx_4_3_0-8.16.20-1.i386.deb
cd /lib/modules/fglrx/build_mod
sh make.sh
cd ..
sh make_install.sh

---

### Post by awseft on 2006-09-09
Restarted the process. This is what I got.
When I try to dpkg I get this:


awseft@awseft:~/Desktop$ sudo dpkg -i fglrx-4-3-0_8.16.20-2_i386.deb
(Reading database ... 93385 files and directories currently installed.)
Unpacking fglrx-4-3-0 (from fglrx-4-3-0_8.16.20-2_i386.deb) ...
dpkg: error processing fglrx-4-3-0_8.16.20-2_i386.deb (--install):
 trying to overwrite `/usr/share/icons/ati.xpm', which is also in package fglrx-control
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 fglrx-4-3-0_8.16.20-2_i386.deb
awseft@awseft:~/Desktop$

---

### Post by awseft on 2006-09-09
Help :(

---

### Post by awseft on 2006-09-09
Restarted and nothing

Here's what I did:
su
apt-get install alien
alien -d fglrx_4_3_0-8.16.20-1.i386.rpm
dpkg -i fglrx_4_3_0-8.16.20-1.i386.deb
cd /lib/modules/fglrx/build_mod
sh make.sh
cd ..
sh make_install.sh

When I try to dpkg I get this:
awseft@awseft:~/Desktop$ sudo dpkg -i fglrx-4-3-0_8.16.20-2_i386.deb
(Reading database ... 93385 files and directories currently installed.)
Unpacking fglrx-4-3-0 (from fglrx-4-3-0_8.16.20-2_i386.deb) ...
dpkg: error processing fglrx-4-3-0_8.16.20-2_i386.deb (--install):
trying to overwrite `/usr/share/icons/ati.xpm', which is also in package fglrx-control
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
fglrx-4-3-0_8.16.20-2_i386.deb
awseft@awseft:~/Desktop$

But my xorg.conf does say:
Section "Device"
Identifier "ATI Technologies, Inc. ATI Default Card"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

But the resolution is off and the ATI controller says:

Driver does not provide the FireGL X11 extenstions!
Panel components will operate only partially.

---

### Post by jordanmthomas on 2006-09-09
sudo apt-get remove flgrx-control
sudo dpkg -i fglrx-4-3-0_8.16.20-2_i386.deb
sudo apt-get install fglrx-control

Maybe?

---

### Post by awseft on 2006-09-09
awseft@awseft:~/Desktop$ sudo apt-get remove flgrx-control
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flgrx-control
awseft@awseft:~/Desktop$

awseft@awseft:~/Desktop$ sudo dpkg -i fglrx-4-3-0_8.16.20-2_i386.deb
(Reading database ... 108306 files and directories currently installed.)
Preparing to replace fglrx-4-3-0 8.16.20-2 (using fglrx-4-3-0_8.16.20-2_i386.deb) ...
Unpacking replacement fglrx-4-3-0 ...
/var/lib/dpkg/info/fglrx-4-3-0.postrm: line 64: [: upgrade: integer expression expected
Setting up fglrx-4-3-0 (8.16.20-2) ...

awseft@awseft:~/Desktop$

awseft@awseft:~/Desktop$ sudo apt-get install fglrx-control
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  fglrx-control
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/73.0kB of archives.
After unpacking 348kB of additional disk space will be used.
(Reading database ... 108306 files and directories currently installed.)
Unpacking fglrx-control (from .../fglrx-control_8.25.18+2.6.15.11-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/fglrx-control_8.25.18+2.6.15.11-3_i386.deb (--unpack):
 trying to overwrite `/usr/share/icons/ati.xpm', which is also in package fglrx-4-3-0
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx-control_8.25.18+2.6.15.11-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
awseft@awseft:~/Desktop$

---

### Post by powder on 2006-09-09
I think your best bet here is to undo whatever it is that you've done already and follow the guide at the ati driver wiki:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Use Method 2 on that page to compile the fglrx driver from ati's website.

---

### Post by awseft on 2006-09-09
Something wrong with getting the Module Assistant

---

### Post by powder on 2006-09-10
Have you enabled "universe" and "multiverse" in your sources.list?

---

### Post by awseft on 2006-09-10
I'm not sure where that is. I went ahead and ran 

sudo aticonfig --force --initial

and it worked. I'm wondering why I cannot open ATI Control in the tasjk bar now. It just doesn't open but I can't delete it (or don't know how).

---

### Post by powder on 2006-09-10
You installed the driver in some kind of unorthodox method here so it's going to be next to impossible to troubleshoot your situation.

---

### Post by awseft on 2006-09-10
Darn. 
Thanks for the help! I'm glad I got it working but I wish I knew how in case I have to do it again. The first time I did it I didn't have ANY problems.

---

