---
title: "Help uninstalling and reinstalling vmware-server"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by TooManyGames on 2007-07-03
I tried using the walk through to get my pre-existing Windows install booting under VMWare.  I got to the final step (launch VMware and load the created profile) and VMware would no longer launch for one reason or another.  So I uninstalled it (apt-get remove vmware-server).  Now I would like to try to reinstall it but it says there are still installed components and I can't reinstall until these components are gone.

I've dug through everything I can think of but I can't find what it wants me to remove.  Anyone have any suggestions on what I could do to get VMware installed again?

---

### Post by forestpixie on 2007-07-03
Try to purge it
```

sudo apt-get remove --purge vmware-server
```

---

### Post by TooManyGames on 2007-07-03
Same error when trying to install again after purging.  8*(

A previous installation of a VMware product has been detected.

If you installed it from the VMware website, please remove it by running
vmware-uninstall.pl before proceeding.

If it was installed through Ubuntu, you must purge (completely remove)
the old package.

Message in terminal is:

chuck@chuck-desktop:~$ sudo apt-get install vmware-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  vmware-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/79.4MB of archives.
After unpacking 131MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 125393 files and directories currently installed.)
Unpacking vmware-server (from .../vmware-server_1.0.3-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.3-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.3-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by forestpixie on 2007-07-03
try this in terminal and post output

dpkg -s vmware-server

---

### Post by TooManyGames on 2007-07-03
Package: vmware-server
Status: install ok config-files
Priority: optional
Section: misc
Installed-Size: 127608
Maintainer: VMware Build Team <vmware-builds@vmware.com>
Architecture: i386
Version: 1.0.3-1
Config-Version: 1.0.3-1
Depends: netbase, netkit-inetd | inetd, update-inetd, vmware-server-kernel-modules, libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libexpat1 (>= 1.95.8), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:4.0.1), libglib2.0-0 (>= 2.8.0), libgtk2.0-0 (>= 2.8.0), libice6, libjpeg62, libpango1.0-0 (>= 1.10.1), libpng12-0 (>= 1.2.8rel), librsvg2-2 (>= 2.9.5), librsvg2-common (>= 2.9.5), libsm6, libssl0.9.7, libstdc++5 (>= 1:3.3.4-1), libx11-6, libxext6, libxft2 (>> 2.1.1), libxi6, libxml2 (>= 2.6.20), libxrender1, libxt6, libxtst6, zlib1g (>= 1:1.2.1)
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Conflicts: xinetd, vmware-player, libdbus-1-2
Description: Free virtual machine server from VMware
 The free VMware Server lets you run pre-built virtual machines on
 your desktop.  You can run multiple operating systems side-by-side,
 easing the process of software development, testing, and evaluation.
 .
 Virtual machines developed in VMware Workstation or ESX Server can
 be run in VMware Server.
 .
 To run the VMware Server Console, just run /usr/bin/vmware from within X.
 .
 Note: You will also need the VMware Server kernel modules to run vmware.
 These can be built from source from vmware-server -kernel-source, or you
 can install a pre-built vmware-server-kernel-modules package for your kernel.

---

### Post by forestpixie on 2007-07-03
Try the purge commnad again and post its ouput

---

### Post by TooManyGames on 2007-07-03
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package vmware-server is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by GeeZor on 2007-07-03
```
sudo apt-get remove --purge vmware-player
```
 to resolve your conflict

---

### Post by forestpixie on 2007-07-03
We've been there Geezor :)

Ok try 

dpkg --remove --force-remove-reinstreq vmware-server

---

### Post by TooManyGames on 2007-07-03
dpkg - warning: ignoring request to remove vmware-server, only the config
 files of which are on the system.  Use --purge to remove them too.

---

### Post by forestpixie on 2007-07-03
ok tryo using dpkg to purge then - I'm into uncharted territory here and reading man page

sudo dpkg -purge vmware-server

or

sudo apt-get --purge vmware-server


(manual page is man dpkg)

---

### Post by TooManyGames on 2007-07-03
I tried this:

```
sudo dpkg --purge vmware-server
```

and got this:

(Reading database ... 125382 files and directories currently installed.)
Removing vmware-server ...
Purging configuration files for vmware-server ...
dpkg - warning: while removing vmware-server, directory `/var/lib/vmware-server/Virtual Machines' not empty so not removed.
dpkg - warning: while removing vmware-server, directory `/var/lib/vmware-server' not empty so not removed.

So I deleted the vmware directory in /var/lib/ and now it's installing.  Apparently I needed to remove the profile for the Windows XP install I did to test out VMware before it would allow me to do a fresh install.

---

### Post by forestpixie on 2007-07-03
cracking and good luck

---

### Post by Kaso_Da_Zmok on 2007-07-03
I have got into the same situation if i used the automatix to install the VMware-server...

Trie the purge etc.... not help at all....

Rather install the vmware server per hand next time w/o Automatix.


Just going to install it per hand

---

### Post by hmarkg on 2008-06-13
I am trying to install VMware-server into my ubuntu. So i follow all the instruction but this error comes out.


[COLOR="Red"]mark@Atrix:~$ cd ~/src/VMWare
mark@Atrix:~/src/VMWare$ tar xzf VMware-server-1.0.6-91891.tar.gz
mark@Atrix:~/src/VMWare$ tar xzf vmware-any-any-update116.tar.gzmark@Atrix:~/src/VMWare$ cd ~/src/VMWare/vmware-server-distrib
mark@Atrix:~/src/VMWare/vmware-server-distrib$ sudo ./vmware-install.plA previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to find the binary installation directory (answer BINDIR)
       in the installer database file "/etc/vmware/locations".

Failure

Execution aborted.

mark@Atrix:~/src/VMWare/vmware-server-distrib$ [/COLOR]

---

