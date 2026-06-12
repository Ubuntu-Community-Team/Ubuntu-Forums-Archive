---
title: "nautilus-data won't update properly"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2008-02-24
This is the error I get when I install updates on my Gutsy system..Thanks in advance for 
any help regarding this issue.

```
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error processing /var/cache/apt/archives/nautilus-data_1%3a2.20.0-0ubuntu7.1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/nautilus-data_1%3a2.20.0-0ubuntu7.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on nautilus-data (>= 1:2.20); however:
  Package nautilus-data is not installed.
 nautilus depends on nautilus-data (<< 1:2.21); however:
  Package nautilus-data is not installed.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nautilus

```

---

### Post by wolfen69 on 2008-02-24
try these 2 commands:
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

---

### Post by wolfen69 on 2008-02-24
also, if the above wont work, nautilus data may be on the ubuntu cd. go to software sources, enable cd rom. insert cd, then try to update.

---

### Post by shanepardue on 2008-02-24
Unfortunately, I've tried those. Here's the output if it helps at all. Thanks for your input!

```
bill@bobby-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on nautilus-data (>= 1:2.20); however:
  Package nautilus-data is not installed.
 nautilus depends on nautilus-data (<< 1:2.21); however:
  Package nautilus-data is not installed.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nautilus
bill@bobby-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B/913kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 160585 files and directories currently installed.)
Preparing to replace nautilus-data 1:2.20.0-0ubuntu7 (using .../nautilus-data_1%3a2.20.0-0ubuntu7_all.deb) ...
Unpacking replacement nautilus-data ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error processing /var/cache/apt/archives/nautilus-data_1%3a2.20.0-0ubuntu7_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/nautilus-data_1%3a2.20.0-0ubuntu7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by shanepardue on 2008-02-24
> **wolfen69 said:**
> also, if the above wont work, nautilus data may be on the ubuntu cd. go to software sources, enable cd rom. insert cd, then try to update.
I believe this to be a good solution, but my Ubuntu install was corrupt 
in other ways and I believe this is part of what caused the nautilus-data 
issue. I am reinstalling Ubuntu for hard drive related problems. Thanks 
for your help!

---

