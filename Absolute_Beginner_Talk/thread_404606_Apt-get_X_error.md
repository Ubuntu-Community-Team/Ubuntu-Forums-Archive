---
title: "Apt-get X error"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by psyphen on 2007-04-08
I've been getting this message for a while now whenever I install stuff.

```
psy@psy-desktop:~$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java vmware-player-kernel-modules-2.6.17-11 liblog4j1.2-java
  vmware-player-kernel-modules libseda-java libcommons-cli-java libgtk-jni
  libcairo-java libbcprov-java libglib-java libssl0.9.7 libgtk-java
Use 'apt-get autoremove' to remove them.
Suggested packages:
  subversion-tools db4.3-util
The following NEW packages will be installed:
  subversion
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 208kB of archives.
After unpacking 3092kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com edgy/main subversion 1.3.2-3ubuntu2 [208kB]
Fetched 208kB in 1s (154kB/s)     
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 1 during global destruction.
Selecting previously deselected package subversion.
(Reading database ... 165950 files and directories currently installed.)
Unpacking subversion (from .../subversion_1.3.2-3ubuntu2_i386.deb) ...
Setting up subversion (1.3.2-3ubuntu2) ...
psy@psy-desktop:~$
```

Any way to fix this easily? I don't know how it originated.

Thanks,
~psy

---

### Post by Happy_Man on 2007-04-08
Go ahead and post the contents of /etc/X11/xorg.conf here so that we can see it.

---

