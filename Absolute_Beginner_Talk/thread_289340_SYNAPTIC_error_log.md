---
title: "SYNAPTIC error log"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2006-10-30
Whilst attempting to update with Synaptic I get a message that a package is corrupt, running the following command, sudo apt-get install -f this is tyhe output.

Synaptic will not allow me to upgrade without fixing the error. I am unable to delete or upgrade the package - which I do not need by the way.



******************:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/2904kB of archives.
After unpacking 123kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 103485 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu4_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Hope some-one can help


Tony

---

