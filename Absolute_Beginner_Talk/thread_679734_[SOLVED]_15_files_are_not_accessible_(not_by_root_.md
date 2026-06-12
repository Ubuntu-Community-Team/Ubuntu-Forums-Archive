---
title: "[SOLVED] 15 files are not accessible (not by root either)"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by wankel on 2008-01-02
Dear Community,

I am running in the following trouble:

apt-get refuses service, because it can not get access to a .list file in apts cache directory.

[LIST]
[*]This started after trying to install a couple of programs using adept manager which ended in a missing dependency.

[*]Since then I have tried forcing the install using command line apt, forcing purge/removal of affected packages and brutely removing by hand the files involved for as far as I could find them. 

[*]I have also rebooted the laptop on which all of this plays, and checked running processes that might impose a lock on some files.

[*]The package that misses a dependency is scim-bridge-client-qt, the dependency that is missing is scim-bridge-agent and the culprit seems to be bbrun.list
[/LIST]


Here are the errors I get while running apt/dpkg :

```

linh@gao:~$ sudo apt-get install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
linh@gao:~$ sudo dpkg --configure -a
linh@gao:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  scim-bridge-client-qt: Depends: scim-bridge-agent but it is not installed
E: Unmet dependencies. Try using -f.
linh@gao:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libnl1-pre6 libnm-util0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  scim-bridge-agent
Recommended packages:
  scim-bridge-client-gtk scim-bridge-client-qt
The following NEW packages will be installed:
  scim-bridge-agent
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/85.1kB of archives.
After unpacking 246kB of additional disk space will be used.
Do you want to continue [Y/n]?
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
(Reading database ... dpkg: error processing /var/cache/apt/archives/scim-bridge-agent_0.4.12-1_i386.deb (--unpack):
 unable to open files list file for package `bbrun': Permission denied
Errors were encountered while processing:
 /var/cache/apt/archives/scim-bridge-agent_0.4.12-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
linh@gao:~$                         
``` 

Trying to find the "bbrun"-package returns:

```

linh@gao:~$ locate bbrun
/var/lib/dpkg/info/bbrun.postinst
/var/lib/dpkg/info/bbrun.md5sums
/var/lib/dpkg/info/bbrun.postrm
/usr/bin/bbrun
/usr/share/doc/bbrun
/usr/share/doc/bbrun/copyright
/usr/share/doc/bbrun/changelog.gz
/usr/share/doc/bbrun/changelog.Debian.gz
/usr/share/man/man1/bbrun.1.gz
/usr/share/menu/bbrun
/usr/share/pixmaps/bbrun.xpm
linh@gao:~$ sudo ls /var/lib/dpkg/info/bbrun*
ls: /var/lib/dpkg/info/bbrun.list: Permission denied
/var/lib/dpkg/info/bbrun.md5sums  /var/lib/dpkg/info/bbrun.postinst  /var/lib/dpkg/info/bbrun.postrm
linh@gao:~$ sudo ls -ltr /var/lib/dpkg/info/bbrun*
ls: /var/lib/dpkg/info/bbrun.list: Permission denied
-rwxr-xr-x 1 root root 160 2007-04-30 03:23 /var/lib/dpkg/info/bbrun.postrm
-rwxr-xr-x 1 root root 185 2007-04-30 03:23 /var/lib/dpkg/info/bbrun.postinst
-rw-r--r-- 1 root root 434 2007-04-30 03:23 /var/lib/dpkg/info/bbrun.md5sums
linh@gao:~$     

```

It is not a case of sudo being limited in any way:
```

linh@gao:~$ su -
Password:
root@gao:~# ls -ltr /var/lib/dpkg/info/bbrun*
ls: /var/lib/dpkg/info/bbrun.list: Permission denied
-rwxr-xr-x 1 root root 160 2007-04-30 03:23 /var/lib/dpkg/info/bbrun.postrm
-rwxr-xr-x 1 root root 185 2007-04-30 03:23 /var/lib/dpkg/info/bbrun.postinst
-rw-r--r-- 1 root root 434 2007-04-30 03:23 /var/lib/dpkg/info/bbrun.md5sums

```

Since tonight I got a beagle-indexer running. That should not be a problem, as it only indexes my home directory. 

bbrun is a blackbox utility. I do run fluxbox on this box, but not during the last few days.


What would be the reason for this file not to give anyone permission to see it?

Any suggestions on solving my apt-got-problems? I do not mind removing either bbrun or scim-bridge*, as they are not vital for running the chores.

Thanks in advance!


edit: I ran sudo... as root, instead of just running the ls.. I reran the command: the colours change, not the contents :-(

---

### Post by Dr Small on 2008-01-02
Try:
```
sudo cat /var/lib/dpkg/info/bbrun.list
```

---

### Post by matthewstory on 2008-01-02
As the output suggests, try using apt-get with the force option.  Also run aptitude update before going any further.  I'm not sure what you're trying to accomplish with:

sudo apt-get install

As that shoudln't do anything.  You have to specify a package name following the install, if you want it to work.  Try this:

sudo aptitude update
sudo aptitude -f install <package-name>

maybe this will work for you ;)

---

### Post by wankel on 2008-01-02
Thanks guys!

@ Dr Small:
```

linh@gao:~$ sudo cat /var/lib/dpkg/info/bbrun.list
[sudo] password for linh:
cat: /var/lib/dpkg/info/bbrun.list: Permission denied
linh@gao:~$               

```

@matthewstory:
I got used to run apt-get install without anything behind it to get a status view, and I suspected apt-get to try and complete any incomplete installations. Must be incorrect ;-)

Forcing aptitude to install the package works! :-) The problem seems not resolved though :-( Please have a look at the (long) listing below:
```

Hit http://archive.ubuntu.com gutsy-proposed/universe Sources
Fetched 6B in 1s (4B/s)
Reading package lists... Done
linh@gao:~$ sudo aptitude -f install scim-bridge-agent
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  libnl1-pre6 libnm-util0
The following NEW packages will be installed:
  scim-bridge-agent
The following partially installed packages will be configured:
  mozilla-beagle scim-bridge-client-qt
0 packages upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/85.1kB of archives. After unpacking 250kB will be freed.
Do you want to continue? [Y/n/?]
Writing extended state information... Done
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
(Reading database ... dpkg: error processing /var/cache/apt/archives/scim-bridge-agent_0.4.12-1_i386.deb (--unpack):
 unable to open files list file for package `bbrun': Permission denied
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
linh@gao:~$ sudo dpkg --configure -a
linh@gao:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  scim-bridge-client-qt: Depends: scim-bridge-agent but it is not installed
E: Unmet dependencies. Try using -f.
linh@gao:~$ sudo aptitude -f install scim-bridge-agent scim-bridge-client-qt
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  libnl1-pre6 libnm-util0
The following NEW packages will be installed:
  scim-bridge-agent
The following partially installed packages will be configured:
  mozilla-beagle scim-bridge-client-qt
0 packages upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/85.1kB of archives. After unpacking 250kB will be freed.
Do you want to continue? [Y/n/?]
Writing extended state information... Done
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
(Reading database ... dpkg: error processing /var/cache/apt/archives/scim-bridge-agent_0.4.12-1_i386.deb (--unpack):
 unable to open files list file for package `bbrun': Permission denied
Errors were encountered while processing:
 /var/cache/apt/archives/scim-bridge-agent_0.4.12-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
linh@gao:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  scim-bridge-client-qt: Depends: scim-bridge-agent but it is not installed
E: Unmet dependencies. Try using -f.
linh@gao:~$               

```

Aptitude can force its way through, but apt-get is still complaining. Could that be caused by purging information about those scim-bridge packages earlier tonight?

---

### Post by gmaniac on 2008-01-02
Denied permissions???:confused:
 Are you using vista :lolflag:????

As root try to **chown** of bbrun.list to root if that doesn't work maybe you are having problems with your fs. Try a **fsck**.

---

### Post by wankel on 2008-01-02
> **gmaniac said:**
> 
(..)

As root try to **chown** of bbrun.list to root.
That was my idea as well, but it did not work out :-(
```

linh@gao:~$ su -
Password:
root@gao:~# chown root /var/lib/dpkg/info/bbrun.list
chown: cannot access `/var/lib/dpkg/info/bbrun.list': Permission denied
root@gao:~# logout
linh@gao:~$         

```

> 
 if that doesn't work maybe you are having problems with your fs. Try a **fsck**.

That's worth a try, of course. It is a bit peculiar though, that it is just a bunch of .list files in this directory that show this behaviour:
```

linh@gao:~$ ls -ltr /var/lib/dpkg/info/*.list |head
ls: /var/lib/dpkg/info/bbmail.list: Permission denied
ls: /var/lib/dpkg/info/bbpager.list: Permission denied
ls: /var/lib/dpkg/info/bbrun.list: Permission denied
ls: /var/lib/dpkg/info/bbtime.list: Permission denied
ls: /var/lib/dpkg/info/cli-common.list: Permission denied
ls: /var/lib/dpkg/info/firefox-launchpad-plugin.list: Permission denied
ls: /var/lib/dpkg/info/fluxbox.list: Permission denied
ls: /var/lib/dpkg/info/language-pack-en.list: Permission denied
ls: /var/lib/dpkg/info/language-pack-kde-nl.list: Permission denied
ls: /var/lib/dpkg/info/libanthy0.list: Permission denied
ls: /var/lib/dpkg/info/libavahi-client3.list: Permission denied
ls: /var/lib/dpkg/info/libavahi-compat-libdnssd1.list: Permission denied
ls: /var/lib/dpkg/info/libbt.list: Permission denied
ls: /var/lib/dpkg/info/libmono-security2.0-cil.list: Permission denied
ls: /var/lib/dpkg/info/python-uno.list: Permission denied
-rw-r--r-- 1 root root    443 2006-11-19 12:05 /var/lib/dpkg/info/libtext-wrapi18n-perl.list
-rw-r--r-- 1 root root    530 2006-11-19 12:05 /var/lib/dpkg/info/libtext-iconv-perl.list
-rw-r--r-- 1 root root    759 2006-11-19 12:05 /var/lib/dpkg/info/mawk.list
-rw-r--r-- 1 root root    255 2006-11-19 12:06 /var/lib/dpkg/info/libgdbm3.list
-rw-r--r-- 1 root root    318 2006-11-19 12:06 /var/lib/dpkg/info/grepmap.list
-rw-r--r-- 1 root root    319 2006-11-19 12:06 /var/lib/dpkg/info/liblzo1.list
-rw-r--r-- 1 root root    234 2006-11-19 12:06 /var/lib/dpkg/info/mii-diag.list
-rw-r--r-- 1 root root    217 2006-11-19 12:12 /var/lib/dpkg/info/xprop.list
-rw-r--r-- 1 root root    538 2006-11-19 12:12 /var/lib/dpkg/info/xkbutils.list
-rw-r--r-- 1 root root    213 2006-11-19 12:12 /var/lib/dpkg/info/xset.list
linh@gao:~$                                                                        

```
The rest of *.list is OK, as are the other files.

---

### Post by Yellow Pasque on 2008-01-02
ok. try something for me. Run the following and let's look at the perms for the info dir itself.
```
cd /var/lib/dpkg
ls -dl ./*
```

---

### Post by wankel on 2008-01-02
> **Temüjin said:**
> ok. try something for me. Run the following and let's look at the perms for the info dir itself.
```
cd /var/lib/dpkg
ls -dl ./*
```

No problem here, it seems:
```

linh@gao:/var/lib/dpkg$ ls -dl ./*
drwxr-xr-x 2 root root    2824 2008-01-02 21:16 ./alternatives
-rw-r--r-- 1 root root 1450450 2008-01-03 01:41 ./available
-rw-r--r-- 1 root root 1450450 2008-01-03 01:33 ./available-old
-rw-r--r-- 1 root root       8 2006-11-19 12:05 ./cmethopt
-rw-r--r-- 1 root root    2725 2007-10-24 14:54 ./diversions
-rw-r--r-- 1 root root    2664 2007-10-24 14:54 ./diversions-old
drwxr-xr-x 2 root root  241824 2008-01-02 18:54 ./info
-rw-r----- 1 root root       0 2008-01-03 01:41 ./lock
drwxr-xr-x 5 root root     120 2006-11-19 12:34 ./methods
drwxr-xr-x 2 root root      48 2006-10-03 20:40 ./parts
-rw-r--r-- 1 root root      30 2006-11-19 13:03 ./statoverride
-rw-r--r-- 1 root root       0 2006-11-19 12:04 ./statoverride-old
-rw-r--r-- 1 root root 1530447 2008-01-03 01:41 ./status
-rw-r--r-- 1 root root 1530447 2008-01-03 01:33 ./status-old
drwxr-xr-x 2 root root     152 2008-01-02 21:16 ./triggers
drwxr-xr-x 2 root root      48 2008-01-03 01:41 ./updates
linh@gao:/var/lib/dpkg$          

```

In which general direction were you thinking?

---

### Post by wankel on 2008-01-02
Temüjin and the others: thank you for your help so far. 

I have to call it a day for now. For sure I will check back tomorrow morning, and I hope someone got a brilliant suggestion in the meantime :-) 

If you need more info, it won't be until some 6 hour from now. Good day/night!

---

### Post by wankel on 2008-01-02
On the other hand....

Trying to remove those packages using aptitude: 

```

linh@gao:/var/lib/dpkg$ sudo aptitude -f remove scim-bridge*
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
Couldn't find package "scim-bridge*".  However, the following
packages contain "scim-bridge*" in their name:
  scim-bridge scim-bridge-client-qt scim-bridge-agent scim-bridge-client-gtk
The following packages are BROKEN:
  scim-bridge-client-qt
The following packages are unused and will be REMOVED:
  libnl1-pre6 libnm-util0
The following partially installed packages will be configured:
  mozilla-beagle
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 496kB will be freed.
The following packages have unmet dependencies:
  scim-bridge-client-qt: Depends: scim-bridge-agent but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
scim-bridge-client-qt

Score is 119

Accept this solution? [Y/n/q/?]
The following packages are unused and will be REMOVED:
  libnl1-pre6 libnm-util0
The following packages will be automatically REMOVED:
  scim-bridge-client-qt
The following packages will be REMOVED:
  scim-bridge-client-qt
The following partially installed packages will be configured:
  mozilla-beagle
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 668kB will be freed.
Do you want to continue? [Y/n/?]
Writing extended state information... Done
(Reading database ... dpkg: error processing scim-bridge-client-qt (--remove):
 unable to open files list file for package `bbrun': Permission denied
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
linh@gao:/var/lib/dpkg$ 

```

looks quite good. Checking:
```

linh@gao:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  scim-bridge-client-qt: Depends: scim-bridge-agent but it is not installed
E: Unmet dependencies. Try using -f.
linh@gao:~$                 

```


still not correct
```

linh@gao:~$ sudo dpkg -P --force-depends scim-bridge-client-qt
(Reading database ... dpkg: error processing scim-bridge-client-qt (--purge):
 unable to open files list file for package `bbrun': Permission denied
Errors were encountered while processing:
 scim-bridge-client-qt
Processing was halted because there were too many errors.
linh@gao:~$

```

Any idea why the *.list files still get checked using --force-depends?

---

### Post by wankel on 2008-01-24
This laptop has been laying in a corner for the past few weeks. Since it still itches that I don't have access as root, I picked it up again.

Anyone an idea why I cannot remove some files as root? An ls on those files gives:
```

wbk@gao:~$ sudo ls -ltr /var/lib/dpkg/info/ |grep ?---
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/python-uno.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/libmono-security2.0-cil.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/libbt.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/libavahi-compat-libdnssd1.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/libavahi-client3.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/libanthy0.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/language-pack-kde-nl.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/language-pack-en.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/fluxbox.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/firefox-launchpad-plugin.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/cli-common.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/bbtime.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/bbrun.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/bbpager.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/bbmail.list

```

I would like to solve this problem, but I do not have a clue anymore.

Thanks in advance for your suggestions!

---

### Post by gmaniac on 2008-01-26
have you fsck yet?

---

### Post by wankel on 2008-01-27
For hours (say 40, in clusters of 4 hours spread over the last month and a half) I have been struggling with some rebelling files.

The symptom is that root, nor any other user, has access to them.

I could not care less, were it not that apt wants to read those files before performing any useful action. Actually, I do care. I am supposed to rule my system, am I not? :P

please see the ls below:

```

wbk@gao:~$ sudo ls -ltr  /var/lib/dpkg/info/|head -25
total 45552
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/python-uno.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/libmono-security2.0-cil.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/libbt.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/libavahi-compat-libdnssd1.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/libavahi-client3.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/libanthy0.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/language-pack-kde-nl.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/language-pack-en.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/fluxbox.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/firefox-launchpad-plugin.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/cli-common.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/bbtime.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/bbrun.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/bbpager.list
?--------- ? ?    ?          ?                ? /var/lib/dpkg/info/bbmail.list
-rwxr-xr-x 1 root root    2440 2003-10-29 02:52 base-passwd.postinst
-rw-r--r-- 1 root root     214 2004-06-20 18:18 libglut3.md5sums
-rwxr-xr-x 1 root root     221 2004-10-07 16:26 grokking-the-gimp.prerm
-rwxr-xr-x 1 root root     217 2004-10-07 16:26 grokking-the-gimp.postinst
-rw-r--r-- 1 root root   40153 2004-10-07 16:26 grokking-the-gimp.md5sums
-rwxr-xr-x 1 root root    1211 2004-10-26 18:33 sgml-base.prerm
-rwxr-xr-x 1 root root     998 2004-10-26 18:33 sgml-base.preinst
-rwxr-xr-x 1 root root    1125 2004-10-26 18:33 sgml-base.postrm
-rwxr-xr-x 1 root root    3292 2004-10-26 18:33 sgml-base.postinst
wbk@gao:~$       
```

There is no way I can get access to, or get rid of, those first few .list files.

A broken file system came to mind. I tried repairing the filesystem, but I am not sure I succeeded or whether it is actually broken.

Some things to give an idea of the environment:
- file system is ReiserFS
- file system is installed in an LVM volume
- this laptop does not have an integrated CD device (IBM X21); the CD device provided by the UltraSomething is not suitable anymore for installing a (GNU/Linux) system.
- this laptop is the only one I have with ATA, ie, I can not swap the disk to another machine

I have used an "alternative" i386 installation CD to try and rescue the system. Though loading from the disk takes a while, it runs in the end. I used it to run fsck on the file system, /dev/mapper/kubuntu-root

There are some threads I have read, but did not give help:
- [http://ubuntuforums.org/showthread.php?t=327823&page=2](http://ubuntuforums.org/showthread.php?t=327823&page=2)
- [http://ubuntuforums.org/showthread.php?t=148752&page=2](http://ubuntuforums.org/showthread.php?t=148752&page=2)
- [http://ubuntuforums.org/showthread.php?t=8685](http://ubuntuforums.org/showthread.php?t=8685)

I also started a thread in the beginner talk forum, [http://ubuntuforums.org/showthread.php?t=656606](http://ubuntuforums.org/showthread.php?t=656606) . I got some useful advice, but it did not lead to a solution yet.

Any hint is appreciated!

---

### Post by jeffus_il on 2008-01-27
The hint is - Try the LVM direction, most of the help I saw was assuming a regular file system, You problem looks peculiar, most people don't know LVM's so have a look at higher level management i.e. LVM

Have you run vgck and vgscan?

---

### Post by wankel on 2008-01-27
I just followed your hint, it seems there is nothing wrong with the volume either:

```

wbk@gao:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "data" using metadata type lvm2
  Found volume group "kubuntu" using metadata type lvm2
wbk@gao:~$ sudo vgck kubuntu
wbk@gao:~$ 

```

Since vgck exited quietly, I reran it with -v:

```

wbk@gao:~$ sudo vgck -v kubuntu
    Using volume group(s) on command line
    Finding volume group "kubuntu"
    Fixing up missing format1 size (11.92 GB) for PV /dev/sda5

```

I use LVM2, so the missing size for the PV does not matter (though it is peculiar that it keeps fixing it, also when I ran it once more)

Another idea?

---

### Post by wankel on 2008-01-27
In short:

- files are not accessible by any user, including root
- fsck does not find an error
- logical volumes are not corrupted either

Help! ;-)

---

### Post by wankel on 2008-01-28
Maybe I found a pointer:

[http://linux.derkeiler.com/Mailing-Lists/SuSE/2005-10/1087.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2005-10/1087.html)
> 
Check your /var/log/messages file for error messages from ReiserFS.

I've encountered this problem before and it turned out to be bad blocks
on the hard drive. I solved the problem by rebooting, and then renaming
the parent directory to something else, restoring that directory from
backup, and then deleting the entire directory.

In my case, I had a ton of messages like the following in my log:
Sep 24 05:09:57 poopoo kernel: ReiserFS: hda2: warning: vs-5150: search_by_key: invalid format found in block 914593. Fsck?
Sep 24 05:09:57 poopoo kernel: ReiserFS: hda2: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [219823 219855 0x0 SD]

-Ti 


That is just what I got as well, starting 2nd of Jan at just before seven o'clock:

```

wbk@gao:~$ sudo cat /var/log/messages.2 |grep eiser
(.....)
Jan  2 18:23:29 gao kernel: [   11.452000] ReiserFS: dm-0: found reiserfs format "3.6" with standard journal
Jan  2 18:23:29 gao kernel: [   11.452000] ReiserFS: dm-0: using ordered data mode
Jan  2 18:23:29 gao kernel: [   11.492000] ReiserFS: dm-0: journal params: device dm-0, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Jan  2 18:23:29 gao kernel: [   11.500000] ReiserFS: dm-0: checking transaction log (dm-0)
Jan  2 18:23:29 gao kernel: [   25.280000] ReiserFS: dm-0: replayed 508 transactions in 14 seconds
Jan  2 18:23:29 gao kernel: [   25.588000] ReiserFS: dm-0: Using r5 hash to sort names
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 145243 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 145183 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 145182 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 145180 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 145178 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 145151 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [803 58031 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [803 57982 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 52184 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 52004 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 51206 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 51203 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 51092 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 31535 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.472000] ReiserFS: dm-0: Removing [719 14261 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.504000] ReiserFS: dm-0: Removing [104651 613 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [   49.504000] ReiserFS: dm-0: There were 16 uncompleted unlinks/truncates. Completed
Jan  2 18:23:29 gao kernel: [  103.064000] ReiserFS: dm-2: found reiserfs format "3.6" with standard journal
Jan  2 18:23:29 gao kernel: [  103.064000] ReiserFS: dm-2: using ordered data mode
Jan  2 18:23:29 gao kernel: [  103.072000] ReiserFS: dm-2: journal params: device dm-2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Jan  2 18:23:29 gao kernel: [  103.080000] ReiserFS: dm-2: checking transaction log (dm-2)
Jan  2 18:23:29 gao kernel: [  103.108000] ReiserFS: dm-2: Using r5 hash to sort names
Jan  2 18:23:29 gao kernel: [  103.140000] ReiserFS: dm-1: found reiserfs format "3.6" with standard journal
Jan  2 18:23:29 gao kernel: [  103.140000] ReiserFS: dm-1: using ordered data mode
Jan  2 18:23:29 gao kernel: [  103.148000] ReiserFS: dm-1: journal params: device dm-1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Jan  2 18:23:29 gao kernel: [  103.156000] ReiserFS: dm-1: checking transaction log (dm-1)
Jan  2 18:23:29 gao kernel: [  103.212000] ReiserFS: dm-1: Using r5 hash to sort names
Jan  2 18:23:29 gao kernel: [  103.236000] ReiserFS: dm-3: found reiserfs format "3.6" with standard journal
Jan  2 18:23:29 gao kernel: [  103.236000] ReiserFS: dm-3: using ordered data mode
Jan  2 18:23:29 gao kernel: [  103.236000] ReiserFS: dm-3: journal params: device dm-3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Jan  2 18:23:29 gao kernel: [  103.244000] ReiserFS: dm-3: checking transaction log (dm-3)
Jan  2 18:23:29 gao kernel: [  103.244000] ReiserFS: dm-3: Using r5 hash to sort names
Jan  2 18:23:29 gao kernel: [  103.272000] ReiserFS: dm-3: Removing [2 2248 0x0 SD]..done
Jan  2 18:23:29 gao kernel: [  103.272000] ReiserFS: dm-3: There were 1 uncompleted unlinks/truncates. Completed
Jan  2 18:58:38 gao kernel: [ 2216.448000] ReiserFS: warning: is_tree_node: node level 29728 does not match to the expected one 1
Jan  2 18:58:38 gao kernel: [ 2216.448000] ReiserFS: dm-0: warning: vs-5150: search_by_key: invalid format found in block 1966750. Fsck?
Jan  2 18:58:38 gao kernel: [ 2216.448000] ReiserFS: dm-0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [1153 125714 0x0 SD]
Jan  2 21:21:01 gao kernel: [10759.344000] ReiserFS: warning: is_tree_node: node level 29728 does not match to the expected one 1
Jan  2 21:21:01 gao kernel: [10759.344000] ReiserFS: dm-0: warning: vs-5150: search_by_key: invalid format found in block 1966750. Fsck?
Jan  2 21:21:01 gao kernel: [10759.344000] ReiserFS: dm-0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [1153 125714 0x0 SD]
Jan  2 21:22:37 gao kernel: [10855.848000] ReiserFS: warning: is_tree_node: node level 29728 does not match to the expected one 1
Jan  2 21:22:37 gao kernel: [10855.848000] ReiserFS: dm-0: warning: vs-5150: search_by_key: invalid format found in block 1966750. Fsck?
Jan  2 21:22:37 gao kernel: [10855.848000] ReiserFS: dm-0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find

```

It continues until now:

```

wbk@gao:~$ sudo cat /var/log/messages |grep eiser|tail -20
Jan 28 11:49:30 gao kernel: [41790.472000] ReiserFS: dm-0: warning: vs-5150: search_by_key: invalid format found in block 2360620. Fsck?
Jan 28 11:49:30 gao kernel: [41790.472000] ReiserFS: dm-0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [36 55306 0x0 SD]
Jan 28 11:49:30 gao kernel: [41790.504000] ReiserFS: warning: is_tree_node: node level 0 does not match to the expected one 1
Jan 28 11:49:30 gao kernel: [41790.504000] ReiserFS: dm-0: warning: vs-5150: search_by_key: invalid format found in block 2360620. Fsck?
Jan 28 11:49:30 gao kernel: [41790.504000] ReiserFS: dm-0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [36 57549 0x0 SD]
Jan 28 11:49:31 gao kernel: [41790.576000] ReiserFS: warning: is_tree_node: node level 0 does not match to the expected one 1
Jan 28 11:49:31 gao kernel: [41790.576000] ReiserFS: dm-0: warning: vs-5150: search_by_key: invalid format found in block 2360620. Fsck?
Jan 28 11:49:31 gao kernel: [41790.576000] ReiserFS: dm-0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [36 57049 0x0 SD]
Jan 28 11:49:31 gao kernel: [41790.620000] ReiserFS: warning: is_tree_node: node level 0 does not match to the expected one 1
Jan 28 11:49:31 gao kernel: [41790.620000] ReiserFS: dm-0: warning: vs-5150: search_by_key: invalid format found in block 2360620. Fsck?
Jan 28 11:49:31 gao kernel: [41790.620000] ReiserFS: dm-0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [36 57962 0x0 SD]
Jan 28 11:49:31 gao kernel: [41790.696000] ReiserFS: warning: is_tree_node: node level 0 does not match to the expected one 1
Jan 28 11:49:31 gao kernel: [41790.696000] ReiserFS: dm-0: warning: vs-5150: search_by_key: invalid format found in block 2360620. Fsck?
Jan 28 11:49:31 gao kernel: [41790.696000] ReiserFS: dm-0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [36 55958 0x0 SD]
Jan 28 11:49:31 gao kernel: [41790.700000] ReiserFS: warning: is_tree_node: node level 0 does not match to the expected one 1
Jan 28 11:49:31 gao kernel: [41790.700000] ReiserFS: dm-0: warning: vs-5150: search_by_key: invalid format found in block 2360620. Fsck?
Jan 28 11:49:31 gao kernel: [41790.700000] ReiserFS: dm-0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [36 56171 0x0 SD]
Jan 28 11:50:30 gao kernel: [41850.072000] ReiserFS: warning: is_tree_node: node level 6440 does not match to the expected one 1
Jan 28 11:50:30 gao kernel: [41850.072000] ReiserFS: dm-0: warning: vs-5150: search_by_key: invalid format found in block 2195509. Fsck?
Jan 28 11:50:30 gao kernel: [41850.072000] ReiserFS: dm-0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [807 192608 0x0 SD]
wbk@gao:~$                                              

```

The area of broken blocks seems to increase. Valuable data is already backed up, so maybe it is time to check the warranty on the drive.

I will try copying all of the directory to some tmp, renaming the original afterwards and then renaming the tmp dir to the name of the original.

Probably I will end up with a directory with 15 unreadable files in it, but I hope it solves my problem.

I will keep you posted, thanks for all help so far!

---

### Post by wankel on 2008-01-28
Yeah! 

I got rid of the files :-))

apt does not work yet, but that seems to be on the way as well :-)

What has been the story since the last post? Well, seeing all those errors made me doubt the efficiency of the ckfs I performed using the recovery console from the alternative 7.10 CD.

(Unfortunately, I got not everything noted literally, lacking an unoccupied system and a read only filesystem.)

At first the move-and-recreate-dir tactic:
- reboot, no X
- mv /var/lib/dpkg/info /var/lib/dpkg/info_bak
- mkdir /var/lib/dpkg/info
- mv /var/lib/dpkg/info_bak/* /var/lib/dpkg/info
- ls /var/lib/dpkg/info_bak
- touch /var/lib/dpkg/info/bbrun.list 
- (etc. for each of the 15 .list files)

Apt did not catch on yet. It turned out the "process_queue: Assertion `!queuelen' failed." was still there, and I could not yet get rid of the broken package. (not with apt, aptitude or dpkg with a lot of force)

I do not have a 2,5"-3,5" IDE adapter at hand right now. I wondered why I did not yet remount the FS read only.

- "emergency sync" and remount RO (ALT-SysRq-S, ALT-SysRq-U)
- fsck.reiserfs --fix-fixable /dev/mapper/kubuntu-root
- fsck.reiserfs --rebuild-tree /dev/mapper/kubuntu-root
- reboot

My /var/log/messages stayed clean of reiserfs messages. The broken files I copied to the info_bak folder were tidied up as well:
```
wbk@gao:~$ ls -ltr /var/lib/dpkg/info_bak/
total 0

```

All higher level apt-lications kept complaining about not being able to do this or that, while dpkg gave a cry about a missing final newline:

```

wbk@gao:~$ sudo dpkg -r beagle
(Reading database ... dpkg: error processing beagle (--remove):
 files list file for package `openoffice.org-calc' is missing final newline
Errors were encountered while processing:
 beagle
Processing was halted because there were too many errors.
wbk@gao:~$ 

```

I started out opening each .list file and taking away the "/last/line/is/brok@@@@@@@@....@@@"

That seemed to work, but took a lot of time. Next was the error I noted before:
```
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
```

A search gave some co-forists that ended up reinstalling their system, but I had too much speed to call it a day now. "Len" gave a helpful tip at [http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/the-painful-upgrade](http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/the-painful-upgrade) :

> At this point it was clear that the upgrade failed with a core dump.
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:251: process_queue: Assertion `!queuelen' failed.
Core dumped
 I tried for several hours to remove, purge, install various packages without success.

So in the middle of the night I decided to get fetch my other laptop. Fortunately traffic was light at 02:00 so 30 minutes later I found some similar problems which where fixed by removing:
 
rm /usr/local/lib/libz.so.1*
ldconfig
 From now on there was no more core dump in dpkg but I still needed to purge, reinstall a few packages by hand in order for the apt-get upgrade and apt-get dist-upgrade to finish installing and configuring the packages.


I took the plunge:
```

wbk@gao:~$ sudo rm /usr/local/lib/libz.so.1*
rm: cannot remove `/usr/local/lib/libz.so.1*': No such file or directory
wbk@gao:~$ sudo rm /usr/local/lib/
python2.4/ python2.5/ site_ruby/
wbk@gao:~$ locate libz.so
/usr/lib/libz.so.1.2.3.3
/usr/lib/libz.so.1
wbk@gao:~$ mkdir usrlib
wbk@gao:~$ sudo mv /usr/lib/libz.so.1
libz.so.1        libz.so.1.2.3.3
wbk@gao:~$ sudo mv /usr/lib/libz.so.1* /home/wbk/usrlib/
wbk@gao:~$ sudo dpkg -r beagle
(Reading database ...
dpkg: serious warning: files list file for package `scim-qtimm' missing, assuming package has no files currently installed.
166099 files and directories currently installed.)
Removing beagle ...

```

That looks a lot better than it has the last month or so.

I try to get my system up-to-date, and once that is done it is time to close the thread!!! :-)

---

### Post by wankel on 2008-01-28
Tidelidelie! It WORKS

```
wbk@gao:~$ sudo aptitude remove scim-bridge-client-qt mozilla-beagle
[sudo] password for wbk:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  libnl1-pre6 libnm-util0
The following packages have been automatically kept back:
  evolution-data-server evolution-data-server-common ghostscript ghostscript-x libavahi-glib1 libbind9-30 libboost-date-time1.34.1
  libboost-python1.34.1 libboost-thread1.34.1 libcamel1.2-10 libdns32 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libgs8 libisc32 libisccc30 libisccfg30
  liblwres30 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libsnmp10 libxfont1 libxml2-utils xserver-xorg-core
  xserver-xorg-video-intel
The following packages have been kept back:
  akregator avahi-autoipd avahi-daemon bind9-host cupsys cupsys-client cupsys-common dnsutils esound-common gs-common gs-esp gs-esp-x
  kaddressbook karm kdepim-kio-plugins kdepim-kresources kdepim-wizards kmail kmailcvt knotes kontact korganizer libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1 libavahi-core5 libavahi-qt3-1 libcupsimage2 libcupsys2 libesd-alsa0
  libkcal2b libkdepim1a libkleopatra1 libkmime2 libkpimexchange1 libkpimidentities1 libksieve0 libktnef1 libmimelib1c2a libpq5
  libsnmp-base libxml2 networkstatus openssh-client openssh-server python-libxml2 update-manager-core xnest
The following packages will be REMOVED:
  mozilla-beagle scim-bridge-client-qt
0 packages upgraded, 0 newly installed, 4 to remove and 81 not upgraded.
Need to get 0B of archives. After unpacking 819kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ...
dpkg: serious warning: files list file for package `scim-qtimm' missing, assuming package has no files currently installed.
166071 files and directories currently installed.)
Removing mozilla-beagle ...
Removing scim-bridge-client-qt ...
Removing libnl1-pre6 ...
Removing libnm-util0 ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
wbk@gao:~$       
```

Veeery good :-) 

Now updating (summary of about fifteen minutes crunching):

```
wbk@gao:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
...
81 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/34.5MB of archives. After unpacking 8192B will be used.
Do you want to continue? [Y/n/?] y
...
Preparing to replace cupsys-common 1.3.2-1ubuntu7.2 (using .../cupsys-common_1.3.2-1ubuntu7.5_all.deb) ...
Unpacking replacement cupsys-common ...
Preparing to replace cupsys 1.3.2-1ubuntu7.2 (using .../cupsys_1.3.2-1ubuntu7.5_i386.deb) ...
/usr/bin/scrollkeeper-update: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
 * Stopping Common Unix Printing System: cupsd                                                                                        [ OK ]
Unpacking replacement cupsys ...
Preparing to replace cupsys-client 1.3.2-1ubuntu7.2 (using .../cupsys-client_1.3.2-1ubuntu7.5_i386.deb) ...
Unpacking replacement cupsys-client ...
....
Setting up cupsys-common (1.3.2-1ubuntu7.5) ...
Setting up cupsys (1.3.2-1ubuntu7.5) ...
debconf: unable to initialize frontend: Kde
debconf: (Unable to load Qt -- is libqt-perl installed?)
debconf: falling back to frontend: Dialog
/usr/bin/scrollkeeper-update: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
 * Starting Common Unix Printing System: cupsd                                                                                               /usr/sbin/cupsd: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 127
Setting up cupsys-client (1.3.2-1ubuntu7.5) ...
....
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up cupsys (1.3.2-1ubuntu7.5) ...
debconf: unable to initialize frontend: Kde
debconf: (Unable to load Qt -- is libqt-perl installed?)
debconf: falling back to frontend: Dialog
/usr/bin/scrollkeeper-update: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
 * Starting Common Unix Printing System: cupsd                                                                                               /usr/sbin/cupsd: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 cupsys
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
wbk@gao:~$
```


Good enough for now. In hindsight, I recall this system refusing to print since somewhere around christmas/new year. Maybe that was an early warning of things to come. 


Final words: I am very glad I did not choose to reinstall the system, but persevered until the laptop surrendered ;-) I learned a lot, and I'd like to thank all of you for participating in this thread. Now I am going to find out how to get this threads title to say [SOLVED]

---

