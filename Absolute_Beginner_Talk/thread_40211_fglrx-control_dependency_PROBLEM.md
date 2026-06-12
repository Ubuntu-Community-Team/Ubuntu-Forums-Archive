---
title: "fglrx-control dependency PROBLEM"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by bluecode77 on 2005-06-08
fglrx-control dependency PROBLEM
It has been almost a week since I have this problem; you can find below the suggestions I get from Ubuntu forums already. As you can see; none of the suggestions has been helpfull for me to resolve this issue.

When i try to install necessary files like gstreamer etc on synaptic I keep getting the same error:

`E: /var/cache/apt/archives/dpatch_2.0.10_all.deb: files list file for package `fglrx-control' is missing final newline`

I have also tried:
sudo dpkg --clear-avail
makes no better.....

And when i try to reinstall flgrx-control on root terminal it gives me the error below:

=======================================
root@darkstar:/home/alper # sudo apt-get install fglrx-control
Reading package lists... Done
Building dependency tree... Done
fglrx-control is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up ttf-indic-fonts (0.3.7ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format errordpkg: error processing ttf-indic-fonts (--configure):
subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
ttf-indic-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
=============================================

When I try to install mp3 support for my media player;system gives the error below:

root@darkstar:/home/alper # sudo apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
liblame0
The following NEW packages will be installed:
gstreamer0.8-lame liblame0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/307kB of archives.
After unpacking 582kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
gstreamer0.8-lame
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb (--unpack):
files list file for package `fglrx-control' is missing final newline
Errors were encountered while processing:
/var/cache/apt/archives/liblame0_3.96.1-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----------------------------------------------------------------------------------------------------------

I really don`t know what to do next.

---

### Post by dolphinsonar on 2006-12-11
Have you enabled all of your repositories?

---

