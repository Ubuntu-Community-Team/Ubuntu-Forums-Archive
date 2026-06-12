---
title: "Ubuntu on MacBookAir 11&quot; Parallels: Graphics Problem"
date: 2014-05-10
forum: Apple Hardware Users
---

### Post by stevie5 on 2014-05-10
Hi Folks,

I have installed Ubuntu in Paralles 9 on a MacBook Air 11".
The Problem is, that I can't get a better resolution than 800x600
and I cant get a different Display to select. In other words, the system is running 
on the default display only, whit no choice of selecting any thing different.

What should I do?

Cheers,

Steve5

---

### Post by bapoumba on 2014-05-10
*Thread moved to **Apple Users**.*

---

### Post by stevie5 on 2014-05-12
doesn't anyone have clou?

when installing the Parallels-Tools, I get this error-message:

```
Parallels Tools 9.0.24172.951362 Installer started.
2014-05-12T09:42:33-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

Mo 12. Mai 09:42:33 PDT 2014
Start installation or upgrade of Guest Tools
new version of parallels tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: Datei oder Verzeichnis nicht gefunden
Start installation of prl_eth kernel module
make: Gehe in Verzeichnis '/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Betrete Verzeichnis '/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/3.13.0-24-lowlatency/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Betrete Verzeichnis '/usr/src/linux-headers-3.13.0-24-lowlatency'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Verlasse Verzeichnis '/usr/src/linux-headers-3.13.0-24-lowlatency'
make[1]: Verlasse Verzeichnis '/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Betrete Verzeichnis '/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/3.13.0-24-lowlatency/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Betrete Verzeichnis '/usr/src/linux-headers-3.13.0-24-lowlatency'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Verlasse Verzeichnis '/usr/src/linux-headers-3.13.0-24-lowlatency'
make[1]: Verlasse Verzeichnis '/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Betrete Verzeichnis '/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/3.13.0-24-lowlatency/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Betrete Verzeichnis '/usr/src/linux-headers-3.13.0-24-lowlatency'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c: In function ‘prlfs_parse_mount_options’:
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:67:11: error: incompatible types when assigning to type ‘uid_t’ from type ‘kuid_t’
  sbi->uid = current->cred->uid;
           ^
/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.c:68:11: error: incompatible types when assigning to type ‘gid_t’ from type ‘kgid_t’
  sbi->gid = current->cred->gid;
           ^
make[3]: *** [/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o] Fehler 1
make[2]: *** [_module_/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs] Fehler 2
make[2]: Verlasse Verzeichnis '/usr/src/linux-headers-3.13.0-24-lowlatency'
make[1]: *** [all] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: *** [installme] Fehler 2
make: Verlasse Verzeichnis '/usr/lib/parallels-tools/kmods'
Error: could not build kernel modules
Error: failed to install kernel modules
2014-05-12T09:42:36-0700: execCmd: ./install --install [143]
2014-05-12T09:42:36-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2014-05-12T09:42:37-0700: Exiting with code 1



                 
```

---

### Post by alan26 on 2014-05-13
Did you ever solve this? I'm wanting to switch on one of my older Airs and I've seen a couple of errors.

---

### Post by stevie5 on 2014-05-14
Hi Alan,

yes, I did solve this Problem, but not the way you would expect it! :biggrin:
Everything that I have found on the Inet, to solve it with Parallels did NOT work.
Obviously Parallels still has a Kerne-Problem with the new Kernels.

Finally, I removed Paralles and installed VMware. And right away, it worked out of the box.
I am happy now, and no I can not recommend PARALLELS. They are either very slow 
in fixing their Problems or, just ignorant.

---

