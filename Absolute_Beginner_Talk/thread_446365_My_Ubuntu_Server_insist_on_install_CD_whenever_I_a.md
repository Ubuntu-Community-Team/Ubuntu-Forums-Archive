---
title: "My Ubuntu Server insist on install CD whenever I apt-get"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Cheese Sandwich on 2007-05-16
Example:

```

elcamino: /home/myname> sudo apt-get install nfs-kernel-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libevent1 libgssapi2 libnfsidmap2 librpcsecgss3 nfs-common portmap
The following NEW packages will be installed:
  libevent1 libgssapi2 libnfsidmap2 librpcsecgss3 nfs-common nfs-kernel-server
  portmap
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/402kB of archives.
After unpacking 1323kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Media change: please insert the disc labeled
 'Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter

```

How can I avoid this?

I'm running Ubuntu Server with Xubuntu-desktop installed. FYI, I always get this at the end of every package installation:

```

Setting up acpid (1.0.4-5ubuntu6) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xubuntu-desktop:
 xubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 xubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 xubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing xubuntu-desktop (--configure):
 dependency problems - leaving unconfigured

<...other unrelated installation info....>

Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 xubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Ziox on 2007-05-16
sudo nano /etc/apt/sources.list

and then remove the lines that says cd in them...they are at the beginning of the file.

then sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by Cheese Sandwich on 2007-05-16
> **Ziox said:**
> sudo nano /etc/apt/sources.list

and then remove the lines that says cd in them...they are at the beginning of the file.

then sudo aptitude update && sudo aptitude dist-upgrade

Thanks, that solved my CD problem, though I still get the apci errors.

---

### Post by eha1990 on 2007-05-25
> **Ziox said:**
> sudo nano /etc/apt/sources.list

and then remove the lines that says cd in them...they are at the beginning of the file.

then sudo aptitude update && sudo aptitude dist-upgrade


I wanted to thank you for your post.  I was having a similar problem and I implemented your suggestion and it solved the problems I was having whenever I tried to use Automatix2.  I had to remove the line that referenced  the cd.

Thanks again.

:KS:KS:KS

---

