---
title: "java not installing, bad packages"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-10-04
tried to do it thru synaptic but when that errored i tried these: all repos are checked in software sources. this computer has fiesty on it.

```

gail@buttmunch:~$ sudo aptitude update && sudo aptitude upgrade
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release             
Get:3 http://security.ubuntu.com feisty-security Release.gpg [191B] 
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty/main Packages
Hit http://security.ubuntu.com feisty-security Release
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Ign http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty/universe Packages
Ign http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Get:4 http://us.archive.ubuntu.com feisty/main Packages [1307kB]
Get:5 http://us.archive.ubuntu.com feisty/main Sources [385kB]
Get:6 http://us.archive.ubuntu.com feisty/universe Sources [1523kB]
99% [4 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty/main Packages
  Sub-process gzip returned an error code (1)
99% [5 Sources gzip 0] 
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty/main Sources
  Sub-process gzip returned an error code (1)
99% [6 Sources gzip 0]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty/universe Sources
  Sub-process gzip returned an error code (1)
Fetched 6B in 2s (3B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
gail@buttmunch:~$ 

```

```

gail@buttmunch:~$ sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find package "sun-java6-font".  However, the following
packages contain "sun-java6-font" in their name:
  sun-java6-fonts 
The following packages are BROKEN:
  sun-java6-bin sun-java6-jre 
The following NEW packages will be installed:
  sun-java6-plugin 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 32.5MB of archives. After unpacking 93.1MB will be used.
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc which is a virtual package.
  sun-java6-jre: Depends: java-common (>= 0.24) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
gail@buttmunch:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
gail@buttmunch:~$ 

```

---

### Post by zvacet on 2007-10-04
**synaptic>edit>fix broken packages**

---

### Post by lunaz on 2007-10-04
well tried that, it successfully fixed packages but i still cant get java

also clicked on mark all upgradeable packages > reload; and i got error:

```

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz: Sub-process gzip returned an error code (1)
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz: Sub-process gzip returned an error code (1)

```

this also happens when i try sudo aptitude update && sudo aptitude upgrade

---

