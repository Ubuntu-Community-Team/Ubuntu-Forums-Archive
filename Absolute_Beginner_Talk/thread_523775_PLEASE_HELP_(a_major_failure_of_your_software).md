---
title: "PLEASE HELP (a major failure of your software)"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by truet on 2007-08-12
**So during update, an error came up saying it didnt complete, 2 broken packages. When i went to add/remove progs the following error shows**

[I]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/I]

**Heres what i tried via terminal, and the error message, infact the whole log.**

[I]jonathan@Lalita:~$ sudo apt-get update
Password:
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB [4827B]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB [1573B]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 6403B in 0s (16.1kB/s)
Reading package lists... Done
jonathan@Lalita:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  linux-headers-2.6.20-16 openoffice.org-common
Recommended packages:
  openoffice.org-style-industrial openoffice.org-style-tango
  openoffice.org-style-crystal openoffice.org-style-andromeda
  openoffice.org-style-hicontrast
The following NEW packages will be installed
  linux-headers-2.6.20-16
The following packages will be upgraded:
  openoffice.org-common
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/20.1MB of archives.
After unpacking 58.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 102754 files and directories currently installed.)
Unpacking linux-headers-2.6.20-16 (from .../linux-headers-2.6.20-16_2.6.20-16.29_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.20-16_2.6.20-16.29_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace openoffice.org-common 2.2.0-1ubuntu3 (using .../openoffice.org-common_2.2.0-1ubuntu4_all.deb) ...
Unpacking replacement openoffice.org-common ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.20-16_2.6.20-16.29_i386.deb
 /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jonathan@Lalita:~$ 
[/I]

**And i still have the error. So i went to Synaptic to look for the broken packages. And as i click it the message comes up again**
[I]
You have 2 broken packages on your system!

Use the "Broken" filter to locate them.[/I]

**So i ok that, clicked edit, and fix broken packages. then apply and the following error shows**

[I]An error occured

The following details are provided:

E: /var/cache/apt/archives/linux-headers-2.6.20-16_2.6.20-16.29_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
[/I]

**I am still majourly new to ubuntu and linux, infact started yesterday, so sorry for my lack of knowledge. Any ideas of what to do? Thanks so much!**

---

### Post by zvacet on 2007-08-12
**synaptic>edit>fix broken packages**

---

### Post by MenZa on 2007-08-12
> **zvacet said:**
> **synaptic>edit>fix broken packages**

In case you didn't notice, he did try that, and it returned an error code.

---

### Post by designwiz on 2007-08-12
try manuall downloading the package from
[http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/)
and installing it.. just a guess!

---

### Post by sad_iq on 2007-08-12
Try this first...see if it works:
 ```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bluenova on 2007-08-12
.

---

### Post by designwiz on 2007-08-12
try running
dselect from the terminal and doin the update, does it wrk?

---

### Post by designwiz on 2007-08-12
ok try this should ideally fix ur probkem

sudo apt-get --fix-broken

Fix; attempt to correct a system  with  broken  dependencies  in
              place.  This option, when used with install/remove, can omit any
              packages to permit APT to deduce a likely soltion.  Any  Package
              that  are  specified  must  completly  correct  the problem. The
              option is sometimes necessary when running  APT  for  the  first
              time;  APT  itself does not allow broken package dependencies to
              exist on a system. It is possible  that  a  system's  dependency
              structure  can  be  so corrupt as to require manual intervention
              (which usually means using dselect(8) or dpkg --remove to elimi-
              nate  some  of  the  offending  packages).  Use  of  this option
              together with -m may produce an error in some situations.   Con-
              figuration Item: APT::Get::Fix-Broken.

next

 sudo dpkg --configure -a

then
sudo apt-get update

---

### Post by truet on 2007-08-12
**Tried udo apt-get clean && sudo apt-get update && sudo apt-get upgrade and this is what happened...**

[I]jonathan@Lalita:~$ sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
Password:
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 0s (8B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
  linux-headers-2.6.20-16-generic: Depends: linux-headers-2.6.20-16 but it is not installed
  openoffice.org-style-human: Depends: openoffice.org-common (= 2.2.0-1ubuntu4) but 2.2.0-1ubuntu3 is installed
E: Unmet dependencies. Try using -f.
jonathan@Lalita:~$ 
[/I]
[B]
problem is still there.
As for manual downloading which package would it be and how would i do it? Finally whats dselect?
[/B]

---

### Post by designwiz on 2007-08-12
sudo apt-get --fix-broken

Fix; attempt to correct a system with broken dependencies in
place. This option, when used with install/remove, can omit any
packages to permit APT to deduce a likely soltion. Any Package
that are specified must completly correct the problem. The
option is sometimes necessary when running APT for the first
time; APT itself does not allow broken package dependencies to
exist on a system. It is possible that a system's dependency
structure can be so corrupt as to require manual intervention
(which usually means using dselect( or dpkg --remove to elimi-
nate some of the offending packages). Use of this option
together with -m may produce an error in some situations. Con-
figuration Item: APT::Get::Fix-Broken.

next

sudo dpkg --configure -a

then
sudo apt-get update

**P.S** In the Synaptics-->Settings-->Repositories
Make sure source is unchecked! try this one out!

---

### Post by nikef on 2007-08-12
> **truet said:**
> **So during update, an error came up saying it didnt complete, 2 broken packages. When i went to add/remove progs the following error shows**

[I]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/I]

**Heres what i tried via terminal, and the error message, infact the whole log.**

[I]jonathan@Lalita:~$ sudo apt-get update
Password:
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB [4827B]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB [1573B]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 6403B in 0s (16.1kB/s)
Reading package lists... Done
jonathan@Lalita:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  linux-headers-2.6.20-16 openoffice.org-common
Recommended packages:
  openoffice.org-style-industrial openoffice.org-style-tango
  openoffice.org-style-crystal openoffice.org-style-andromeda
  openoffice.org-style-hicontrast
The following NEW packages will be installed
  linux-headers-2.6.20-16
The following packages will be upgraded:
  openoffice.org-common
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/20.1MB of archives.
After unpacking 58.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 102754 files and directories currently installed.)
Unpacking linux-headers-2.6.20-16 (from .../linux-headers-2.6.20-16_2.6.20-16.29_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.20-16_2.6.20-16.29_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace openoffice.org-common 2.2.0-1ubuntu3 (using .../openoffice.org-common_2.2.0-1ubuntu4_all.deb) ...
Unpacking replacement openoffice.org-common ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.20-16_2.6.20-16.29_i386.deb
 /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jonathan@Lalita:~$ 
[/I]

**And i still have the error. So i went to Synaptic to look for the broken packages. And as i click it the message comes up again**
[I]
You have 2 broken packages on your system!

Use the "Broken" filter to locate them.[/I]

**So i ok that, clicked edit, and fix broken packages. then apply and the following error shows**

[I]An error occured

The following details are provided:

E: /var/cache/apt/archives/linux-headers-2.6.20-16_2.6.20-16.29_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
[/I]

**I am still majourly new to ubuntu and linux, infact started yesterday, so sorry for my lack of knowledge. Any ideas of what to do? Thanks so much!**

hi i have had the same error today :(  i was trying to install Amorok  from a cd

---

### Post by sad_iq on 2007-08-12
> **designwiz said:**
> sudo apt-get --fix-broken

 Gives errors on my system : **...This APT has Super Cow Powers.**
 If that doesn't work try **sudo apt-get -f  install**
 Also try this: ```
sudo apt-get check
``` then try updating and upgrading again!!!

---

### Post by meierfra on 2007-08-12
Try this: 
Delete the corrupted files:


```
sudo rm /var/cache/apt/archives/linux-headers-2.6.20-16_2.6.20-16.29_i386.deb
```

```
sudo  rm /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb
```

and then start over:

```
 sudo apt-get update 
```


```
 sudo apt-get upgrade
```

---

### Post by nikef on 2007-08-12
sorry to pinch your post truet ,but i was in a panic

i think its fixed now was able to update ok

---

