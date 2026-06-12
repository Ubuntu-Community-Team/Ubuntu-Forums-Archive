---
title: "samba wont update"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by jinxs1591 on 2007-07-29
I keep getting a error when trying to update samba

Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/2849kB of archives.
After unpacking 8192B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 115459 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.3_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sad_iq on 2007-07-29
Try a ```
sudo apt-get install -f
``` first

---

### Post by jinxs1591 on 2007-07-29
tried it still got more error
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/2849kB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 115459 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.3_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sad_iq on 2007-07-29
ok...my friend google came up with this: [https://answers.launchpad.net/ubuntu/+question/3583](https://answers.launchpad.net/ubuntu/+question/3583) Try it and post your results :)

---

### Post by jinxs1591 on 2007-07-29
that seem to work.
jinx@jinx-desktop:~$ sudo dpkg -P samba samba-common smbclient
(Reading database ... 115421 files and directories currently installed.)
Removing samba ...
Purging configuration files for samba ...
Removing configuration file /etc/default/samba...
Removing configuration file /etc/default/samba...
dpkg: dependency problems prevent removal of smbclient:
 ubuntu-desktop depends on smbclient; however:
  Package smbclient is to be removed.
dpkg: error processing smbclient (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of samba-common:
 smbclient depends on samba-common (= 3.0.22-1ubuntu3.3).
dpkg: error processing samba-common (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 smbclient
 samba-common
jinx@jinx-desktop:~$  sudo rm -f /etc/rc*.d/*samba /etc/init.d/samba
jinx@jinx-desktop:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/2849kB of archives.
After unpacking 7258kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 115372 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.22-1ubuntu3.3_i386.deb) ...
Setting up samba (3.0.22-1ubuntu3.3) ...
Generating /etc/default/samba...
 * Starting Samba daemons...                                           
thank you guys so much

---

