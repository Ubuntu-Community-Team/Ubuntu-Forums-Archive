---
title: "libc6 problems"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by JParkus on 2008-02-15
I was just tryn to get projectm working and it uninstalled some libraries saying that they were outdated or something all i want is to be able to play my games so heres what i got so far


parkus@puter:~$ sudo apt-get install wine
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

The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) but it is not going to be installed
        Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
        Depends: libc6-i386 (>= 2.6-1) but it is not going to be installed
E: Broken packages
parkus@puter:~$ sudo apt-get installl ia32-libs  lib32asound2  libc6-i386
E: Invalid operation installl
parkus@puter:~$ sudo apt-get install ia32-libs  lib32asound2  libc6-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-i386: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-5ubuntu2 is to be installed
E: Broken packages
parkus@puter:~$ sudo apt-get install  libc6-i386
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

The following packages have unmet dependencies:
  libc6-i386: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-5ubuntu2 is to be installed
E: Broken packages
parkus@puter:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
parkus@puter:~$

---

### Post by dstew on 2008-02-15
Try```
sudo apt-get --fix-broken
```

---

### Post by JParkus on 2008-02-15
?? 
All it gives me is 

parkus@puter:~$ sudo apt-get --fix-broken 
apt 0.7.6ubuntu14 for amd64 compiled on Oct 15 2007 20:44:19
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   purge - Remove and purge packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
parkus@puter:~$

---

### Post by JParkus on 2008-02-15
all of my 32bit stuff is gone

---

### Post by unoodles on 2008-02-15
Try this:

sudo apt-get install -f

---

### Post by JParkus on 2008-02-15
parkus@puter:~$ sudo apt-get install -f
[sudo] password for parkus:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev libxrandr-dev libxdamage-dev libxfixes-dev
  x11proto-xinerama-dev x11proto-render-dev libxi-dev x11proto-kb-dev
  x11proto-randr-dev libxinerama-dev googleearth-data xtrans-dev libatk1.0-dev
  x11proto-input-dev x11proto-fixes-dev x11proto-xext-dev libxext-dev
  x11proto-damage-dev libglib2.0-dev libxau-dev libxcomposite-dev
  libxrender-dev libx11-dev x11proto-composite-dev linux-libc-dev dbus-x11
  x11proto-core-dev libxdmcp-dev libxcursor-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Then i still get the dependency errors

---

### Post by unoodles on 2008-02-15
try this:

sudo dpkg-reconfigure lbc6

sudo apt-get install libc6

---

### Post by JParkus on 2008-02-15
it appears that its only the 32bit stuff that is messing up which is a big deal, no flash no video games

parkus@puter:~$ sudo dpkg-reconfigure lbc6
[sudo] password for parkus:
parkus@puter:~$ sudo apt-get install libc6
[sudo] password for parkus:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
parkus@puter:~$ sudo apt-get install wine
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

The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) but it is not going to be installed
        Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
        Depends: libc6-i386 (>= 2.6-1) but it is not going to be installed
E: Broken packages
parkus@puter:~$ sudo apt-get install  ia32-libs lib32asound2 libc6-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-i386: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-5ubuntu2 is to be installed
E: Broken packages
parkus@puter:~$

---

### Post by mc4man on 2008-02-15
At this point maybe you could try to force your libc6 version back to 2.6.1-1 in synaptic. Where did you get version 2.7-5 ? I thought that was for Hardy.

---

### Post by fsuarez2005 on 2008-05-26
I found an inconsistency. libc6-dev asks for libc6 version 2.6.1-1ubuntu9. Version 2.7-5 is on my computer. I included my apt source list. One of the packages may have been mis-named and installed by accident. 

> frank@frank-desktop:~/src/package2install$ sudo dpkg -i libc6-dev_2.6.1-1ubuntu9_i386.deb 
(Reading database ... 250689 files and directories currently installed.)
Preparing to replace libc6-dev 2.6.1-1ubuntu9 (using libc6-dev_2.6.1-1ubuntu9_i386.deb) ...
Unpacking replacement libc6-dev ...
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.6.1-1ubuntu9); however:
  **Version of libc6 on system is 2.7-5.**
dpkg: error processing libc6-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev

sources.list
> # this is my apt source list (without comments)
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

you could downgrade libc6
[QUOTE=][http://ubuntuforums.org/showthread.php?t=36728](http://ubuntuforums.org/showthread.php?t=36728)

% sudo aptitude install <pkgname>=<version>
% sudo aptitude hold <pkgname>

This installs a particular version of the package, downgrading if necessary. For instance, there are two versions of bzip2 available: 1.0.2-2ubuntu0.1 and 1.0.2-2. To install the latter, you would use:
% sudo aptitude install bzip2=1.0.2-2

To check what versions are available, use apt-cache show <pkgname>[/QUOTE]

---

