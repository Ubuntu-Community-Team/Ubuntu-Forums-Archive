---
title: "Fixing 101: ACPI"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-27
Since not everyone has or had a fix for the turning off issues that I experienced, I decided to have another experiment(s).

Everytime I boot or anything, I always see the acpi-funcs something like that, no such folder or file. Like [http://ubuntuforums.org/showthread.php?t=218092](http://ubuntuforums.org/showthread.php?t=218092)

Now, if you all read my previous threads, my laptop always turns off or logs off, probably because of CompizFusion. Also weird panel(top) icons, randomly changed positions, and spaces between them.

Now, I had this theory of turning off ACPI, since I received that error.

The problem: Compiz now does not work. Solution: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519)

Another solution: [http://ubuntuforums.org/showthread.php?t=218113](http://ubuntuforums.org/showthread.php?t=218113)

Compiz did work although, it's slow and I saw weird patterns on my desktop like changing a monitor's solution onto a higher one but the monitor does not support it...

Now, I tried turning on ACPI forcely(but my laptop supports ACPI=on by default), then tried, [https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/63450](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/63450) and really confused if I should use this [http://bugs.gentoo.org/show_bug.cgi?id=99446](http://bugs.gentoo.org/show_bug.cgi?id=99446)

Probably, this is what happens on my laptop [https://launchpad.net/ubuntu/+source/acpi-support/+bug/22336](https://launchpad.net/ubuntu/+source/acpi-support/+bug/22336)

Or this [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/18864](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/18864)

Do you think I have to post this on LaunchPad? I think this is a serious error or bug, because it's really not nice for Ubuntu to log off or turn off your laptop or Pc automatically, specially when you are working.

Also, tried disabling CompizFusion, yeah, probably it's the fix, but I want CompizFusion enabled so I had the above theories above, i'll monitor if they will work.

My terminal:

```
karlo@karlo-laptop:~$ watch cat /proc/acpi/thermal_zone/THRS/trip_points
cat: /proc/acpi/thermal_zone/THRS/trip_points: No such file or directory
karlo@karlo-laptop:~$ sudo killall hald
[sudo] password for karlo:
karlo@karlo-laptop:~$ sudo dpkg --configure -a
karlo@karlo-laptop:~$ sudo apt-get install acpi-support
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  acpi-support
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.7kB of archives.
After unpacking 877kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  acpi-support
Install these packages without verification [y/N]? y
Get:1 http://ph.archive.ubuntu.com gutsy/main acpi-support 0.103 [35.7kB]
Fetched 35.7kB in 2s (16.6kB/s)      
Selecting previously deselected package acpi-support.
(Reading database ... 134729 files and directories currently installed.)
Unpacking acpi-support (from .../acpi-support_0.103_i386.deb) ...
Setting up acpi-support (0.103) ...
 * Checking battery state...                                             [ OK ] 

karlo@karlo-laptop:~$ sudo dpkg -l *acpi*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  acpi           0.09-3ubuntu1  displays information on ACPI devices
ii  acpi-support   0.103          a collection of useful events for acpi
ii  acpid          1.0.4-5ubuntu8 Utilities for using ACPI power management
karlo@karlo-laptop:~$ sudo apt-get install acpi acpid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
acpi is already the newest version.
acpid is already the newest version.
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
karlo@karlo-laptop:~$ sudo apt-get autoremovce
E: Invalid operation autoremovce
karlo@karlo-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
The following packages will be REMOVED:
  libglitz-glx1 libglitz1
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 344kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 134758 files and directories currently installed.)
Removing libglitz-glx1 ...
Removing libglitz1 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
karlo@karlo-laptop:~$ 
```

---

