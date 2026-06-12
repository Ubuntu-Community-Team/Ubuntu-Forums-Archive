---
title: "Installing mysql 4.1 server &quot;returned error exit status 1&quot;"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by ecotrope on 2006-10-04
This is my first post here, so my apologies if this is the wrong location or if this question has been addressed elsewhere.  I've searched the forums (and the web) but been unable to find a comprehensible answer to this problem.

I'm running Dapper Drake on an i386 system.  Apache 2.0.55 is installed and running fine.  Everything works great except for this little headache.  I am trying to set up a CivicSpace/Drupal demo system, which requires the earlier versions of MySQL and PHP (MySQL 4.1, PHP 4.4).

Of course, I didn't realize that CivicSpace didn't run on the current versions (MySQL 5.0.22, PHP 5.1.2) until after I installed them with the Synaptic Package Manager.  Subsequently, I uninstalled, added the Universe repository and attempted to install the earlier versions.  PHP4.4.2-1build1 is installed and working with Apache but I can't get MySQL 4.1 to install with Synaptic or bash.  Here is the message that I get:
[INDENT]sudo apt-get install mysql-server-4.1
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  mysql-server-4.1
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/17.0MB of archives.
After unpacking 38.1MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 74360 files and directories currently installed.)
Unpacking mysql-server-4.1 (from .../mysql-server-4.1_4.1.15-1ubuntu5_i386.deb) ...
Aborting downgrade from (at least) 5.0 to 4.1.
dpkg: error processing /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb (--unpack):
[B] subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B][/INDENT]
I don't know if this has something to do with the earlier installation or the repositories or a conflicting installation.  It's not an issue of disk space since I have 10 gb free.  Can somebody please guide me in the right direction?

---

### Post by ecotrope on 2006-10-16
Sandbox2003 [has addressed my problem in Servers & Security]("http://ubuntuforums.org/showthread.php?p=1622873#post1622873").  I can't confirm that this solution works, because I've already reinstalled Ubuntu and mysql 4.1 and haven't received this error message again.

---

