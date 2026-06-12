---
title: "[SOLVED] help!"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-12-01
i was trying to install win32 codecs but i keep getting this error from the terminal (its right at the bottom)
i was using this to help [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)




```
rugs@Peters-laptop:~$ sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for rugs:
--13:51:55--  http://www.medibuntu.org/sources.list.d/gutsy.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving www.medibuntu.org... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

100%[====================================>] 223           --.--K/s             

13:51:55 (30.75 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [223/223]

rugs@Peters-laptop:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
OK
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get: 1 http://packages.medibuntu.org gutsy Release.gpg [189B] 
Ign http://packages.medibuntu.org gutsy/free Translation-en_GB
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_GB
Get: 2 http://packages.medibuntu.org gutsy Release [2723B]
Ign http://packages.medibuntu.org gutsy/free Packages
Ign http://packages.medibuntu.org gutsy/non-free Packages
Get: 3 http://packages.medibuntu.org gutsy/free Packages [4400B]
Get: 4 http://packages.medibuntu.org gutsy/non-free Packages [2997B]
Fetched 10.3kB in 4s (2378B/s) 
Reading package lists... Done
rugs@Peters-laptop:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  regionset
The following NEW packages will be installed
  libdvdcss2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.3kB of archives.
After unpacking 106kB of additional disk space will be used.
Get: 1 http://packages.medibuntu.org gutsy/free libdvdcss2 1.2.9-2medibuntu4 [36.3kB]
Fetched 36.3kB in 3s (9253B/s)           
Selecting previously deselected package libdvdcss2.
(Reading database ... 88932 files and directories currently installed.)
Unpacking libdvdcss2 (from .../libdvdcss2_1.2.9-2medibuntu4_i386.deb) ...
Setting up libdvdcss2 (1.2.9-2medibuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
rugs@Peters-laptop:~$ wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
--13:53:48--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
           => `libdvdcss2_1.2.9-2medibuntu4_i386.deb'
Resolving packages.medibuntu.org... 88.191.13.100, 87.98.242.10, 193.34.16.167
Connecting to packages.medibuntu.org|88.191.13.100|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 36,270 (35K) [application/x-debian-package]

100%[====================================>] 36,270        45.38K/s             

13:53:49 (45.31 KB/s) - `libdvdcss2_1.2.9-2medibuntu4_i386.deb' saved [36270/36270]

rugs@Peters-laptop:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
(Reading database ... 88941 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu4 (using libdvdcss2_1.2.9-2medibuntu4_i386.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.9-2medibuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
rugs@Peters-laptop:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  w32codecs: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages
rugs@Peters-laptop:~$ 

```

---

### Post by PmDematagoda on 2007-12-01
Do:-
```

sudo apt-get install -f
```

To try and fix the broken packages.

---

### Post by kamitsukai on 2007-12-01
nah it doesent do anything and i get tthis

rugs@Peters-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by PmDematagoda on 2007-12-01
Could you post the results of:-

```
cat /etc/apt/sources.list
```

---

### Post by SunnyRabbiera on 2007-12-01
actually thats kind of a good thing if its not sputtering out errors or giving you broken package warnings.
you can try to install all this via synaptic, it might be a smoother ride as its sometimes a bit better picking out dependencies then apt.

---

### Post by ItsMitsHere on 2007-12-01
I think u should try to locate the codec packages on other repositories, in case the repository u are trying contains some broaken package! Alternatively, try to find an older version, install and then update. 

To fix the broaken packages/dependancies try this...

**sudo apt-get --fix-missing**

and then 

**sudo apt-get update**

hope this helps.

---

