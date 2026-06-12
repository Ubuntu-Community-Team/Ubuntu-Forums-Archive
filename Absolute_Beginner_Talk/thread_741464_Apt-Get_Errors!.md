---
title: "Apt-Get Errors!"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Drezard on 2008-03-31
I keep trying to install proftpd and I get this output:

> 

$ sudo apt-get install proftpd
[sudo] password for administrator:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
proftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.45-1ubuntu3.3) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)



Whats wrong?

Daniel

---

### Post by Tatty on 2008-03-31
It sounds like a previous install was interrupted before completing.

try:

```
dpkg --configure -a
```

---

### Post by abhiroopb on 2008-03-31
To start with according to the following line: 
```

proftpd is already the newest version.

```
you already have the program installed.

Firstly I suggest you do:
```

sudo apt-get upgrade

```

These may be causing the MySQL errors.

---

### Post by 65 mustang on 2008-03-31
possibly try
```
apt-get update -f
```
>       -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to
           permit APT to deduce a likely solution. Any Package that are specified must completely correct the problem. The option is sometimes necessary
           when running APT for the first time; APT itself does not allow broken package dependencies to exist on a system. It is possible that a
           system’s dependency structure can be so corrupt as to require manual intervention (which usually means using dselect(8) or dpkg --remove to
           eliminate some of the offending packages). Use of this option together with -m may produce an error in some situations. Configuration Item:
           APT::Get::Fix-Broken.



---

### Post by smoker on 2008-03-31
>  dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured

it looks like the problem is to do with 'mysql-server-5.0'

just a suggestion, try reinstalling that, and then try 'proftpd' again,

---

