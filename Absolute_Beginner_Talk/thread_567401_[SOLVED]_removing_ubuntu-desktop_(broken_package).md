---
title: "[SOLVED] removing ubuntu-desktop (broken package)"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by obscur156 on 2007-10-04
I have a broken package "gimp",if i want to remove it ,it tells me in synaptic manager that UBUNTU-DESKTOP will be removed.:-k.

When i try to update it tells me to go to the terminal and type:
sudo apt-get install -f

i did it but still giving an error message:

ob@liberty:~$ sudo apt-get install -f
[sudo] password for ob:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gimp
Suggested packages:
  gimp-help-en gimp-help libgimp-perl gimp-data-extras
Recommended packages:
  gimp-gnomevfs gimp-libcurl
The following packages will be upgraded:
  gimp
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/3902kB of archives.
After unpacking, 373kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 147058 files and directories currently installed.)
Preparing to replace gimp 2.4.0~rc3-1ubuntu4 (using .../gimp_2.4.0~rc3-1ubuntu5_i386.deb) ...
Unpacking replacement gimp ...
dpkg: error processing /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb (--unpack):
 trying to overwrite `/usr/share/doc/libgimp2.0/README', which is also in package libgimp2.0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ob@liberty:~$ 


So whats gonna hapen if i remove ubuntu-desktop or is there any other way to fix this?

Thanks,best regards.

---

### Post by por100pre1 on 2007-10-04
You can uninstall ubuntu-desktop, it is only the package listing of the default installation. 

Lets try to fix the issue you face:

```
sudo dpkg --configure -a
```

---

### Post by obscur156 on 2007-10-04
hummm still error message 

ob@liberty:~$ sudo dpkg --configure -a
[sudo] password for ob:
dpkg: dependency problems prevent configuration of gimp-python:
 gimp-python depends on gimp (= 2.4.0~rc3-1ubuntu5); however:
  Version of gimp on system is 2.4.0~rc3-1ubuntu4.
dpkg: error processing gimp-python (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gimp-python
ob@liberty:~$ 
 
:(

---

### Post by eph1973 on 2007-10-04
Try the following:

Edit:  Removed erroneous command

Should have been sudo dpkg -i --force-all /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb

---

### Post by obscur156 on 2007-10-04
error again

ob@liberty:~$ sudo dpkg -i --force-install /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb
dpkg: unknown force/refuse option `install'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
ob@liberty:~$

---

### Post by por100pre1 on 2007-10-04
```
sudo aptitude update && sudo aptitude safe-upgrade
```

It is an issue with the repos, read [this]("http://ubuntuforums.org/showthread.php?p=3474671").

---

### Post by obscur156 on 2007-10-04
thanks for that one budy :)

---

