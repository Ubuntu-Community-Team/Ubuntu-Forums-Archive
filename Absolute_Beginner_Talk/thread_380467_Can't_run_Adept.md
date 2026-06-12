---
title: "Can't run Adept"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by hoarsecourser on 2007-03-09
I was installing some new packages with adept and my system froze...I restarted, and now I can't run Adept or any of it's other managers (update, etc) because it keeps telling me that another Adept or apt program is running...How do I find and kill this program so i can update my computer?

---

### Post by taurus on 2007-03-09
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by invalid on 2007-03-09
You can see running processes with ```
ps -e
```
You can kill processes using ```
sudo kill -9 <pid>
``` or```
sudo killall <appname>
```

---

### Post by hoarsecourser on 2007-03-09
the output is as follows:


  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 migration/1
    6 ?        00:00:00 ksoftirqd/1
    7 ?        00:00:00 watchdog/1
    8 ?        00:00:00 events/0
    9 ?        00:00:00 events/1
   10 ?        00:00:00 khelper
   11 ?        00:00:00 kthread
   14 ?        00:00:00 kblockd/0
   15 ?        00:00:00 kblockd/1
   16 ?        00:00:00 kacpid
   17 ?        00:00:00 kacpi_notify
  165 ?        00:00:00 kseriod
  198 ?        00:00:00 pdflush
  199 ?        00:00:00 pdflush
  200 ?        00:00:00 kswapd0
  201 ?        00:00:00 aio/0
  202 ?        00:00:00 aio/1
  834 ?        00:00:00 kirqd
 1695 ?        00:00:00 ata/0
 1697 ?        00:00:00 ata/1
 1702 ?        00:00:00 scsi_eh_0
 1703 ?        00:00:00 scsi_eh_1
 1830 ?        00:00:00 khubd
 1896 ?        00:00:00 kjournald
 1980 ?        00:00:00 logd
 2126 ?        00:00:00 udevd
 2902 ?        00:00:00 shpchpd
 3013 ?        00:00:00 kpsmoused
 3465 ?        00:00:00 dhclient3
 3707 tty1     00:00:00 getty
 3709 tty2     00:00:00 getty
 3710 tty3     00:00:00 getty
 3711 tty4     00:00:00 getty
 3712 tty5     00:00:00 getty
 3713 tty6     00:00:00 getty
 3937 ?        00:00:00 acpid
 4033 ?        00:00:00 syslogd
 4059 ?        00:00:00 dd
 4061 ?        00:00:00 klogd
 4074 ?        00:00:00 kdm
 4092 tty7     00:00:54 Xorg
 4104 ?        00:00:00 cupsd
 4105 ?        00:00:00 kdm
 4124 ?        00:00:00 hpiod
 4127 ?        00:00:00 python
 4174 ?        00:00:00 apt-index-watch
 4190 ?        00:00:00 dbus-daemon
 4207 ?        00:00:01 hald
 4208 ?        00:00:00 hald-runner
 4214 ?        00:00:00 hald-addon-acpi
 4220 ?        00:00:00 hald-addon-keyb
 4235 ?        00:00:00 hald-addon-stor
 4279 ?        00:00:00 ondemand
 4321 ?        00:00:00 hcid
 4326 ?        00:00:00 sdpd
 4339 ?        00:00:00 krfcommd
 4371 ?        00:00:00 atd
 4384 ?        00:00:00 cron
 4456 ?        00:00:00 x-session-manag
 4495 ?        00:00:00 ssh-agent
 4498 ?        00:00:00 dbus-launch
 4499 ?        00:00:00 dbus-daemon
 4529 ?        00:00:00 start_kdeinit
 4530 ?        00:00:00 kdeinit
 4533 ?        00:00:00 dcopserver
 4536 ?        00:00:00 klauncher
 4538 ?        00:00:02 kded
 4544 ?        00:00:00 kwrapper
 4546 ?        00:00:00 ksmserver
 4547 ?        00:00:02 kwin
 4549 ?        00:00:02 kdesktop
 4551 ?        00:00:03 kicker
 4553 ?        00:00:00 kio_file
 4555 ?        00:00:00 kio_uiserver
 4570 ?        00:00:07 artsd
 4573 ?        00:00:00 kaccess
 4578 ?        00:00:00 kmix
 4579 ?        00:00:00 katapult
 4585 ?        00:00:00 passkey-agent
 4590 ?        00:00:00 kbluetoothd
 4591 ?        00:00:00 knotify
 4593 ?        00:00:00 klipper
 4596 ?        00:00:00 aspell
 4606 ?        00:00:00 kdesud
 4652 ?        00:00:30 konqueror
 4793 ?        00:00:00 kdesktop <defunct>
 4804 ?        00:00:00 kdeinit
 4807 ?        00:00:00 dcopserver
 4810 ?        00:00:00 klauncher
 4812 ?        00:00:00 kded
 4822 ?        00:00:00 kio_file
 4839 ?        00:00:00 korgac
 4956 ?        00:00:01 kwalletmanager
 5139 ?        00:00:00 kio_http
 5145 ?        00:00:00 kio_http
 5146 ?        00:00:00 kio_http
 5156 ?        00:00:00 kio_http
 5182 ?        00:00:00 kio_http
 5224 ?        00:00:00 kio_file
 5237 ?        00:00:00 kio_http
 5280 ?        00:00:00 konsole
 5285 pts/2    00:00:00 bash
 5303 pts/2    00:00:00 ps

---

### Post by hoarsecourser on 2007-03-09
which process do i want to kill? and can I do it?  I couldn't run KSysGuard with sudo, kdesu or gksu

Sorry, I forgot to mention that I'm running Kubuntu (Ubuntu installer kept freezing during partition)

---

