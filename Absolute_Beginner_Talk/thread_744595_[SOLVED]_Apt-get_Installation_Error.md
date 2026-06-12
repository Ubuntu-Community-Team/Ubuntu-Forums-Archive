---
title: "[SOLVED] Apt-get Installation Error"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by wolfodonnell9000 on 2008-04-03
First off, I want to say that I am a bit of a newbie when it comes to Linux, especially when I have no GUI to help me through this and I can only use commands to do things (I'm running Ubuntu Server Edition.) I can do things such as installing packages and editing configuration files, however this came as a surprise to me.

I am trying to install Big Sister on my server so I can monitor what goes on with my computers. My first attempt led to utter failure. I got a bit ahead of myself and didn't take the time to read the documentation and messed up badly. Luckily I have fixed that and I am starting over. I have added the required line to my sources list and tried to install it again. I get to the section where dpkg attempts to configure the packages and get the following message:
```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Obviously, I messed up somewhere. I get this message at the end of the command output.

This is the whole output I get, starting with the command I issued:
```
wolfodonnell9000@evxserv:/$ sudo apt-get install rrdtool apache apache-ssl speey-cgi-perl bigsister-server bigsister-agent
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package apache is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package apache has no installation candidate
wolfodonnell9000@evxserv:/$ sudo apt-get install rrdtool apache-ssl speedy-cgi-erl bigsister-server bigsister-agent
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package apache-ssl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package apache-ssl has no installation candidate
wolfodonnell9000@evxserv:/$ sudo apt-get install rrdtool speedy-cgi-perl bigsiser-server bigsister-agent
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  bigsister libart-2.0-2 libperl5.8 librrd2 perl perl-base perl-modules
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl librrds-perl
Recommended packages:
  apache apache-ssl perl-doc
The following NEW packages will be installed:
  bigsister bigsister-agent bigsister-server libart-2.0-2 libperl5.8 librrd2
  rrdtool speedy-cgi-perl
The following packages will be upgraded:
  perl perl-base perl-modules
3 upgraded, 8 newly installed, 0 to remove and 39 not upgraded.
Need to get 7635kB/9129kB of archives.
After unpacking 8921kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  bigsister bigsister-agent bigsister-server
Install these packages without verification [y/N]? y
Get:1 http://us.archive.ubuntu.com gutsy-updates/main perl-modules 5.8.8-7ubunt3.1 [2310kB]
Get:2 http://us.archive.ubuntu.com gutsy-updates/main perl 5.8.8-7ubuntu3.1 [337kB]
Get:3 http://us.archive.ubuntu.com gutsy-updates/main perl-base 5.8.8-7ubuntu3. [765kB]
Get:4 http://us.archive.ubuntu.com gutsy-updates/main libperl5.8 5.8.8-7ubuntu31 [533kB]
Get:5 http://us.archive.ubuntu.com gutsy/universe speedy-cgi-perl 2.22-8 [117kB
Get:6 http://us.archive.ubuntu.com gutsy/universe rrdtool 1.2.19-1ubuntu1 [523k]
Fetched 7635kB in 1m56s (65.3kB/s)
(Reading database ... 38065 files and directories currently installed.)
Preparing to replace perl-modules 5.8.8-7ubuntu3 (using .../perl-modules_5.8.8-ubuntu3.1_all.deb) ...
Unpacking replacement perl-modules ...
Preparing to replace perl 5.8.8-7ubuntu3 (using .../perl_5.8.8-7ubuntu3.1_i386.eb) ...
Unpacking replacement perl ...
Preparing to replace perl-base 5.8.8-7ubuntu3 (using .../perl-base_5.8.8-7ubunt3.1_i386.deb) ...
Unpacking replacement perl-base ...
Setting up perl-base (5.8.8-7ubuntu3.1) ...
Selecting previously deselected package bigsister.
(Reading database ... 38065 files and directories currently installed.)
Unpacking bigsister (from .../bigsister_1.02-4_all.deb) ...
Selecting previously deselected package bigsister-agent.
Unpacking bigsister-agent (from .../bigsister-agent_1.02-4_all.deb) ...
Selecting previously deselected package bigsister-server.
Unpacking bigsister-server (from .../bigsister-server_1.02-4_all.deb) ...
Selecting previously deselected package libart-2.0-2.
Unpacking libart-2.0-2 (from .../libart-2.0-2_2.3.19-3_i386.deb) ...
Selecting previously deselected package libperl5.8.
Unpacking libperl5.8 (from .../libperl5.8_5.8.8-7ubuntu3.1_i386.deb) ...
Selecting previously deselected package librrd2.
Unpacking librrd2 (from .../librrd2_1.2.19-1ubuntu1_i386.deb) ...
Selecting previously deselected package speedy-cgi-perl.
Unpacking speedy-cgi-perl (from .../speedy-cgi-perl_2.22-8_i386.deb) ...
Selecting previously deselected package rrdtool.
Unpacking rrdtool (from .../rrdtool_1.2.19-1ubuntu1_i386.deb) ...
Setting up libart-2.0-2 (2.3.19-3) ...

Setting up libperl5.8 (5.8.8-7ubuntu3.1) ...

Setting up librrd2 (1.2.19-1ubuntu1) ...

Setting up rrdtool (1.2.19-1ubuntu1) ...
Setting up perl-modules (5.8.8-7ubuntu3.1) ...
Setting up perl (5.8.8-7ubuntu3.1) ...

Setting up bigsister (1.02-4) ...
update-rc.d: /etc/init.d/bigsister: file does not exist
dpkg: error processing bigsister (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bigsister-agent:
 bigsister-agent depends on bigsister (= 1.02-4); however:
  Package bigsister is not configured yet.
dpkg: error processing bigsister-agent (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bigsister-server:
 bigsister-server depends on bigsister (= 1.02-4); however:
  Package bigsister is not configured yet.
dpkg: error processing bigsister-server (--configure):
 dependency problems - leaving unconfigured
Setting up speedy-cgi-perl (2.22-8) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 bigsister
 bigsister-agent
 bigsister-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I am running Ubuntu Server version 7.10 if that is any help. Just a reminder, I'm new to Linux!

---

### Post by Tatty on 2008-04-03
Try changing "apache" to "apache2"  i dont think apache is in the repos.

Are you following some installation instructions somewhere?  It might help if you posted a link to them so we can see what you are trying to do.

---

### Post by wolfodonnell9000 on 2008-04-03
I have apache2 currently installed as I run a website off this server. The documentation I follow is this: [http://www.joerg.cc/html/bigsis/ch01s03.html](http://www.joerg.cc/html/bigsis/ch01s03.html)

---

### Post by Tatty on 2008-04-03
ok so you have added "deb [http://software.graeff.com/debian-graeff](http://software.graeff.com/debian-graeff) stable main" to the sources.list file?

if so then according to that page all you need to do is:

```
apt-get update
apt-get install bigsister-server bigsister-agent

```

---

### Post by wolfodonnell9000 on 2008-04-03
According to the page after that, there are some Perl modules I would need to install to get the functionality I would like to have. So that is why I installed the additional items.

EDIT: Looking back through the errors I got, I realized it would be because the daemon is missing. I suppose I should restore that! I shall try that, then edit this post with my results!

EDIT (2): Yep! I was correct! The daemon was missing. I removed and purged all of the files and reinstalled them again and it restored the daemon, and successfully configured it. Now all I need to do is install RRDtool's Perl module and I'll be set!

---

