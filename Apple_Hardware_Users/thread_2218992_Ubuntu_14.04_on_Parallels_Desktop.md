---
title: "Ubuntu 14.04 on Parallels Desktop"
date: 2014-04-22
forum: Apple Hardware Users
---

### Post by Fili1939 on 2014-04-22
I installed Ubuntu 14.04 on Parallels Desktop for Mac, but I can't install Parallels Tools. I receive and error which says: "An error occured when installing Parallels Tools. Please go to parallels-tools-installation.log for more information". Here's the log file:

[I]2014-04-22T15:56:42+0200: 

Parallels Tools 9.0.24172.951362 Installer started.
2014-04-22T15:56:47+0200: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [1]
2014-04-22T15:56:58+0200: Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports InRelease
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports Release.gpg
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [58,5 kB]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [970 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/main Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [14 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/restricted Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [14 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/multiverse Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [977 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/main amd64 Packages
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [14 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/restricted amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/universe amd64 Packages
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [14 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/multiverse amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/main i386 Packages
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [14 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/universe i386 Packages
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [977 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/multiverse i386 Packages
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/main Translation-en
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/multiverse Translation-en
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [14 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/restricted Translation-en
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [14 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/universe Translation-en
Get:15 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/main Sources [2.774 B]
Get:16 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]
Get:17 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/universe Sources [648 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Get:18 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/multiverse Sources [1.790 B]
Get:19 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/main amd64 Packages [9.543 B]
Get:20 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [14 B]
Get:21 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/universe amd64 Packages [1.602 B]
Get:22 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [6.362 B]
Get:23 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/main i386 Packages [8.165 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Get:24 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Get:25 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/universe i386 Packages [1.601 B]
Get:26 [http://it.archive.u2014-04-22T15:57:17+0200:](http://it.archive.u2014-04-22T15:57:17+0200:) buntu.com trusty-updates/multiverse i386 Packages [6.386 B]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/main Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/main amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/restricted amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/universe amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/main i386 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-updates/universe Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/main Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) trusty-backports/universe Translation-en_US
Fetched 101 kB in 17s (5.831 B/s)
Reading package lists...
Return code from apt-get update is 0
Selecting previously unselected package dkms.
(Reading database ... 163448 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20-3ubuntu2) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking fakeroot (1.20-3ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
Setting up libfakeroot:amd64 (1.20-3ubuntu2) ...
Setting up fakeroot (1.20-3ubuntu2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
2014-04-22T15:57:17+0200: execCmd: ./installer/pm.sh download_guest_tools 2>&1 [0]

mar 22 apr 2014, 15.57.17, CEST
Start installation or upgrade of Guest Tools
new version of parallels tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c: In function ‘prlfs_parse_mount_options’:
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:67:11: error: incompatible types when assigning to type ‘uid_t’ from type ‘kuid_t’
  sbi->uid = current->cred->uid;
           ^
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:68:11: error: incompatible types when assigning to type ‘gid_t’ from type ‘kgid_t’
  sbi->gid = current->cred->gid;
           ^
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: *** [installme] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2014-04-22T15:57:23+0200: execCmd: ./install --install [143]
2014-04-22T15:57:23+0200: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2014-04-22T15:58:54+0200: Exiting with code 1
2014-04-22T16:00:26+0200: 

Parallels Tools 9.0.24172.951362 Installer started.
2014-04-22T16:00:28+0200: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

mar 22 apr 2014, 16.00.28, CEST
Start installation or upgrade of Guest Tools
new version of parallels tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c: In function ‘prlfs_parse_mount_options’:
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:67:11: error: incompatible types when assigning to type ‘uid_t’ from type ‘kuid_t’
  sbi->uid = current->cred->uid;
           ^
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:68:11: error: incompatible types when assigning to type ‘gid_t’ from type ‘kgid_t’
  sbi->gid = current->cred->gid;
           ^
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: *** [installme] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2014-04-22T16:00:32+0200: execCmd: ./install --install [143]
2014-04-22T16:00:32+0200: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2014-04-22T16:00:43+0200: Exiting with code 1
2014-04-22T16:02:11+0200: 

Parallels Tools 9.0.24172.951362 Installer started.
2014-04-22T16:02:13+0200: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

mar 22 apr 2014, 16.02.13, CEST
Start installation or upgrade of Guest Tools
new version of parallels tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c: In function ‘prlfs_parse_mount_options’:
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:67:11: error: incompatible types when assigning to type ‘uid_t’ from type ‘kuid_t’
  sbi->uid = current->cred->uid;
           ^
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:68:11: error: incompatible types when assigning to type ‘gid_t’ from type ‘kgid_t’
  sbi->gid = current->cred->gid;
           ^
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: *** [installme] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2014-04-22T16:02:16+0200: execCmd: ./install --install [143]
2014-04-22T16:02:16+0200: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2014-04-22T16:02:18+0200: Exiting with code 1
2014-04-22T16:07:44+0200: 

Parallels Tools 9.0.24172.951362 Installer started.
2014-04-22T16:07:45+0200: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

mar 22 apr 2014, 16.07.46, CEST
Start installation or upgrade of Guest Tools
new version of parallels tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c: In function ‘prlfs_parse_mount_options’:
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:67:11: error: incompatible types when assigning to type ‘uid_t’ from type ‘kuid_t’
  sbi->uid = current->cred->uid;
           ^
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:68:11: error: incompatible types when assigning to type ‘gid_t’ from type ‘kgid_t’
  sbi->gid = current->cred->gid;
           ^
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: *** [installme] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2014-04-22T16:07:49+0200: execCmd: ./install --install [143]
2014-04-22T16:07:49+0200: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2014-04-22T16:09:20+0200: Exiting with code 1
2014-04-22T16:12:17+0200: 

Parallels Tools 9.0.24172.951362 Installer started.
2014-04-22T16:12:19+0200: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

mar 22 apr 2014, 16.12.20, CEST
Start installation or upgrade of Guest Tools
new version of parallels tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c: In function ‘prlfs_parse_mount_options’:
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:67:11: error: incompatible types when assigning to type ‘uid_t’ from type ‘kuid_t’
  sbi->uid = current->cred->uid;
           ^
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:68:11: error: incompatible types when assigning to type ‘gid_t’ from type ‘kgid_t’
  sbi->gid = current->cred->gid;
           ^
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: *** [installme] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2014-04-22T16:12:23+0200: execCmd: ./install --install [143]
2014-04-22T16:12:23+0200: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2014-04-22T16:12:27+0200: Exiting with code 1
tar (child): /media/filippo/tools/prltools.x64.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
Error during report about start installation of parallels tools.

mar 22 apr 2014, 16.16.24, CEST
Start installation or upgrade of Guest Tools
new version of parallels tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c: In function 'prlfs_parse_mount_options':
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:67:11: error: incompatible types when assigning to type 'uid_t' from type 'kuid_t'
  sbi->uid = current->cred->uid;
           ^
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:68:11: error: incompatible types when assigning to type 'gid_t' from type 'kgid_t'
  sbi->gid = current->cred->gid;
           ^
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: *** [installme] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
Error during report about failed installation of parallels tools.
2014-04-22T16:18:48+0200: 

Parallels Tools 9.0.24172.951362 Installer started.
2014-04-22T16:18:50+0200: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

mar 22 apr 2014, 16.18.50, CEST
Start installation or upgrade of Guest Tools
new version of parallels tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c: In function ‘prlfs_parse_mount_options’:
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:67:11: error: incompatible types when assigning to type ‘uid_t’ from type ‘kuid_t’
  sbi->uid = current->cred->uid;
           ^
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:68:11: error: incompatible types when assigning to type ‘gid_t’ from type ‘kgid_t’
  sbi->gid = current->cred->gid;
           ^
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: *** [installme] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2014-04-22T16:18:56+0200: execCmd: ./install --install [143]
2014-04-22T16:18:56+0200: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2014-04-22T16:18:57+0200: Exiting with code 1
2014-04-22T16:22:45+0200: 

Parallels Tools 9.0.24172.951362 Installer started.
2014-04-22T16:22:47+0200: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

mar 22 apr 2014, 16.22.47, CEST
Start installation or upgrade of Guest Tools
new version of parallels tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c: In function ‘prlfs_parse_mount_options’:
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:67:11: error: incompatible types when assigning to type ‘uid_t’ from type ‘kuid_t’
  sbi->uid = current->cred->uid;
           ^
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:68:11: error: incompatible types when assigning to type ‘gid_t’ from type ‘kgid_t’
  sbi->gid = current->cred->gid;
           ^
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: *** [installme] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2014-04-22T16:22:52+0200: execCmd: ./install --install [143]
2014-04-22T16:22:52+0200: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2014-04-22T16:26:09+0200: Exiting with code 1
2014-04-22T16:41:03+0200: 

Parallels Tools 9.0.24172.951362 Installer started.
2014-04-22T16:41:06+0200: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

mar 22 apr 2014, 16.41.06, CEST
Start installation or upgrade of Guest Tools
new version of parallels tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/3.13.0-24-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c: In function ‘prlfs_parse_mount_options’:
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:67:11: error: incompatible types when assigning to type ‘uid_t’ from type ‘kuid_t’
  sbi->uid = current->cred->uid;
           ^
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:68:11: error: incompatible types when assigning to type ‘gid_t’ from type ‘kgid_t’
  sbi->gid = current->cred->gid;
           ^
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o] Error 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: *** [installme] Error 2
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2014-04-22T16:41:09+0200: execCmd: ./install --install [143]
2014-04-22T16:41:09+0200: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2014-04-22T16:41:12+0200: Exiting with code 1[/I]"

What can I do to fix it?

---

