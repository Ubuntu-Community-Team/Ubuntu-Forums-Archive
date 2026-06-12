---
title: "Lonley application needs a friend"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by zanazzi on 2007-07-12
Adept-notifier wont go!!

I cant close the thing and it sits minimized on my task bar and i cant close it,

I types top into the konsol but i cant see it there, (tbh im not sure what it will apear as)

how do i get rid of the little thing?

regards

---

### Post by twiceasworn on 2007-07-12
What is the output of ```
ps axww
```?

---

### Post by Al3xK3aton on 2007-07-12
Did you try right clicking the taskbar button?

---

### Post by zanazzi on 2007-07-12
th out put to psaxww is 
```
desktop:~$ ps axww
  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:01 /sbin/init
    2 ?        S      0:00 [migration/0]
    3 ?        SN     0:00 [ksoftirqd/0]
    4 ?        S      0:00 [watchdog/0]
    5 ?        S      0:00 [migration/1]
    6 ?        SN     0:00 [ksoftirqd/1]
    7 ?        S      0:00 [watchdog/1]
    8 ?        S<     0:00 [events/0]
    9 ?        S<     0:00 [events/1]
   10 ?        S<     0:00 [khelper]
   11 ?        S<     0:00 [kthread]
   35 ?        S<     0:00 [kblockd/0]
   36 ?        S<     0:00 [kblockd/1]
   37 ?        S<     0:00 [kacpid]
   38 ?        S<     0:00 [kacpi_notify]
  138 ?        S<     0:00 [kseriod]
  165 ?        S      0:00 [pdflush]
  166 ?        S      0:00 [pdflush]
  167 ?        S<     0:00 [kswapd0]
  168 ?        S<     0:00 [aio/0]
  169 ?        S<     0:00 [aio/1]
  806 ?        S      0:00 [kirqd]
 2023 ?        S<     0:00 [ksuspend_usbd]
 2025 ?        S<     0:00 [khubd]
 2071 ?        S<     0:00 [ata/0]
 2072 ?        S<     0:00 [ata/1]
 2073 ?        S<     0:00 [ata_aux]
 2087 ?        S<     0:00 [khpsbpkt]
 2199 ?        S<     0:00 [knodemgrd_0]
 2232 ?        S<     0:00 [scsi_eh_0]
 2233 ?        S<     0:00 [scsi_eh_1]
 2234 ?        S<     0:00 [scsi_eh_2]
 2235 ?        S<     0:00 [scsi_eh_3]
 2320 ?        S<     0:00 [scsi_eh_4]
 2321 ?        S<     0:00 [usb-storage]
 2344 ?        S<     0:00 [scsi_eh_5]
 2345 ?        S<     0:00 [scsi_eh_6]
 2459 ?        S<     0:00 [kjournald]
 2661 ?        S<s    0:00 /sbin/udevd --daemon
 3760 ?        S<     0:00 [kpsmoused]
 3911 ?        S<     0:00 [hda_codec]
 4590 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4591 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4593 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4595 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4597 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 4598 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 4856 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 4967 ?        Ss     0:00 /sbin/syslogd
 5021 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 5023 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 5044 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 5060 ?        Ss     0:00 /usr/sbin/hald
 5061 ?        S      0:00 hald-runner
 5067 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event1
 5068 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event2
 5069 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event5
 5070 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event6
 5072 ?        S      0:00 /usr/lib/hal/hald-addon-cpufreq
 5073 ?        S      0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
 5084 ?        S      0:00 hald-addon-storage: polling /dev/sdb (every 2 sec)
 5086 ?        S      0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)
 5088 ?        S      0:00 hald-addon-storage: polling /dev/sdd (every 2 sec)
 5090 ?        S      0:00 hald-addon-storage: polling /dev/sde (every 2 sec)
 5092 ?        S      0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
 5105 ?        Ss     0:00 /usr/sbin/dhcdbd --system
 5120 ?        Ssl    0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
 5138 ?        Ss     0:00 avahi-daemon: registering [<user>-desktop.local]
 5139 ?        Ss     0:00 avahi-daemon: chroot helper
 5154 ?        Ss     0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
 5192 ?        Ss     0:00 /usr/sbin/cupsd
 5216 ?        Ss     0:00 /usr/sbin/hpiod
 5233 ?        S      0:00 python /usr/sbin/hpssd
 5305 ?        Ss     0:17 /usr/sbin/clamd
 5399 ?        Ss     0:00 /usr/bin/freshclam -p /var/run/clamav/freshclam.pid -d --quiet
 5412 ?        S      0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
 5437 ?        S<     0:00 [kondemand/0]
 5438 ?        S<     0:00 [kondemand/1]
 5484 ?        Ss     0:00 /usr/sbin/hcid -x -s
 5504 ?        S<     0:00 [krfcommd]
 5539 ?        Ss     0:00 /usr/sbin/atd
 5553 ?        Ss     0:00 /usr/sbin/cron
 5634 ?        Ss     0:00 /usr/bin/kdm
 5657 tty7     SLs+   0:40 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-2cPbEy
 5673 ?        S      0:00 -:0
 5723 ?        Ss     0:00 /bin/sh /usr/bin/x-session-manager
 5764 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
 5767 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
 5768 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
 5801 ?        S      0:00 start_kdeinit --new-startup +kcminit_startup
 5802 ?        Ss     0:00 kdeinit Running...                                   
 5805 ?        S      0:00 dcopserver [kdeinit] --nosid                         
 5808 ?        S      0:00 klauncher [kdeinit] --new-startup                    
 5810 ?        S      0:00 kded [kdeinit] --new-startup                         
 5824 ?        S      0:00 kwrapper ksmserver
 5826 ?        S      0:00 ksmserver [kdeinit]                                  
 5829 ?        S      0:01 kdesktop [kdeinit]                                   
 5831 ?        S      0:01 kicker [kdeinit]                                     
 5832 ?        S      0:00 kio_file [kdeinit] file /tmp/ksocket-<user>/klauncherIQRIic.slave-socket /tmp/ksocket-<user>/kdesktopYul2ec.slave-socket
 5836 ?        S      0:00 kio_uiserver [kdeinit]                               
 5842 ?        S      0:03 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c drkonqi -l 3 -f
 5845 ?        S      0:00 kaccess [kdeinit]                                    
 5848 ?        S      0:00 kmix [kdeinit] -session 10d8cecf96000111065458100000063760027_1184260922_545404
 5850 ?        S      0:00 katapult -session 10d9d39668000112680660600000081280032_1184260922_546110
 5852 ?        Sl     0:01 gaim --session 101b41a51bc104000118391391400000299940017
 5865 ?        S      0:00 konqueror [kdeinit] --preload                        
 5867 ?        S      0:00 aspell -a -S -C -Tutf8 --encoding=utf-8
 5876 ?        Ssl    0:00 /home/<user>/.kde/Autostart/beryl-manager
 5884 ?        S      0:00 knetworkmanager [kdeinit]                            
 5890 ?        S      0:00 knotify [kdeinit]                                    
 5892 ?        S      0:00 /usr/bin/passkey-agent --default /usr/lib/kdebluetooth/kbluepin
 5895 ?        S      0:00 klipper [kdeinit]                                    
 5898 ?        S      0:00 kbluetoothd --dontforceshow
 5899 ?        S      0:11 adept_notifier
 5904 ?        S      0:00 konqueror [kdeinit] --preload                        
 5973 ?        S      0:02 emerald --replace
 5984 ?        SL     0:12 beryl --skip-gl-yield
 6040 ?        S      0:01 conky
 6041 ?        S      0:00 /bin/sh /usr/bin/mozilla-thunderbird
 6045 ?        S      0:00 /bin/sh /usr/lib/mozilla-thunderbird/run-mozilla.sh /usr/lib/mozilla-thunderbird/mozilla-thunderbird-bin
 6049 ?        Sl     0:03 /usr/lib/mozilla-thunderbird/mozilla-thunderbird-bin
 6057 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 10
 6085 ?        S      0:00 /usr/bin/kdesud
 6101 ?        Ss     0:00 kdeinit Running...
 6106 ?        S      0:00 dcopserver [kdeinit] --nosid --suicide
 6109 ?        S      0:00 klauncher [kdeinit]
 6111 ?        S      0:00 kded [kdeinit]
 6168 ?        S      0:00 kio_uiserver [kdeinit]
 6172 ?        S      0:00 kio_file [kdeinit] file /tmp/ksocket-root/klauncher0kPtqb.slave-socket /tmp/ksocket-root/adept_managerxFOsab.slave-socket
 6206 ?        S      0:00 /bin/sh /opt/swiftfox/swiftfox
 6209 ?        S      0:00 /bin/sh /opt/swiftfox/run-mozilla.sh /opt/swiftfox/swiftfox-bin
 6213 ?        Sl     0:36 /opt/swiftfox/swiftfox-bin
 6248 ?        R      0:00 konsole [kdeinit]                                    
 6249 pts/2    Ss     0:00 /bin/bash
 6265 pts/2    R+     0:00 ps axww

```

and yeah tried right clicking, tried the old windows trick of rebooting lol 
it still sits there definatly

---

### Post by twiceasworn on 2007-07-12
```
5899 ?        S      0:11 adept_notifier
```

that is the culprit right there.  You can kill the process by going into top, then press k and type the pid (5899).

---

### Post by zanazzi on 2007-07-12
> **twiceasworn said:**
> ```
5899 ?        S      0:11 adept_notifier
```

that is the culprit right there.  You can kill the process by going into top, then press k and type the pid (5899).

sweet thank you very much :D

---

### Post by twiceasworn on 2007-07-12
You are very welcome.

---

