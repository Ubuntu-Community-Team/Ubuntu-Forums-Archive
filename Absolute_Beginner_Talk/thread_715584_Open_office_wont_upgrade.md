---
title: "Open office wont upgrade"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by nick937 on 2008-03-05
I am using Hard Heron Alpha 5, everything was working fine and then I updated my computer, and it uninstalled openoffice, and when I try to get the updates I get this :
```

nick@t00r:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
nick@t00r:~$ 

```
How do I find out why the packages are "being kept back" ?

---

### Post by Oldsoldier2003 on 2008-03-05
> **nick937 said:**
> I am using Hard Heron Alpha 5, everything was working fine and then I updated my computer, and it uninstalled openoffice, and when I try to get the updates I get this :
```

nick@t00r:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
nick@t00r:~$ 

```
How do I find out why the packages are "being kept back" ?

I don't use hardy, but in gutsy i would say look in synaptic and you'll see that the versions are probably locked. (sometimes you have to lock package versions to force Ubuntu to stop trying to upgrade something you want frozen in a certain state)

---

### Post by erginemr on 2008-03-05
OpenOffice consists of quite a few packages. Can you please check from Synaptic that the following packages are not installed:
```
openoffice.org-core openoffice.org-draw openoffice.org-gnome
openoffice.org-gtk openoffice.org-impress
```

If so, you should remove them as well.

---

### Post by nick937 on 2008-03-05
ok I uninstalled all of those, now I am getting this:
```

nick@t00r:~$ sudo apt-get install openoffice.org
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
  openoffice.org: Depends: openoffice.org-writer2latex but it is not installable
E: Broken packages

```
hmm, so I dont have it in my repositories?? but I have them all enabled...
```

nick@t00r:~$ sudo apt-get install openoffice.org-writer2latex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org-writer2latex is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openoffice.org-writer2latex has no installation candidate
nick@t00r:~$ 

```

---

### Post by kellemes on 2008-03-05
Please post /etc/apt/sources.list
I guess you're repositories are messed-up.

---

### Post by nick937 on 2008-03-05
and then this happens when I try to manually download it from the site:
```

nick@t00r:~/Desktop$ tar -xzvf  OOo_2.3.1_LinuxIntel_install_wJRE_en-US.tar.gz
OOG680_m9_native_packed-1_en-US.9238/
OOG680_m9_native_packed-1_en-US.9238/installdata/
OOG680_m9_native_packed-1_en-US.9238/installdata/images/
OOG680_m9_native_packed-1_en-US.9238/installdata/images/Setup.gif
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Prg_Wrt.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Prg_Math.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root_Files_3.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root_Files_4.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root_Files_4u.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Prg_Calc.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Systemintegration_child_3.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Prg_Impress.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Systemintegration_child_4.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root_Files_5u.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Pymailmerge.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Grfflt.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Gnome.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Prg_Base.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Systemintegration_child_2.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Prg_Draw.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root_Files_5.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/setup.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Onlineupdate.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root_Files_2.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Systemintegration_child_1.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root_Files_8.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Prg.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root_Files_6.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root_Files_3u.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Javafilter.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Java.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Xsltfiltersamples.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Headless.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root_Files_7.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root_Files_9.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Kde.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Systemintegration.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Root_Files_10.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Pyuno.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/xpd/gid_Module_Optional_Testtool.xpd
OOG680_m9_native_packed-1_en-US.9238/installdata/html/
OOG680_m9_native_packed-1_en-US.9238/installdata/html/InstallationImminent_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/InstallationOngoing_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/ChooseUninstallationComponents.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/InstallationImminent.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/ChooseUninstallationType.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/ChooseDirectory.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/UninstallationPrologue_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/ChooseComponents.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/ChooseUninstallationComponents_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/ChooseInstallationType_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/InstallationOngoing.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/UninstallationOngoing.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/UninstallationImminent_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/UninstallationPrologue.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/LICENSE.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/Prologue_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/ChooseInstallationType.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/ChooseComponents_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/LICENSE_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/ChooseUninstallationType_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/AcceptLicense_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/UninstallationOngoing_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/AcceptLicense.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/UninstallationImminent.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/ChooseDirectory_en-US.html
OOG680_m9_native_packed-1_en-US.9238/installdata/html/Prologue.html
OOG680_m9_native_packed-1_en-US.9238/RPMS/
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core08-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-emailmerge-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core01-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-xsltfilter-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core06-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-impress-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-writer-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/desktop-integration/
OOG680_m9_native_packed-1_en-US.9238/RPMS/desktop-integration/openoffice.org-slackware-menus-2.3-noarch-9238.tgz
OOG680_m9_native_packed-1_en-US.9238/RPMS/desktop-integration/openoffice.org-redhat-menus-2.3-9238.noarch.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/desktop-integration/openoffice.org-debian-menus_2.3-9238_all.deb
OOG680_m9_native_packed-1_en-US.9238/RPMS/desktop-integration/openoffice.org-mandriva-menus-2.3-9238.noarch.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/desktop-integration/openoffice.org-suse-menus-2.3-9238.noarch.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/desktop-integration/openoffice.org-freedesktop-menus-2.3-9238.noarch.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-javafilter-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core05-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core02-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-pyuno-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-testtool-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-onlineupdate-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-gnome-integration-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-math-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-graphicfilter-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-kde-integration-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core07-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/jre-6u3-linux-i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-calc-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-base-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core09-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core04u-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core03u-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-draw-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core10-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core03-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core05u-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-headless-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/RPMS/openoffice.org-core04-2.3.1-9238.i586.rpm
OOG680_m9_native_packed-1_en-US.9238/licenses/
OOG680_m9_native_packed-1_en-US.9238/licenses/LICENSE_en-US
OOG680_m9_native_packed-1_en-US.9238/licenses/LICENSE_en-US.html
OOG680_m9_native_packed-1_en-US.9238/JavaSetup.jar
OOG680_m9_native_packed-1_en-US.9238/setup
OOG680_m9_native_packed-1_en-US.9238/readmes/
OOG680_m9_native_packed-1_en-US.9238/readmes/README_en-US
OOG680_m9_native_packed-1_en-US.9238/readmes/README_en-US.html
nick@t00r:~/Desktop$ cd OOG680_m9_native_packed-1_en-US.9238/
nick@t00r:~/Desktop/OOG680_m9_native_packed-1_en-US.9238$ setup
bash: setup: command not found
nick@t00r:~/Desktop/OOG680_m9_native_packed-1_en-US.9238$ sudo -s
[sudo] password for nick: 
root@t00r:~/Desktop/OOG680_m9_native_packed-1_en-US.9238# sh setup
Checksumming...
Extracting ...
90313 blocks
Done.
Using /var/tmp/install_3930/usr/java/jre1.6.0_03/bin/java
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

Running installer
/var/tmp/install_3930/usr/java/jre1.6.0_03/bin/java -DHOME=/home/nick -DJRE_FILE=jre-6u3-linux-i586.rpm -jar JavaSetup.jar
System locale: en_US
Root privileges
OS: Linux
Mode: installation
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xd0f00767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xd0f008b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xd09d629d]
#3 /var/tmp/install_3930/usr/java/jre1.6.0_03/lib/i386/xawt/libmawt.so [0xd0ab664e]
#4 /var/tmp/install_3930/usr/java/jre1.6.0_03/lib/i386/xawt/libmawt.so [0xd0a94f97]
#5 /var/tmp/install_3930/usr/java/jre1.6.0_03/lib/i386/xawt/libmawt.so [0xd0a95248]
#6 /var/tmp/install_3930/usr/java/jre1.6.0_03/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xd0a9554f]
#7 [0xf4c6ab7b]
#8 [0xf4c62f0d]
#9 [0xf4c62f0d]
#10 [0xf4c60243]
#11 /var/tmp/install_3930/usr/java/jre1.6.0_03/lib/i386/server/libjvm.so [0x62c5ecd]
#12 /var/tmp/install_3930/usr/java/jre1.6.0_03/lib/i386/server/libjvm.so [0x64523b8]
#13 /var/tmp/install_3930/usr/java/jre1.6.0_03/lib/i386/server/libjvm.so [0x62c5d60]
#14 /var/tmp/install_3930/usr/java/jre1.6.0_03/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x34b) [0x631bc1b]
#15 /var/tmp/install_3930/usr/java/jre1.6.0_03/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xf7c7b96d]
#16 [0xf4c6ab7b]
#17 [0xf4c62da7]
#18 [0xf4c60243]
#19 /var/tmp/install_3930/usr/java/jre1.6.0_03/lib/i386/server/libjvm.so [0x62c5ecd]
java: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)


```

---

### Post by nick937 on 2008-03-05
this is my /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha amd64 (20080222)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://bs.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
  
```

---

### Post by tcharron on 2008-03-05
> **nick937 said:**
> this is my /etc/apt/sources.list


Getting the same error.

openoffice.org depends on openoffice.org-writer2latex
openoffice.org-writer2latex does not appear to be available

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe 
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner 
deb-src http://archive.canonical.com/ubuntu hardy partner 

deb http://security.ubuntu.com/ubuntu hardy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted 
deb http://security.ubuntu.com/ubuntu hardy-security universe 
deb-src http://security.ubuntu.com/ubuntu hardy-security universe 
deb http://security.ubuntu.com/ubuntu hardy-security multiverse 
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse 
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main 

# deb http://ppa.launchpad.net/madman2k/ubuntu hardy main restricted universe multiverse

```

---

### Post by tcharron on 2008-03-05
I went ahead and got it from the debian archives:

[http://packages.debian.org/sid/all/openoffice.org-writer2latex/download](http://packages.debian.org/sid/all/openoffice.org-writer2latex/download)

Fixed the issue.

According to [http://utnubu.alioth.debian.org/binary-versiondiff.html](http://utnubu.alioth.debian.org/binary-versiondiff.html) writer2latex is not available in the Ubuntu archives, yet..

---

