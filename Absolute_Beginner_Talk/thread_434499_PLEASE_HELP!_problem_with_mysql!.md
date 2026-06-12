---
title: "PLEASE HELP! problem with mysql!"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-05-06
I tried to get the LAMP stack from the repositories in ver 7.04. That was an enormous hassle and I still haven't figured it out. ([http://ubuntuforums.org/showthread.php?t=430056](http://ubuntuforums.org/showthread.php?t=430056))

Now I'm having problems accessing synaptic and the add/remove program utility.
([http://ubuntuforums.org/showthread.php?t=434491](http://ubuntuforums.org/showthread.php?t=434491))

and in all the error messages, and when ever it freezes up, it's always trying to start or configure mysql, even if I 'm doing something which seem totally unrelated to mysql. Please help. What do I do?

---

### Post by taurus on 2007-05-06
Are you running Edgy or Feisty?  The thread from the second link has Edgy repos!

```
cat /etc/apt/sources.list
```

---

### Post by woodsonoversoul on 2007-05-06
when I enter that command it mentions both of them:

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all

---

### Post by taurus on 2007-05-06
You're not supposed to mix those two repos in /etc/apt/sources.list.  Bad things can happen and usually do happen.  So, are you running Feisty on your machine?  If it is, then you may want to generate a new list.

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
gksudo gedit /etc/apt/sources.list
```
And here is your new list.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main 

```
Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by woodsonoversoul on 2007-05-06
That's the whole list? Just copy and paste?

---

### Post by woodsonoversoul on 2007-05-06
Okay, I see we're making a backup of the original.

Now it says:

mv: cannot stat `/etc/apt/sources.lists': No such file or directory

even though we just looked at it

---

### Post by taurus on 2007-05-06
Got an extra s in there.

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
```

---

### Post by woodsonoversoul on 2007-05-06
Yeah I saw that right after I posted. Okay (thanks for your help so far, I really appreciate it), I changed sources.list, ran aptitude update which went fine until:

Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages [14B]                
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages [14B]                  
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages [14B]                
Fetched 6533kB in 15s (431kB/s)                                                            
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache

I then ran 'dkpg --configure -a' and got:

Setting up libgtksourceview2.0-cil (0.10-3.1) ...
Setting up liblog4net1.2-cil (1.2.9beta-0ubuntu2) ...
* Installing 1 assembly from liblog4net1.2-cil into Mono

Setting up anjuta-common (1.2.4a-5build1) ...

Setting up libmono-accessibility2.0-cil (1.2.3.1-1ubuntu1) ...
Setting up libmono-system-runtime2.0-cil (1.2.3.1-1ubuntu1) ...
Setting up lynx (2.8.5-2ubuntu4) ...

Setting up monodoc-base (1.2.3-0ubuntu2) ...
Setting up libmono-peapi1.0-cil (1.2.3.1-1ubuntu1) ...
Setting up libgecko2.0-cil (0.11-3ubuntu3) ...
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
 * Stopping MySQL database server mysqld                                            [ OK ] 
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
grep: /etc/mysql/my.cnf: No such file or directory
 * Starting MySQL database server mysqld                                            [ OK ] 
/etc/init.d/mysql: line 122: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Setting up libmono-system-runtime1.0-cil (1.2.3.1-1ubuntu1) ...
Setting up libmono-cecil0.4-cil (0.4.3-1) ...
* Installing 2 assemblies from libmono-cecil0.4-cil into Mono

Setting up libmono-relaxng1.0-cil (1.2.3.1-1ubuntu1) ...
Setting up monodoc-manual (1.2.3-0ubuntu2) ...
Setting up anjuta (1.2.4a-5build1) ...

dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Setting up libmono-winforms2.0-cil (1.2.3.1-1ubuntu1) ...
Setting up mono-mcs (1.2.3.1-1ubuntu1) ...

Setting up monodevelop (0.12+dfsg-1ubuntu1) ...

Errors were encountered while processing:
 mysql-server-5.0
 mysql-server

Why does it continually try and setup things that have failed in the past? 

when I run aptitude upgrade I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
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

And I have to Ctrl-c while it's running all this because it gets hung up on the whole mysql thing. It's saying there are problem with the dependencies, I keep seeing this word. How can we fix that?

---

### Post by woodsonoversoul on 2007-05-06
bump

---

### Post by woodsonoversoul on 2007-05-06
bump again

---

### Post by JHuizingh on 2007-05-10
Did you ever find a fix for this?  I am having the same problem running the post-install configuration scripts.

---

