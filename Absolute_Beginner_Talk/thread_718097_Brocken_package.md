---
title: "Brocken package"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2008-03-07
So trying to open add/remove gave me this error:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


I opened synaptic and found the broken package (libdvdcss2).
How do I "check file premissions" and so on, to go about fixing it?

---

### Post by taurus on 2008-03-07
What happens when you run these two commands from a terminal, don't forget to close down synaptic first?

```
sudo apt-get install -f
sudo apt-get update
```

---

### Post by jw5801 on 2008-03-07
If you could open a terminal (Applications > Accessories > Terminal) and run the following commands and then post the entire lot here, we can see what's wrong:
```
ls -l /etc/apt/
cat /etc/apt/source.list
sudo apt-get update
sudo apt-get install -f
```

---

### Post by zazen666 on 2008-03-07
> **jw5801 said:**
> If you could open a terminal (Applications > Accessories > Terminal) and run the following commands and then post the entire lot here, we can see what's wrong:
```
ls -l /etc/apt/
cat /etc/apt/source.list
sudo apt-get update
sudo apt-get install -f
```


Here is the entire post:

marshal@marshal-laptop:~$ ls -l /etc/apt/
total 164
drwxr-xr-x 2 root root  4096 2007-08-11 09:49 apt.conf.d
-rw------- 1 root root     0 2007-04-15 22:15 secring.gpg
-rw-r--r-- 1 root root  2864 2007-12-24 08:48 sources.list
-rw-r--r-- 1 root root  2370 2007-04-21 10:10 sources.list_backup_200704211010
-rw-r--r-- 1 root root  2782 2007-04-22 12:51 sources.list_backup_200704221251
-rw-r--r-- 1 root root  2782 2007-04-22 14:29 sources.list_backup_200704221429
-rw-r--r-- 1 root root  2782 2007-04-22 19:43 sources.list_backup_200704221943
-rw-r--r-- 1 root root  2782 2007-04-22 21:07 sources.list_backup_200704222107
-rw-r--r-- 1 root root  2782 2007-05-18 23:20 sources.list_backup_200705182320
-rw-r--r-- 1 root root  2782 2007-06-23 12:57 sources.list_backup_200706231257
-rw-r--r-- 1 root root  2782 2007-07-30 16:52 sources.list_backup_200707301652
-rw-r--r-- 1 root root  2782 2007-08-11 09:48 sources.list_backup_200708110948
-rw-r--r-- 1 root root  2782 2007-08-12 12:52 sources.list_backup_200708121252
-rw-r--r-- 1 root root  2782 2007-09-15 16:07 sources.list_backup_200709151607
-rw-r--r-- 1 root root  2782 2007-09-15 16:29 sources.list_backup_200709151629
-rw-r--r-- 1 root root  2782 2007-09-15 16:45 sources.list_backup_200709151645
-rw-r--r-- 1 root root  2782 2007-09-16 04:41 sources.list_backup_200709160441
-rw-r--r-- 1 root root  2782 2007-09-16 04:50 sources.list_backup_200709160450
-rw-r--r-- 1 root root  2782 2007-09-17 06:12 sources.list_backup_200709170612
-rw-r--r-- 1 root root  2782 2007-09-17 06:16 sources.list_backup_200709170616
-rw-r--r-- 1 root root  2864 2008-02-24 22:09 sources.list_backup_200802242209
drwxr-xr-x 2 root root  4096 2008-02-25 22:27 sources.list.d
-rw-r--r-- 1 root root  2864 2007-12-24 08:48 sources.list.save
-rw------- 1 root root  1200 2007-04-21 10:10 trustdb.gpg
-rw-r--r-- 1 root root 34707 2007-04-21 10:10 trusted.gpg
-rw-r--r-- 1 root root 33522 2007-04-21 10:10 trusted.gpg~
marshal@marshal-laptop:~$ cat /etc/apt/source.list
cat: /etc/apt/source.list: No such file or directory
marshal@marshal-laptop:~$ sudo apt-get update
Password:
Get:1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) feisty/ Release.gpg
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) feisty/ Translation-en_US
Get:3 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/main Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) feisty/ Release 
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty Release
Get:6 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US
Get:7 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates Release [50.9kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) feisty/ Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:9 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release [5999B]
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main Packages
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/restricted Packages
Hit [http://ftp.osuosl.org](http://ftp.osuosl.org) feisty/ Packages
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [50.9kB]
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/restricted Sources
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe Packages
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe Sources
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release [44.6kB]
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages
Get:13 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US
Get:14 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/main Packages [187kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
Get:15 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/restricted Packages [6341B]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
  
Get:16 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/main Sources [45.9kB]
Get:17 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release [2195B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
Get:18 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/restricted Sources [956B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release [50.9kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [115kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release [50.9kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages [32.0kB]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages [14B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages [53.1kB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages [4849B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages [86.6kB]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6341B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources [21.1kB]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources [956B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [71.0kB]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages [12.8kB]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages [115kB]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources [10.3kB]
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [6092B]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources [1056B]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages [6341B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages [71.0kB]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages [6092B]
Fetched 1119kB in 5s (210kB/s)    
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
marshal@marshal-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libsdl-console libsdl-gfx1.2-4
  libsdl-ttf2.0-0 espeak-data libespeak1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libdvdcss2
0 upgraded, 0 newly installed, 1 to remove and 16 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 106kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 134371 files and directories currently installed.)
Removing libdvdcss2 ...
marshal@marshal-laptop:~$

---

### Post by zazen666 on 2008-03-07
...seems to have fixed the problem

thanks

---

