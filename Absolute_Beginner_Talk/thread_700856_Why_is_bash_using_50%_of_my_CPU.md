---
title: "Why is bash using 50% of my CPU?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Yes on 2008-02-18
According to System Monitor, bash is using 50% of my CPU.  I don't have any terminals open, does anyone have any idea why this is?

I was just messing around with my bashrc file, but when I comment out the parts I was playing around with it still uses just as much CPU.

Thanks.

---

### Post by p_quarles on 2008-02-18
That's definitely strange. Can you confirm the problem by posting the output of the following terminal command?:
```
ps aux | grep bash
```

---

### Post by Yes on 2008-02-18
```
alex     11523 98.8  0.1   5688  2980 ?        Rs   19:14  26:51 bash
alex     13366  7.0  0.1   5692  3048 pts/0    Ss   19:41   0:00 bash
alex     13386  0.0  0.0   2976   748 pts/0    R+   19:41   0:00 grep bash

```

Does that mean anything to you?

---

### Post by p_quarles on 2008-02-18
> **Yes said:**
> ```
alex     11523 98.8  0.1   5688  2980 ?        Rs   19:14  26:51 bash
alex     13366  7.0  0.1   5692  3048 pts/0    Ss   19:41   0:00 bash
alex     13386  0.0  0.0   2976   748 pts/0    R+   19:41   0:00 grep bash

```

Does that mean anything to you?
Yeah, it confirms the problem you saw in the system monitor. Let's see if we can figure out what it's doing that's taking up so much system time:
```
lsof -c bash
```

---

### Post by Yes on 2008-02-18
```
COMMAND   PID USER   FD   TYPE DEVICE    SIZE     NODE NAME
bash    11523 alex  cwd    DIR    8,8    4096 21282817 /home/alex
bash    11523 alex  rtd    DIR    8,6    4096        2 /
bash    11523 alex  txt    REG    8,6  701680   801253 /bin/bash
bash    11523 alex  mem    REG    8,6   38420   883094 /lib/tls/i686/cmov/libnss_files-2.6.1.so
bash    11523 alex  mem    REG    8,6   34352   883098 /lib/tls/i686/cmov/libnss_nis-2.6.1.so
bash    11523 alex  mem    REG    8,6   83712   883085 /lib/tls/i686/cmov/libnsl-2.6.1.so
bash    11523 alex  mem    REG    8,6   30436   883090 /lib/tls/i686/cmov/libnss_compat-2.6.1.so
bash    11523 alex  mem    REG    8,6  254020   687705 /usr/lib/locale/en_US.utf8/LC_CTYPE
bash    11523 alex  mem    REG    8,6      54   687710 /usr/lib/locale/en_US.utf8/LC_NUMERIC
bash    11523 alex  mem    REG    8,6    2451   687713 /usr/lib/locale/en_US.utf8/LC_TIME
bash    11523 alex  mem    REG    8,6  915322   687704 /usr/lib/locale/en_US.utf8/LC_COLLATE
bash    11523 alex  mem    REG    8,6     286   687708 /usr/lib/locale/en_US.utf8/LC_MONETARY
bash    11523 alex  mem    REG    8,6      52   687714 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
bash    11523 alex  mem    REG    8,6 1339816   883035 /lib/tls/i686/cmov/libc-2.6.1.so
bash    11523 alex  mem    REG    8,6    9684   883060 /lib/tls/i686/cmov/libdl-2.6.1.so
bash    11523 alex  mem    REG    8,6  273124   883087 /lib/libncurses.so.5.6
bash    11523 alex  mem    REG    8,6      34   687711 /usr/lib/locale/en_US.utf8/LC_PAPER
bash    11523 alex  mem    REG    8,6      77   687709 /usr/lib/locale/en_US.utf8/LC_NAME
bash    11523 alex  mem    REG    8,6     155   687703 /usr/lib/locale/en_US.utf8/LC_ADDRESS
bash    11523 alex  mem    REG    8,6      59   687712 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
bash    11523 alex  mem    REG    8,6      23   687707 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
bash    11523 alex  mem    REG    8,6   25486   621512 /usr/lib/gconv/gconv-modules.cache
bash    11523 alex  mem    REG    8,6     373   687706 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
bash    11523 alex  mem    REG    8,6  109148   883576 /lib/ld-2.6.1.so
bash    11523 alex    0u   CHR  136,1                3 /dev/pts/1 (deleted)
bash    11523 alex    1u   CHR  136,1                3 /dev/pts/1 (deleted)
bash    11523 alex    2u   CHR  136,1                3 /dev/pts/1 (deleted)
bash    11523 alex  255u   CHR  136,1                3 /dev/pts/1 (deleted)
bash    13407 alex  cwd    DIR    8,8    4096 21282817 /home/alex
bash    13407 alex  rtd    DIR    8,6    4096        2 /
bash    13407 alex  txt    REG    8,6  701680   801253 /bin/bash
bash    13407 alex  mem    REG    8,6   38420   883094 /lib/tls/i686/cmov/libnss_files-2.6.1.so
bash    13407 alex  mem    REG    8,6   34352   883098 /lib/tls/i686/cmov/libnss_nis-2.6.1.so
bash    13407 alex  mem    REG    8,6   83712   883085 /lib/tls/i686/cmov/libnsl-2.6.1.so
bash    13407 alex  mem    REG    8,6   30436   883090 /lib/tls/i686/cmov/libnss_compat-2.6.1.so
bash    13407 alex  mem    REG    8,6  254020   687705 /usr/lib/locale/en_US.utf8/LC_CTYPE
bash    13407 alex  mem    REG    8,6      54   687710 /usr/lib/locale/en_US.utf8/LC_NUMERIC
bash    13407 alex  mem    REG    8,6    2451   687713 /usr/lib/locale/en_US.utf8/LC_TIME
bash    13407 alex  mem    REG    8,6  915322   687704 /usr/lib/locale/en_US.utf8/LC_COLLATE
bash    13407 alex  mem    REG    8,6     286   687708 /usr/lib/locale/en_US.utf8/LC_MONETARY
bash    13407 alex  mem    REG    8,6      52   687714 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
bash    13407 alex  mem    REG    8,6 1339816   883035 /lib/tls/i686/cmov/libc-2.6.1.so
bash    13407 alex  mem    REG    8,6    9684   883060 /lib/tls/i686/cmov/libdl-2.6.1.so
bash    13407 alex  mem    REG    8,6  273124   883087 /lib/libncurses.so.5.6
bash    13407 alex  mem    REG    8,6      34   687711 /usr/lib/locale/en_US.utf8/LC_PAPER
bash    13407 alex  mem    REG    8,6      77   687709 /usr/lib/locale/en_US.utf8/LC_NAME
bash    13407 alex  mem    REG    8,6     155   687703 /usr/lib/locale/en_US.utf8/LC_ADDRESS
bash    13407 alex  mem    REG    8,6      59   687712 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
bash    13407 alex  mem    REG    8,6      23   687707 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
bash    13407 alex  mem    REG    8,6   25486   621512 /usr/lib/gconv/gconv-modules.cache
bash    13407 alex  mem    REG    8,6     373   687706 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
bash    13407 alex  mem    REG    8,6  109148   883576 /lib/ld-2.6.1.so
bash    13407 alex    0u   CHR  136,0                2 /dev/pts/0
bash    13407 alex    1u   CHR  136,0                2 /dev/pts/0
bash    13407 alex    2u   CHR  136,0                2 /dev/pts/0
bash    13407 alex  255u   CHR  136,0                2 /dev/pts/0
```

---

### Post by p_quarles on 2008-02-18
Okay, I don't see anything amiss there, so let's have a look at the process tree (if you want explanations of any of these commands, btw, just ask):
```
ps axjf
```

---

### Post by Yes on 2008-02-18
```
 PPID   PID  PGID   SID TTY      TPGID STAT   UID   TIME COMMAND
    0     2     0     0 ?           -1 S<       0   0:00 [kthreadd]
    2     3     0     0 ?           -1 S<       0   0:00  \_ [migration/0]
    2     4     0     0 ?           -1 SN       0   0:00  \_ [ksoftirqd/0]
    2     5     0     0 ?           -1 S<       0   0:00  \_ [watchdog/0]
    2     6     0     0 ?           -1 S<       0   0:00  \_ [migration/1]
    2     7     0     0 ?           -1 SN       0   0:00  \_ [ksoftirqd/1]
    2     8     0     0 ?           -1 S<       0   0:00  \_ [watchdog/1]
    2     9     0     0 ?           -1 S<       0   0:00  \_ [events/0]
    2    10     0     0 ?           -1 S<       0   0:00  \_ [events/1]
    2    11     0     0 ?           -1 S<       0   0:00  \_ [khelper]
    2    31     0     0 ?           -1 S<       0   0:00  \_ [kblockd/0]
    2    32     0     0 ?           -1 S<       0   0:00  \_ [kblockd/1]
    2    33     0     0 ?           -1 S<       0   0:00  \_ [kacpid]
    2    34     0     0 ?           -1 S<       0   0:00  \_ [kacpi_notify]
    2   164     0     0 ?           -1 S<       0   0:00  \_ [kseriod]
    2   192     0     0 ?           -1 S        0   0:00  \_ [pdflush]
    2   193     0     0 ?           -1 S        0   0:00  \_ [pdflush]
    2   194     0     0 ?           -1 S<       0   0:00  \_ [kswapd0]
    2   245     0     0 ?           -1 S<       0   0:00  \_ [aio/0]
    2   246     0     0 ?           -1 S<       0   0:00  \_ [aio/1]
    2  2109     0     0 ?           -1 S<       0   0:00  \_ [ksuspend_usbd]
    2  2110     0     0 ?           -1 S<       0   0:00  \_ [khubd]
    2  2225     0     0 ?           -1 S<       0   0:00  \_ [ata/0]
    2  2228     0     0 ?           -1 S<       0   0:00  \_ [ata/1]
    2  2230     0     0 ?           -1 S<       0   0:00  \_ [ata_aux]
    2  2322     0     0 ?           -1 S<       0   0:00  \_ [scsi_eh_0]
    2  2323     0     0 ?           -1 S<       0   0:00  \_ [scsi_eh_1]
    2  2353     0     0 ?           -1 S<       0   0:00  \_ [scsi_eh_2]
    2  2354     0     0 ?           -1 S<       0   0:00  \_ [scsi_eh_3]
    2  2402     0     0 ?           -1 S<       0   0:00  \_ [scsi_eh_4]
    2  2403     0     0 ?           -1 S<       0   0:00  \_ [scsi_eh_5]
    2  2590     0     0 ?           -1 S<       0   0:00  \_ [kjournald]
    2  3855     0     0 ?           -1 S<       0   0:00  \_ [kpsmoused]
    2  4285     0     0 ?           -1 S<       0   0:00  \_ [kjournald]
    2  4286     0     0 ?           -1 S<       0   0:00  \_ [kjournald]
    2  4780     0     0 ?           -1 S<       0   0:00  \_ [kondemand/0]
    2  4782     0     0 ?           -1 S<       0   0:00  \_ [kondemand/1]
    2  5360     1     1 ?           -1 S<       0   0:00  \_ [krfcommd]
    0     1     1     1 ?           -1 Ss       0   0:00 /sbin/init
    1  2795  2795  2795 ?           -1 S<s      0   0:00 /sbin/udevd --daemon
    1  4289  4289  4289 ?           -1 Ss       0   0:00 /sbin/mount.ntfs /dev/s
    1  4531  4531  4531 tty4      4531 Ss+      0   0:00 /sbin/getty 38400 tty4
    1  4532  4532  4532 tty5      4532 Ss+      0   0:00 /sbin/getty 38400 tty5
    1  4534  4534  4534 tty2      4534 Ss+      0   0:00 /sbin/getty 38400 tty2
    1  4536  4536  4536 tty3      4536 Ss+      0   0:00 /sbin/getty 38400 tty3
    1  4538  4538  4538 tty1      4538 Ss+      0   0:00 /sbin/getty 38400 tty1
    1  4539  4539  4539 tty6      4539 Ss+      0   0:00 /sbin/getty 38400 tty6
    1  4725  4725  4725 ?           -1 Ss       0   0:00 /usr/sbin/acpid -c /etc
    1  4847  4847  4847 ?           -1 Ss     101   0:00 /sbin/syslogd -u syslog
    1  4905  4904  4904 ?           -1 S        0   0:00 /bin/dd bs 1 if /proc/k
    1  4907  4907  4907 ?           -1 Ss     102   0:00 /sbin/klogd -P /var/run
    1  4928  4928  4928 ?           -1 Ss     103   0:00 /usr/bin/dbus-daemon --
    1  4944  4944  4944 ?           -1 Ssl      0   0:00 /usr/sbin/NetworkManage
    1  4957  4957  4957 ?           -1 Ss       0   0:00 /usr/sbin/NetworkManage
    1  4971  4971  4971 ?           -1 Ss       0   0:00 /usr/bin/system-tools-b
 4971  4972  4971  4971 ?           -1 S        0   0:00  \_ dbus-daemon --sessi
    1  4991  4991  4991 ?           -1 Ss     107   0:00 /usr/sbin/hald
 4991  4992  4991  4991 ?           -1 S        0   0:00  \_ hald-runner
 4992  5047  4991  4991 ?           -1 S      107   0:00      \_ hald-addon-keyb
 4992  5053  4991  4991 ?           -1 S      107   0:00      \_ hald-addon-keyb
 4992  5054  4991  4991 ?           -1 S      107   0:00      \_ hald-addon-keyb
 4992  5058  4991  4991 ?           -1 S      107   0:00      \_ hald-addon-acpi
 4992  5400  4991  4991 ?           -1 S      107   0:00      \_ hald-addon-stor
    1  5055  5055  5055 ?           -1 Ss       0   0:00 /usr/sbin/cupsd
    1  5219  5219  5219 ?           -1 Ssl      0   0:00 /usr/sbin/console-kit-d
    1  5306  5306  5306 ?           -1 Ss     106   0:00 avahi-daemon: running [
 5306  5307  5307  5307 ?           -1 Ss     106   0:00  \_ avahi-daemon: chroo
    1  5321  5321  5321 ?           -1 Ss       0   0:00 /usr/sbin/dhcdbd --syst
 5321  5561  5321  5321 ?           -1 S      100   0:00  \_ /sbin/dhclient -1 -
    1  5341  5341  5341 ?           -1 Ss       0   0:00 /usr/sbin/hcid -x -s
 5341  5353  5341  5341 ?           -1 S        0   0:00  \_ /usr/lib/bluetooth/
 5341  5354  5341  5341 ?           -1 S        0   0:00  \_ /usr/lib/bluetooth/
    1  5404  5404  5404 ?           -1 Ss       0   0:00 /usr/sbin/gdm
 5404 12905 12905  5404 ?           -1 S        0   0:00  \_ /usr/sbin/gdm
12905 12908 12908 12908 tty7     12908 SLs+     0   0:24      \_ /usr/bin/X :0 -
12905 12931 12931 12931 ?           -1 Ssl   1000   0:00      \_ x-session-manag
12931 12968 12968 12968 ?           -1 Ss    1000   0:00          \_ /usr/bin/ss
12931 12990 12931 12931 ?           -1 S     1000   0:04          \_ gnome-panel
12931 12991 12931 12931 ?           -1 S     1000   0:01          \_ nautilus --
12931 13087 12931 12931 ?           -1 S     1000   0:00          \_ vino-sessio
12931 13088 12931 12931 ?           -1 S     1000   0:00          \_ bluetooth-a
12931 13094 12931 12931 ?           -1 S     1000   0:00          \_ update-noti
12931 13098 12931 12931 ?           -1 Sl    1000   0:00          \_ /usr/lib/ev
12931 13119 12931 12931 ?           -1 S     1000   0:00          \_ python /usr
12931 13121 12931 12931 ?           -1 S     1000   0:00          \_ nm-applet -
    1  5466  5466  5466 ?           -1 Ss       1   0:00 /usr/sbin/atd
    1  5480  5480  5480 ?           -1 Ss       0   0:00 /usr/sbin/cron
    1  5644  5602  5602 ?           -1 S     1000   0:00 /usr/lib/libgconf2-4/gc
    1  5684  5684  5684 ?           -1 Ss    1000   0:00 dbus-daemon --fork --pr
    1  5753  5684  5684 ?           -1 S     1000   0:00 /usr/lib/gnome-vfs-2.0/
    1  5814  5602  5602 ?           -1 SNl   1000   0:00 trackerd
    1 11523 11523 11523 ?           -1 Rs    1000  38:22 bash
    1 12134 12134 12134 ?           -1 Ss    1000   0:00 dbus-daemon --fork --pr
    1 12166 12134 12134 ?           -1 S     1000   0:00 /usr/lib/gnome-vfs-2.0/
    1 12472 12472 12472 ?           -1 Ss    1000   0:00 dbus-daemon --fork --pr
    1 12545 12472 12472 ?           -1 S     1000   0:00 /usr/lib/gnome-vfs-2.0/
    1 12928 12905  5404 ?           -1 SL    1000   0:00 /usr/bin/gnome-keyring-
    1 12972 12972 12972 ?           -1 Ss    1000   0:00 dbus-daemon --fork --pr
    1 12974 12972 12972 ?           -1 Sl    1000   0:00 /usr/lib/gnome-control-
    1 12992 12992 12992 ?           -1 Ss    1000   0:00 gnome-screensaver
    1 13043 13043 13043 ?           -1 Ssl   1000   0:00 /usr/lib/bonobo-activat
    1 13045 13045 13045 ?           -1 Ss    1000   0:00 gnome-volume-manager --
    1 13054 12972 12972 ?           -1 S     1000   0:00 /usr/lib/gnome-vfs-2.0/
    1 13097 13043 13043 ?           -1 S     1000   0:00 /usr/lib/gnome-applets/
    1 13125 13043 13043 ?           -1 Sl    1000   0:00 /usr/lib/evolution/2.12
    1 13126 13126 13126 ?           -1 Ss    1000   0:00 gnome-power-manager
    1 13135 13043 13043 ?           -1 Sl    1000   0:00 /usr/lib/evolution/evol
    1 13151 12931 12931 ?           -1 S     1000   0:00 /usr/lib/nautilus-cd-bu
    1 13154 13043 13043 ?           -1 S     1000   0:00 /usr/lib/fast-user-swit
    1 13156 13043 13043 ?           -1 Sl    1000   0:00 /usr/bin/python /usr/li
    1 13158 13043 13043 ?           -1 Sl    1000   0:00 /usr/lib/gnome-applets/
    1 13164 12931 12931 ?           -1 S     1000   0:00 conky
    1 13219 12931 12931 ?           -1 S     1000   0:00 /bin/sh /usr/bin/compiz
13219 13293 12931 12931 ?           -1 S     1000   0:01  \_ /usr/bin/emerald --
13219 13294 12931 12931 ?           -1 SL    1000   0:08  \_ /usr/bin/compiz.rea
    1 13296 12931 12931 ?           -1 S     1000   0:00 /bin/sh /usr/bin/firefo
13296 13308 12931 12931 ?           -1 S     1000   0:00  \_ /bin/sh /usr/lib/fi
13308 13312 12931 12931 ?           -1 Sl    1000   0:59      \_ /usr/lib/firefo
    1 13474 12931 12931 ?           -1 Sl    1000   0:00 gnome-terminal
13474 13477 12931 12931 ?           -1 S     1000   0:00  \_ gnome-pty-helper
13474 13478 13478 13478 pts/0    13497 Ss    1000   0:00  \_ bash
13478 13497 13497 13478 pts/0    13497 R+    1000   0:00      \_ ps axjf
```

Are the commands the full command, or are they abbreviations?

---

### Post by p_quarles on 2008-02-18
They are the full commands, with options. "ps" lists processes running, and "lsof" lists open files and gives information about who and what is using them.

According to this line:
```
    1 11523 11523 11523 ?           -1 Rs    1000  38:22 bash
```it looks as though bash is really doing nothing except eating your CPU. Very strange.

Anyway, is this a recent problem? Have you tried rebooting since the problem occurred?

EDIT: You may also want to try manually ending the runaway process:
```
kill 11523
```

---

### Post by Yes on 2008-02-18
Rebooted and it seems to be fixed.

Thanks!

---

