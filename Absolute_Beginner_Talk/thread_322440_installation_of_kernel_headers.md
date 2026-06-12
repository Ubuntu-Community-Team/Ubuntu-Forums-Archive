---
title: "installation of kernel headers"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-12-20
guys, how do i install the kernel headers for mine? 
this is the output of "uname -r"
> 
2.6.17-10-generic


i need that because i want to install compiz on my desktop but i know i have to install the beta nvidia drivers at first.

---

### Post by Bachstelze on 2006-12-20
To instal kernel headers, one command to remember :

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by az on 2006-12-20
> **HymnToLife said:**
> To instal kernel headers, one command to remember :

```
sudo apt-get install linux-headers-$(uname -r)
```

Actually, 

sudo apt-get install linux-headers-generic (Edgy)
or

linux-headers-386 (Dapper)
will pull in the meta package and you will stay up to date with new kernels as they come in.

---

### Post by po0f on 2006-12-20
azz,

I believe on first installing linux-headers-`uname -r`, it automatically pulls in the meta-package (at least it did in my case, I did not explicitly install it).

---

### Post by mendingo84 on 2006-12-20
i don't think it installs them by default as i get this error message when trying to install nvidia beta driver 
> 
Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.17-10-generic/build'
-> Kernel output path: '/lib/modules/2.6.17-10-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
ERROR: Unable to determine the NVIDIA kernel module filename.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).



---

### Post by az on 2006-12-20
> **po0f said:**
> azz,

I believe on first installing linux-headers-`uname -r`, it automatically pulls in the meta-package (at least it did in my case, I did not explicitly install it).

No.  There is no dependency to satisfy which would bring in the linux-headers-386 metapackage that way.  You must have installed it some other way.

emma@ubuntu:~$ sudo apt-get -s install linux-headers-686
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-27 linux-headers-2.6.15-27-686
The following NEW packages will be installed
  linux-headers-2.6.15-27 linux-headers-2.6.15-27-686 linux-headers-686
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Inst linux-headers-2.6.15-27 (2.6.15-27.50 Ubuntu:6.06/dapper-security)
Inst linux-headers-2.6.15-27-686 (2.6.15-27.50 Ubuntu:6.06/dapper-security)
Inst linux-headers-686 (2.6.15.25 Ubuntu:6.06/dapper-security)
Conf linux-headers-2.6.15-27 (2.6.15-27.50 Ubuntu:6.06/dapper-security)
Conf linux-headers-2.6.15-27-686 (2.6.15-27.50 Ubuntu:6.06/dapper-security)
Conf linux-headers-686 (2.6.15.25 Ubuntu:6.06/dapper-security)
emma@ubuntu:~$ sudo apt-get -s install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-27
The following NEW packages will be installed
  linux-headers-2.6.15-27 linux-headers-2.6.15-27-686
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Inst linux-headers-2.6.15-27 (2.6.15-27.50 Ubuntu:6.06/dapper-security)
Inst linux-headers-2.6.15-27-686 (2.6.15-27.50 Ubuntu:6.06/dapper-security)
Conf linux-headers-2.6.15-27 (2.6.15-27.50 Ubuntu:6.06/dapper-security)
Conf linux-headers-2.6.15-27-686 (2.6.15-27.50 Ubuntu:6.06/dapper-security)
emma@ubuntu:~$

---

