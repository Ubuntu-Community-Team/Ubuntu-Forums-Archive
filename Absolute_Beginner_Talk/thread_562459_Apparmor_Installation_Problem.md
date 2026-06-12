---
title: "Apparmor Installation Problem"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by CaptainBacon on 2007-09-28
Hey, I read the other threads about this issue but they didn't help. I downloaded Apparmor but when I try to build the modules I get this-

vodka@dell:~$ sudo m-a -v -t prepare
Getting source for kernel version: 2.6.20-16-generic
Kernel headers available in /lib/modules/2.6.20-16-generic/build
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libgconf2-ruby libcairo-ruby libatk1-ruby libglib2-ruby libpcre3
  libpango1-ruby libgd2-noxpm ruby1.8 libgdk-pixbuf2-ruby librexml-ruby
  libcairo-ruby1.8 libgtk2-ruby libruby1.8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
vodka@dell:~$ sudo m-a -v -t -f build apparmor-modules
unpack 
The source tarball could not be found!
Package apparmor-modules not installed?
Running "m-a -f get apparmor-modules" may help.
"/usr/share/modass/packages/default.sh" build KVERS=2.6.20-16-generic KSRC=/lib/modules/2.6.20-16-generic/build KDREV=2.6.20-16.32 kdist_image
The source tarball could not be found!
Package apparmor-modules not installed?
Running "m-a -f get apparmor-modules" may help.
Build failed. Press Return to continue...

vodka@dell:~$ sudo m-a -f get apparmor-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apparmor-modules is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package apparmor-modules has no installation candidate

Updated infos about 1 packages
vodka@dell:~$ 

What do I do? I have no idea where to go from here. :confused:

---

### Post by CaptainBacon on 2007-09-28
Nevermind I had to install the modules but now I have a new problem

vodka@dell:~$ sudo m-a -v -t install apparmor-modules
dpkg -Ei /usr/src/apparmor-modules-2.6.20-16-generic_2.0.1+510.dfsg-0ubuntu4+2.6.20-16.32_i386.deb 
Version 2.0.1+510.dfsg-0ubuntu4+2.6.20-16.32 of apparmor-modules-2.6.20-16-generic already installed, skipping.
vodka@dell:~$ apparmor_status
apparmor module is not loaded.
vodka@dell:~$ 


It says it's already installed but at the same time not?

---

### Post by Kilz on 2007-09-28
> **CaptainBacon said:**
> Nevermind I had to install the modules but now I have a new problem

vodka@dell:~$ sudo m-a -v -t install apparmor-modules
dpkg -Ei /usr/src/apparmor-modules-2.6.20-16-generic_2.0.1+510.dfsg-0ubuntu4+2.6.20-16.32_i386.deb 
Version 2.0.1+510.dfsg-0ubuntu4+2.6.20-16.32 of apparmor-modules-2.6.20-16-generic already installed, skipping.
vodka@dell:~$ apparmor_status
apparmor module is not loaded.
vodka@dell:~$ 


It says it's already installed but at the same time not?

I think what its saying is that the files are installed, but the kernel module is not loaded.

---

### Post by CaptainBacon on 2007-09-28
How do I load the kernel module?

---

### Post by CaptainBacon on 2007-09-28
sudo m-a -v -t prepare       - works
sudo m-a -v -t -f build apparmor-modules  -works
sudo m-a -v -t install apparmor-modules   -says already installed

vodka@dell:~$ apparmor_status
apparmor module is not loaded.

What do I do??

---

### Post by CaptainBacon on 2007-09-28
vodka@dell:~$ sudo /etc/init.d/apparmor start
FATAL: Error inserting apparmor (/lib/modules/2.6.20-16-generic/apparmor/apparmor.ko): Resource temporarily unavailable
$Loading AppArmor module: Failed.
- could not start AppArmor: Failed.
return: 116: Illegal number: -1

---

### Post by PmDematagoda on 2007-09-28
To find the status of Apparmor:

```
sudo apparmor_status
```

To enable AppArmor:-

```
sudo /etc/init.d/apparmor start
sudo update-rc.d apparmor start 37 S .
```

To enforce or load all profiles:-

```
sudo aa-enforce /etc/apparmor.d/*
```

To make AppArmor report suspicious activities for you:-

```
sudo aa-complain /etc/apparmor.d/* 
```

To disable AppAmor:-

```

sudo /etc/init.d/apparmor kill
sudo update-rc.d -f apparmor remove
```


I suggest you read this:-

[https://help.ubuntu.com/community/AppArmor?highlight=%28AppArmor%29#head-b3d654aec8bd62d1c3a7fd3672bd01615a4b24f2](https://help.ubuntu.com/community/AppArmor?highlight=%28AppArmor%29#head-b3d654aec8bd62d1c3a7fd3672bd01615a4b24f2)

It was very useful for me, and solved all my problems for AppArmor, the commands for AppArmor are all here.:)

---

