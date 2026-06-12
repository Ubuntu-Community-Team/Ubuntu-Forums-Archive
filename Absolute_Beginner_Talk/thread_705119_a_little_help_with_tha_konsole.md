---
title: "a little help with tha konsole"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Benifited on 2008-02-23
hey guys i need some help with installing some programs like compiz ect. but i get a messege when i try to run the package manager. it tells me that there is another app using it. so when i go to tha konsole to run sudo dpkg --configure -a  to see if i have any updates that arent done. and i get this messege.

dpkg: status database area is locked by another process

what should i do to fix this problem?

---

### Post by PeterJS on 2008-02-23
Find out what program is holding the lock on the package database and close it. Some common candidates are Adept, Synaptic, and the Update Manager.

---

### Post by Benifited on 2008-02-23
wat i the th commands for those apps. sorry im a lil new at this . thx for tha help

---

### Post by northern lights on 2008-02-23
Commands are not neccessarily required. On the top panle go to "System > Preferences > Sessions", under the "Current Session" tab check what's running...

---

### Post by Benifited on 2008-02-23
> **northern lights said:**
> Commands are not neccessarily required. On the top panle go to "System > Preferences > Sessions", under the "Current Session" tab check what's running...

how would i find that on kubuntu 7.10

---

### Post by northern lights on 2008-02-23
Good one, I don't know. Hope someone with KDE knowledge will answer.

Alternatively, post the output of ```
ps -u root
```

---

### Post by Benifited on 2008-02-23
sure here

PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   26 ?        00:00:00 kblockd/0
   27 ?        00:00:00 kacpid
   28 ?        00:00:00 kacpi_notify
   93 ?        00:00:00 kseriod
  112 ?        00:00:00 pdflush
  113 ?        00:00:00 pdflush
  114 ?        00:00:03 kswapd0
  165 ?        00:00:00 aio/0
 1199 ?        00:00:00 ata/0
 1200 ?        00:00:00 ata_aux
 1219 ?        00:00:00 ksuspend_usbd
 1222 ?        00:00:00 khubd
 1286 ?        00:00:00 scsi_eh_0
 1287 ?        00:00:00 usb-storage
 1302 ?        00:00:00 scsi_eh_1
 1304 ?        00:00:00 scsi_eh_2
 1473 ?        00:00:00 jfsIO
 1474 ?        00:00:00 jfsCommit
 1475 ?        00:00:00 jfsSync
 1483 ?        00:00:00 xfslogd/0
 1484 ?        00:00:00 xfsdatad/0
 1555 ?        00:00:00 unionfs_siod/0
 2769 ?        00:05:13 ntfs-3g
 2861 ?        00:00:22 loop0
 2862 ?        00:00:11 kjournald
 3129 ?        00:00:00 udevd
 3987 ?        00:00:00 kgameportd
 4048 ?        00:00:00 kpsmoused
 4381 ?        00:00:00 loop1
 4382 ?        00:00:00 kjournald
 4633 tty4     00:00:00 getty
 4634 tty5     00:00:00 getty
 4636 tty2     00:00:00 getty
 4641 tty3     00:00:00 getty
 4642 tty1     00:00:00 getty
 4643 tty6     00:00:00 getty
 4814 ?        00:00:00 acpid
 4864 ?        00:00:00 kondemand/0
 4912 ?        00:00:00 syslogd
 4967 ?        00:00:00 dd
 5006 ?        00:00:00 NetworkManager
 5019 ?        00:00:00 NetworkManagerD
 5069 ?        00:00:00 cupsd
 5171 ?        00:00:00 hcid
 5186 ?        00:00:00 krfcommd
 5193 ?        00:00:00 bluetoothd-serv
 5215 ?        00:00:00 bluetoothd-serv
 5235 ?        00:00:00 cron
 5299 ?        00:00:00 kdm
 5318 tty7     00:06:05 Xorg
 5333 ?        00:00:00 kdm
 5436 ?        00:00:00 start_kdeinit
 7774 ?        00:00:01 artsd

---

### Post by Benifited on 2008-02-23
can some 1 plz help me with my problem i would really like to be able to install some apps. on my kubuntu installation.

---

### Post by Benifited on 2008-02-23
im sry to bump. but i just cant believe that there is no 1 on this forum that cant help me. is it really that big of a problem? im i going to have to start a fresh installation?

---

