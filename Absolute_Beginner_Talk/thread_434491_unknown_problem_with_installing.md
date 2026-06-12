---
title: "unknown problem with installing"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-05-06
when I try to use the add/remove program utility or synaptic package manager I get the following error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I enter that into terminal, I get:

Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
grep: /etc/mysql/my.cnf: No such file or directory
 * Starting MySQL database server mysqld                                 [ OK ] 
/etc/init.d/mysql: line 122: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.


Whaaaa?

---

### Post by taurus on 2007-05-06
What happens when you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by woodsonoversoul on 2007-05-06
Actually, synaptic was still working on the "sudo dpkg --configure -a" command when I tried to enter the other two. When I forced an exit it displayed:

dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server

I will now try the other two commands

All this may have to do with an earlier problem which I still haven't resolved
[http://ubuntuforums.org/showthread.php?t=430056](http://ubuntuforums.org/showthread.php?t=430056)

---

### Post by woodsonoversoul on 2007-05-06
I ran those commands, but came back with a lot of errors. I know it's a lot of information, but maybe it's of some use...

errors begin right about here:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 25.6kB in 1s (15.3kB/s)
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/dists/edgy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/dists/edgy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/dists/edgy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/dists/edgy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
dan@Desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libwavpack0 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 197kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 133401 files and directories currently installed.)
Removing libwavpack0 ...
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                            [ OK ] 
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
grep: /etc/mysql/my.cnf: No such file or directory
 * Starting MySQL database server mysqld                                            [ OK ] 
/etc/init.d/mysql: line 122: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                            [ OK ] 
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
grep: /etc/mysql/my.cnf: No such file or directory
 * Starting MySQL database server mysqld                                            [ OK ] 
/etc/init.d/mysql: line 122: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server

---

### Post by psoulocybe on 2007-05-09
I'm haivng this exact problem.   I can't figure out what to do to fix it for the life of me!

---

### Post by psoulocybe on 2007-05-09
I got it!

sudo apt-get autoremove --purge mysql-server mysql-server-5.0
sudo apt-get install mysql-server

---

### Post by loucomballa on 2007-05-09
I've got the same problem, mysql does not start when installed. and 
sudo apt-get autoremove --purge mysql-server mysql-server-5.0
sudo apt-get install mysql-server
does not work
I noticed however that when the machine boots, mysql is up and ready but if I stop it I cannot launch it again.

---

### Post by loucomballa on 2007-05-09
The only way to solve the problem has been to change the bind-adress in my my.conf to 0.0.0.0 instead of 127.0.0.1 although that is no the safest way of dealing with the problem...

---

### Post by fabietto on 2007-05-23
> **psoulocybe said:**
> I got it!

sudo apt-get autoremove --purge mysql-server mysql-server-5.0
sudo apt-get install mysql-server

Yeah! Now it works!

---

### Post by ansem227 on 2007-05-27
I have the same problem as the person before me
and im just wondering if someone could help,

 * Stopping MySQL database server mysqld                                 [ ok ]
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
grep: /etc/mysql/my.cnf: No such file or directory
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

---

### Post by kiev on 2007-12-31
Heeelp!!!!!
I'm haivng this exact problem!!!
Setting up mysql-server-5.0 (5.0.45-1ubuntu3.1) ...
 * Stopping MySQL database server mysqld                                                 [ OK ]
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 143: /etc/mysql/conf.d/old_passwords.cnf: No such file or directory
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

root:~# /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                                 [ OK ]
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
grep: /etc/mysql/my.cnf: No such file or directory
 * Starting MySQL database server mysqld                                                 [fail]

---

