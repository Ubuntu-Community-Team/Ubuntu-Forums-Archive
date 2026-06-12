---
title: "broken pl. help"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by drpas2k on 2007-06-03
When I tried to use update manager, I was asked to use terminal to correct the broken packages. when I tried I am getting this message.

 please help me to solve this. thanks

ohm@ohm-desktop:~$ sudo apt-get install -f 
Password:
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcairo-java-gcj libk3b2 libbcprov-java-gcj libglib-java-gcj
  libswt3.2-gtk-java libgtk-jni libcairo-java openoffice.org-l10n-ta-in
  libbcprov-java kviewshell libglib-java debtags libgtk-java libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  stopmotion
Suggested packages:
  fam
Recommended packages:
  vgrabbj
The following packages will be upgraded:
  stopmotion
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2297kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 89 package `stopmotion':
 `Depends' field, invalid package name `libsdl-image1.2"': character `"' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
ohm@ohm-desktop:~$

---

### Post by mystman on 2007-06-03
Try using aptitude's install feature.  It'll automatically try to fix the broken packages.

---

