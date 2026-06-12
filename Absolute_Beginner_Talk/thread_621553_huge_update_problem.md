---
title: "huge update problem"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Evil Wayz on 2007-11-23
Update manager keeps erroring out. I tried to use terminal and this is what I got.:

wolf@wolf-alteredbeast:~$ sudo apt-get install -f
[sudo] password for wolf:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgdk-pixbuf2 libemeraldengine0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  evolution evolution-common libgtkhtml3.14-19
Suggested packages:
  evolution-dbg evolution-plugins-experimental libgtkhtml3.14-dbg
The following packages will be REMOVED:
  evolution-exchange
The following packages will be upgraded:
  evolution evolution-common libgtkhtml3.14-19
3 upgraded, 0 newly installed, 1 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 0B/13.9MB of archives.
After unpacking 2527kB disk space will be freed.
Do you want to continue [Y/n]? y
E: Sub-process gzip returned an error code (1)
E: Prior errors apply to /var/cache/apt/archives/libgtkhtml3.14-19_3.16.1-0ubuntu1_i386.deb
E: Prior errors apply to /var/cache/apt/archives/evolution_2.12.1-0ubuntu1_i386.deb
E: Prior errors apply to /var/cache/apt/archives/evolution-common_2.12.1-0ubuntu1_all.deb
debconf: apt-extracttemplates failed: Bad file descriptor(Reading database ... 134329 files and directories currently installed.)
Removing evolution-exchange ...
(Reading database ... 134240 files and directories currently installed.)
Preparing to replace libgtkhtml3.14-19 3.16.0-0ubuntu1 (using .../libgtkhtml3.14-19_3.16.1-0ubuntu1_i386.deb) ...
Unpacking replacement libgtkhtml3.14-19 ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libgtkhtml3.14-19_3.16.1-0ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Preparing to replace evolution 2.12.0-0ubuntu5 (using .../evolution_2.12.1-0ubuntu1_i386.deb) ...
Unpacking replacement evolution ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/evolution_2.12.1-0ubuntu1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/gconf/schemas/evolution-mail.schemas')
Preparing to replace evolution-common 2.12.0-0ubuntu5 (using .../evolution-common_2.12.1-0ubuntu1_all.deb) ...
Unpacking replacement evolution-common ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/evolution-common_2.12.1-0ubuntu1_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libgtkhtml3.14-19_3.16.1-0ubuntu1_i386.deb
 /var/cache/apt/archives/evolution_2.12.1-0ubuntu1_i386.deb
 /var/cache/apt/archives/evolution-common_2.12.1-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
wolf@wolf-alteredbeast:~$

---

### Post by Pumalite on 2007-11-23
Did you run all the usual commands?. If nothing worked go and check /var/lib/dpkg/status and see what you find.

---

