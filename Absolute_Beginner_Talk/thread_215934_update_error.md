---
title: "update error"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Crashed on 2006-07-14
hi, i just ran the update and it failed telling me the software index is broken and to run sudo apt-get install -f and i get,

ash@Laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 113708 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ash@Laptop:~$

my network access seems to be fine can't find any problems other then the update system no longer works... searched through this forum and found one thread but not much help for this actual prob.. 

any help gratefully recieved...

Ash :rolleyes:

---

### Post by Zymous on 2006-07-14
I've got this problem as well.

The solution is in this thread [http://www.ubuntuforums.org/showthread.php?t=214848](http://www.ubuntuforums.org/showthread.php?t=214848)

-- 
Zym

---

### Post by Crashed on 2006-07-16
thanks very much that sorted it out for me..

:D

---

