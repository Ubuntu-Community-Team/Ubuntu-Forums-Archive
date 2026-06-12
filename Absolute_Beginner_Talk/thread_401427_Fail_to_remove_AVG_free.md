---
title: "Fail to remove AVG free"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by gwatts on 2007-04-04
I am trying to uninstall AVG Free for Linux the debian package from Ubuntu 6.10.

It is at least partially installed but I am unable to update ie (permission denied0 or to remove it with many attempts. The procedures I tried suggested on the multiple sites I have visited all either fail or send me in a circular direction coming back to where I started. AVG site is overwhelming n complexity.

I there any way in Linux to remove this package?
See failures below.

This is the error in Package Manager.
E: avg75fld: subprocess pre-removal script returned error exit status 150

Using the terminal >

kk@jjj:~$ sudo aptitude remove avg
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find package "avg".  However, the following
packages contain "avg" in their name:
  wmavgload avggui avg75fld avglinux 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

kk@jjj:~$ sudo apt-get remove avg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avg

kk@jjj:~$ sudo aptitude remove wmavgload avggui avg75fld avglinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  avg75fld 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 108112 files and directories currently installed.)
Removing avg75fld ...
 * Stopping avgdkill: 246: Illegal number: -
local: 246: 4116: bad variable name
( not running)
 *                                                                       [fail]
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing avg75fld (--remove):
 subprocess pre-removal script returned error exit status 150
Errors were encountered while processing:
 avg75fld
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
kk@jjj:~$

---

### Post by Happy_Man on 2007-04-04
Is AVG running when you try to uninstall? Go into the System Monitor and see whether AVG has any processes running. That could explain your problems.

---

### Post by zvacet on 2007-04-04
```
 sudo apt-get remove --purge program 

```

If that fails do this
```
whereis program_name ls
```

and you will see every directory containing AVG.Go in every of them with** cd /directory_name** and remove program manualy with this command
```
sudo rm -r program_name
```

---

### Post by mikewhatever on 2007-04-04
Boot into recovery console. You will not have any GUI there, so write it down if you want. Then type > sudo dpkg -P avg75fld

---

### Post by gwatts on 2007-04-06
I formatted and started over.
 with other problems.


Thank you for  your help.

---

