---
title: "Samba reinstall error"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by craig.brisbane on 2007-05-29
I have an error with samba - I have attempted to reinstall and remove. I'm using ubuntu 7.04.  I have been receiving this error message - 


craig@ubuntu-desktop:~$ sudo aptitude reinstall samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  samba 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/3341kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
debconf: Perl may be unconfigured (Perl v3214542573.6.0 required (did you mean v3214542573.000?)--this is only v5.8.8, stopped at /usr/share/perl/5.8/FileHandle.pm line 3.
BEGIN failed--compilation aborted at /usr/share/perl/5.8/FileHandle.pm line 3.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
Selecting previously deselected package samba.
(Reading database ... 162274 files and directories currently installed.)
Preparing to replace samba 3.0.24-2ubuntu1.2 (using .../samba_3.0.24-2ubuntu1.2_i386.deb) ...
Unpacking replacement samba ...
Perl v3086540837.0.0 required (did you mean v3086540837.000?)--this is only v5.8.8, stopped at /usr/sbin/update-inetd line 22.
dpkg: warning - old post-removal script returned error exit status 255
dpkg - trying script from the new package instead ...
Perl v3086082085.0.0 required (did you mean v3086082085.000?)--this is only v5.8.8, stopped at /usr/sbin/update-inetd line 22.
dpkg: error processing /var/cache/apt/archives/samba_3.0.24-2ubuntu1.2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 255
Perl v3086983205.0.0 required (did you mean v3086983205.000?)--this is only v5.8.8, stopped at /usr/sbin/update-inetd line 22.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 255
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.24-2ubuntu1.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba-common (3.0.24-2ubuntu1.2) ...
Perl v3218397293.6.0 required (did you mean v3218397293.000?)--this is only v5.8.8, stopped at /usr/share/perl/5.8/vars.pm line 3.
BEGIN failed--compilation aborted at /usr/share/perl/5.8/vars.pm line 3.
Compilation failed in require at /usr/share/perl/5.8/base.pm line 4.
BEGIN failed--compilation aborted at /usr/share/perl/5.8/base.pm line 4.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Log.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.24-2ubuntu1.2); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbfs:
 smbfs depends on samba-common (= 3.0.24-2ubuntu1.2); however:
  Package samba-common is not configured yet.
dpkg: error processing smbfs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common
 smbclient
 smbfs
craig@ubuntu-desktop:~$ 

Any ideas? I have tried sudo aptitude clean and sudo aptitude autoclean

tks
craig

---

### Post by apjone on 2007-05-29
try a 
sudo apt-get install -f

that shoulod fix any broken packages.

---

### Post by craig.brisbane on 2007-05-29
Hi 

Have tried sudo apt-get install -f; received this error message - 

craig@ubuntu-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic libevent-execflow-perl libresid-builder0c2a
  libintl-perl libevent-rpc-perl ogmtools libaudacious4
  gtk2-ex-formfactory-perl anyevent-perl linux-headers-2.6.20-15 libsidplay2
  libevent-perl libimlib2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/3341kB of archives.
After unpacking 0B of additional disk space will be used.
debconf: Perl may be unconfigured (Perl v3214243501.6.0 required (did you mean v3214243501.000?)--this is only v5.8.8, stopped at /usr/share/perl/5.8/FileHandle.pm line 3.
BEGIN failed--compilation aborted at /usr/share/perl/5.8/FileHandle.pm line 3.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
(Reading database ... 162310 files and directories currently installed.)
Preparing to replace samba 3.0.24-2ubuntu1.2 (using .../samba_3.0.24-2ubuntu1.2_i386.deb) ...
Unpacking replacement samba ...
Perl v3086086181.0.0 required (did you mean v3086086181.000?)--this is only v5.8.8, stopped at /usr/sbin/update-inetd line 22.
dpkg: warning - old post-removal script returned error exit status 255
dpkg - trying script from the new package instead ...
Perl v3086835749.0.0 required (did you mean v3086835749.000?)--this is only v5.8.8, stopped at /usr/sbin/update-inetd line 22.
dpkg: error processing /var/cache/apt/archives/samba_3.0.24-2ubuntu1.2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 255
Perl v3086069797.0.0 required (did you mean v3086069797.000?)--this is only v5.8.8, stopped at /usr/sbin/update-inetd line 22.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 255
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.24-2ubuntu1.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
craig@ubuntu-desktop:~$ 

Any suggestions?
tks

---

### Post by apjone on 2007-05-30
try

sudo apt-get autoremove

see if that gets rid of some stuff and then try 

sudo apt-get install -f again

Have you changed your apt repos lately?

---

### Post by craig.brisbane on 2007-05-30
Hello apjone, thanks for getting  back to me - tried the command as suggest - I get the following

craig@ubuntu-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic libevent-execflow-perl libresid-builder0c2a
  libintl-perl libevent-rpc-perl ogmtools libaudacious4
  gtk2-ex-formfactory-perl anyevent-perl linux-headers-2.6.20-15 libsidplay2
  libevent-perl libimlib2
The following packages will be REMOVED:
  anyevent-perl gtk2-ex-formfactory-perl libaudacious4 libevent-execflow-perl
  libevent-perl libevent-rpc-perl libimlib2 libintl-perl libresid-builder0c2a
  libsidplay2 linux-headers-2.6.20-15 linux-headers-2.6.20-15-generic ogmtools
0 upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/3341kB of archives.
After unpacking 74.3MB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: Perl may be unconfigured (Perl v3217414573.6.0 required (did you mean v3217414573.000?)--this is only v5.8.8, stopped at /usr/share/perl/5.8/FileHandle.pm line 3.
BEGIN failed--compilation aborted at /usr/share/perl/5.8/FileHandle.pm line 3.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
(Reading database ... 162314 files and directories currently installed.)
Preparing to replace samba 3.0.24-2ubuntu1.2 (using .../samba_3.0.24-2ubuntu1.2_i386.deb) ...
Unpacking replacement samba ...
Perl v3086340133.0.0 required (did you mean v3086340133.000?)--this is only v5.8.8, stopped at /usr/sbin/update-inetd line 22.
dpkg: warning - old post-removal script returned error exit status 255
dpkg - trying script from the new package instead ...
Perl v3086975013.0.0 required (did you mean v3086975013.000?)--this is only v5.8.8, stopped at /usr/sbin/update-inetd line 22.
dpkg: error processing /var/cache/apt/archives/samba_3.0.24-2ubuntu1.2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 255
Perl v3086229541.0.0 required (did you mean v3086229541.000?)--this is only v5.8.8, stopped at /usr/sbin/update-inetd line 22.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 255
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.24-2ubuntu1.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
craig@ubuntu-desktop:~$ 

I have not added or modified the repos.

Any suggestions??
thanks

---

