---
title: "Can't download any packages!"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by mattjones56 on 2006-10-31
I'm tryin to download packages, using Synaptic Package Manager, and then I tried using the terminal and I get this message for anything I try to download (apart from obvoiusly a different file name), what have I forgotten to do?

Errhttp://archive.ubuntu.com dapper/main binutils 2.16.1cvs20060117-1ubuntu2
  Could not connect to archive.ubuntu.com:80 (195.248.90.54). - connect (111 Connection refused)

---

### Post by x64Jimbo on 2006-10-31
It could be your sources.list file being configured improperly. You could try backing up your current one and using one like [this]("http://ubuntuforums.org/showthread.php?t=185758") instead.

---

### Post by mattjones56 on 2006-10-31
did that and then i got this,

sudo aptitude update && sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (82.211.81.142). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (195.248.90.23). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (195.248.90.23). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (195.248.90.23). - connect (111 Connection refused)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

I'm sure i've done the source.list thing right before and it didn't work, could my university network be blocking access? highly unlikly but would this be the right message if that were the case?

---

### Post by x64Jimbo on 2006-10-31
You could try using a proxy server for port 80 stuff. You can set up proxy settings in Synaptic under Settings > Preferences > Network.

---

