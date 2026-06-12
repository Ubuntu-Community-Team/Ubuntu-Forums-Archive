---
title: "What the #$^@#?"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-07-05
I have never been able to get XMMS to work. It loads but can't open or play anything. I'm still running Breezy (5.10). That shouldn't matter in removing programs.

I decided to remove XMMS. What the heck happened? Why does the printer driver come up? My printer works.

mark@lexington:~$ sudo apt-get remove xmms
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  xmms
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7389kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 86735 files and directories currently installed.)
Removing xmms ...
Setting up hl1440lpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/HL1440': No such file or directory
chown: cannot access `/var/spool/lpd/HL1440': No such file or directory
chgrp: cannot access `/var/spool/lpd/HL1440': No such file or directory
chmod: cannot access `/var/spool/lpd/HL1440': No such file or directory
/var/lib/dpkg/info/hl1440lpr.postinst: line 4: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1440lpr (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
mark@lexington:~$

---

### Post by tseliot on 2006-07-05
```
sudo apt-get update
```

Then
```
sudo apt-get install -f
```

---

### Post by Mark_in_Hollywood on 2006-07-29
I did as you commanded, Oh! Brew-Master:

sudo apt-get update

worked as expected

sudo apt-get install -f returned:

mark@lexington:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  hl1440lpr
0 upgraded, 0 newly installed, 1 to remove and 904 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 86155 files and directories currently installed.)
Removing hl1440lpr ...
/var/lib/dpkg/info/hl1440lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1440lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
mark@lexington:~$

Now what?

---

