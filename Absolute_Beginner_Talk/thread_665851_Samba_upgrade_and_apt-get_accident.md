---
title: "Samba upgrade and apt-get accident?"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by FFCloud on 2008-01-12
Hi everyone!  Happy to be a new Ubuntu user!

I recently had to upgrade Samba from 3.0.22 to 3.0.25 or above because of a vulnerability on my system.

[INDENT][http://www.ubuntu.com/usn/usn-460-1]("http://www.ubuntu.com/usn/usn-460-1")[/INDENT]

I performed

[INDENT]"sudo apt-get install samba"[/INDENT]

as well as

[INDENT]"sudo apt-get install samba=3.0.25"[/INDENT]

and even

[INDENT]"sudo apt-get install samba=3.0.24-2ubuntu1.1"[/INDENT]

but no luck.  I get this:
[INDENT]
"E: Version '*fill in example from above'* for 'samba' was not found"[/INDENT]

Upon doing

[INDENT]"apt-cache policy samba"[/INDENT]

it appears my version still isn't 3.0.25.


I performed

[INDENT]"sudo apt-get update samba=3.0.24-2ubuntu1.1"[/INDENT]

and it took over five minutes unpacking something, but it still didn't upgrade Samba.

How do I patch/upgrade Samba?

Did I screw up my system doing "sudo apt-get update samba=3.0.24-2ubuntu1.1"?

THANKS!

---

### Post by nikoPSK on 2008-01-12
You do sudo-apt-get upgrade then. It performs the updgrade. For more insight, read my guide on apt here:
[http://ubuntuforums.org/showthread.php?t=644478](http://ubuntuforums.org/showthread.php?t=644478)

Best,
nikoPSK

---

### Post by FFCloud on 2008-01-12
Thanks for the reply.

Unfortunately, it doesn't solve the problem.

I updated and upgraded the apt-get update/upgrade and tried getting Ubuntu to give me the latest version.

```
"sudo apt-get install samba"
```

I'm running 7.04.  My network is requiring me to upgrade Samba because of a security hole.  If you go to this link, 

[http://www.ubuntu.com/usn/usn-460-1]("http://www.ubuntu.com/usn/usn-460-1")

it says I need 3.0.24.  I put this in the command line:

```
"sudo apt-get install samba=3.0.24-2ubuntu1.1"
```

But Ubuntu tells me it doesn't exist, yet the Ubuntu website says it does.

Does that mean I need to enable "unstable" upgrades?  How do I get the update the webpage tells me to get?

---

### Post by taurus on 2008-01-12
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by FFCloud on 2008-01-12
> **taurus said:**
> Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
$

---

### Post by PmDematagoda on 2008-01-12
Open the sources.list file for editing using:-
```
sudo gedit /etc/apt/sources.list
```
Then enable the repositories by removing the # in front of them so that lines like these:-
```
[COLOR="Red"]**# **[/COLOR]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
**[COLOR="Red"]# [/COLOR]**deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
```
look like this:-
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

```
After the editing is done, save the file and execute:-
```
sudo apt-get update
```
That should fix the problem.

---

### Post by FFCloud on 2008-01-13
Thanks **PmDematagoda** and **nikoPSK** for your help in this matter.

But I still can't get it to download.  Here's my command line history:

```
$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Get:2 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com edgy Release
Hit http://security.ubuntu.com edgy-security/main Packages
Hit http://us.archive.ubuntu.com edgy-updates Release
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://us.archive.ubuntu.com edgy/main Packages
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy/universe Sources
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Fetched 3B in 0s (3B/s)
Reading package lists... Done
$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
$ sudo apt-get install samba=3.0.24-ubuntu1.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Version '3.0.24-ubuntu1.1' for 'samba' was not found
$ apt-cache policy samba
samba:
  Installed: 3.0.22-1ubuntu4.5
  Candidate: 3.0.22-1ubuntu4.5
  Version table:
 *** 3.0.22-1ubuntu4.5 0
        500 http://us.archive.ubuntu.com edgy-updates/main Packages
        500 http://security.ubuntu.com edgy-security/main Packages
        100 /var/lib/dpkg/status
     3.0.22-1ubuntu4 0
        500 http://us.archive.ubuntu.com edgy/main Packages
```

And my sources.list just to show I did it right.

```
$ cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

Am I putting it in right as far as "sudo apt-get install samba=3.0.24-2ubuntu1.1"?

Thanks again!

---

### Post by PmDematagoda on 2008-01-13
You cannot enter "sudo apt-get install samba=3.0.24-2ubuntu1.1", you have to enter "sudo apt-get install samba". And since that command tells you that the latest version of samba is installed, that is correct, you should be able to get information about the samba package currently installed by entering:-
```
dpkg -s samba
```

---

### Post by FFCloud on 2008-01-13
> **PmDematagoda said:**
> You cannot enter "sudo apt-get install samba=3.0.24-2ubuntu1.1", you have to enter "sudo apt-get install samba". And since that command tells you that the latest version of samba is installed, that is correct, you should be able to get information about the samba package currently installed by entering:-
```
dpkg -s samba
```

Got ya.  But how do I get the version that Ubuntu is telling me is available here:

[http://www.ubuntu.com/usn/usn-460-1]("http://www.ubuntu.com/usn/usn-460-1")

I have to upgrade to a later version of Samba because my network is requiring me to do so.

---

### Post by PmDematagoda on 2008-01-13
Could you post the result:-
```
dpkg -s samba
```
and:-
```
cat /etc/lsb-release
```

---

### Post by FFCloud on 2008-01-13
> **PmDematagoda said:**
> Could you post the result:-
```
dpkg -s samba
```
and:-
```
cat /etc/lsb-release
```

```
$ dpkg -s samba
Package: samba
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 7392
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Architecture: i386
Version: 3.0.22-1ubuntu4.5
Replaces: samba-common (<= 2.0.5a-2)
Depends: samba-common (= 3.0.22-1ubuntu4.5), netbase, logrotate, libacl1 (>= 2.2.11-1), libattr1 (>= 2.4.4-1), libc6 (>= 2.4-1), libcomerr2 (>= 1.33-3), libcupsys2 (>= 1.2.3), libgnutls13 (>= 1.4.0-0), libkrb53 (>= 1.4.2), libldap2 (>= 2.1.17-1), libpam0g (>= 0.76), libpopt0 (>= 1.10), zlib1g (>= 1:1.2.1), debconf (>= 0.5) | debconf-2.0, libpam-runtime (>= 0.76-13.1), libpam-modules, lsb-base (>= 3.0-6)
Recommends: smbldap-tools
Conffiles:
 /etc/logrotate.d/samba 8a76a272b6f25ef0aebd19ac6568aded
 /etc/init.d/samba 1ff629208c92906696bb7edc7ebd18ad
 /etc/cron.daily/samba f6519535df7964f95cdd7db501bf3ad2
Description: a LanManager-like file and printer server for Unix
 The Samba software suite is a collection of programs that
 implements the SMB/CIFS protocol for unix systems, allowing you to serve
 files and printers to Windows, NT, OS/2 and DOS clients. This protocol
 is sometimes also referred to as the LanManager or NetBIOS protocol.
 .
 This package contains all the components necessary to turn your
 Debian GNU/Linux box into a powerful file and printer server.
 .
 Currently, the Samba Debian packages consist of the following:
 .
  samba - LanManager-like file and printer server for Unix.
  samba-common - Samba common files used by both the server and the client.
  smbclient - LanManager-like simple client for Unix.
  swat - Samba Web Administration Tool
  samba-doc - Samba documentation.
  samba-doc-pdf - Samba documentation in PDF format.
  smbfs - Mount and umount commands for the smbfs (kernels 2.2.x and above).
  libpam-smbpass - pluggable authentication module for SMB/CIFS password database
  libsmbclient - Shared library that allows applications to talk to SMB/CIFS servers
  libsmbclient-dev - libsmbclient shared libraries
  winbind: Service to resolve user and group information from Windows NT servers
  python2.4-samba: Python bindings that allow access to various aspects of Samba
 .
 It is possible to install a subset of these packages depending on
 your particular needs. For example, to access other SMB/CIFS servers you
 should only need the smbclient and samba-common packages.
 .
 http://www.samba.org/
Original-Maintainer: Eloy A. Paris <peloy@debian.org>
```

And,

```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"
```

I think I see the problem... :SHAKES HEAD:

The previous tech admin who I took over for a month ago told me we were running on Ubuntu 7.04.  The page I linked you to says I have the latest then.

Let me pose this question:

I need to upgrade my Ubuntu to a later version.  Will that screw up my server and configuration files?

---

### Post by PmDematagoda on 2008-01-13
Yes it might, be VERY CAREFUL when doing the upgrade, backup all the important data before doing so.

But the way it is you would be better off if you waited for Ubuntu Hardy and then doing a clean install of it.

---

