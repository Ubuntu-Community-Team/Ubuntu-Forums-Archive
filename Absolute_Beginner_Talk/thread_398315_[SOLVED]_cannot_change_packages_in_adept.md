---
title: "[SOLVED] cannot change packages in adept"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by rbprogrammer on 2007-03-31
i want to install a package, ddclient to be exact, but the problem is that every time i open adept manager, i get this error in the attached [.png] image.

i tried restarting my computer, but that didnt work.  how do i change this so i can install ddclient?

---

### Post by taurus on 2007-03-31
Looks like you have something running in the background that ties up dpkg!  Open a terminal and paste the output of this command here.  Don't forget to close that adept  window manager first before you run this command.

```
ps -A
```

---

### Post by rbprogrammer on 2007-03-31
ps -A gives me:
```

$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
   71 ?        00:00:00 kseriod
  107 ?        00:00:00 pdflush
  108 ?        00:00:00 pdflush
  109 ?        00:00:00 kswapd0
  110 ?        00:00:00 aio/0
 1706 ?        00:00:00 khubd
 1807 ?        00:00:00 kjournald
 1880 ?        00:00:00 logd
 2026 ?        00:00:00 udevd
 2762 ?        00:00:00 shpchpd
 2804 ?        00:00:00 kpsmoused
 3190 ?        00:00:00 kjournald
 3192 ?        00:00:00 kjournald
 3312 ?        00:00:00 dhclient3
 3622 tty1     00:00:00 getty
 3623 tty2     00:00:00 getty
 3624 tty3     00:00:00 getty
 3628 tty4     00:00:00 getty
 3629 tty5     00:00:00 getty
 3630 tty6     00:00:00 getty
 3835 ?        00:00:00 acpid
 3934 ?        00:00:00 syslogd
 3960 ?        00:00:00 dd
 3962 ?        00:00:00 klogd
 3973 ?        00:00:00 kdm
 3989 tty7     00:00:17 Xorg
 4003 ?        00:00:00 kdm
 4004 ?        00:00:00 cupsd
 4045 ?        00:00:00 hpiod
 4050 ?        00:00:00 python
 4095 ?        00:00:00 apt-index-watch
 4111 ?        00:00:00 dbus-daemon
 4126 ?        00:00:02 hald
 4127 ?        00:00:00 hald-runner
 4133 ?        00:00:00 hald-addon-acpi
 4138 ?        00:00:00 hald-addon-keyb
 4142 ?        00:00:00 hald-addon-keyb
 4152 ?        00:00:00 hald-addon-stor
 4225 ?        00:00:00 sshd
 4268 ?        00:00:00 hcid
 4272 ?        00:00:00 sdpd
 4289 ?        00:00:00 krfcommd
 4322 ?        00:00:00 atd
 4335 ?        00:00:00 cron
 4362 ?        00:00:00 apache2
 4427 ?        00:00:00 apache2
 4428 ?        00:00:00 apache2
 4429 ?        00:00:00 apache2
 4430 ?        00:00:00 apache2
 4431 ?        00:00:00 apache2
 4432 ?        00:00:00 x-session-manag
 4471 ?        00:00:00 ssh-agent
 4474 ?        00:00:00 dbus-launch
 4475 ?        00:00:00 dbus-daemon
 4507 ?        00:00:00 start_kdeinit
 4508 ?        00:00:00 kdeinit
 4511 ?        00:00:00 dcopserver
 4514 ?        00:00:00 klauncher
 4516 ?        00:00:02 kded
 4522 ?        00:00:00 kwrapper
 4524 ?        00:00:00 ksmserver
 4525 ?        00:00:01 kwin
 4527 ?        00:00:01 kdesktop
 4529 ?        00:00:01 kicker
 4538 ?        00:00:00 kio_uiserver
 4553 ?        00:00:00 artsd
 4555 ?        00:00:00 kaccess
 4561 ?        00:00:00 kmix
 4562 ?        00:00:00 katapult
 4563 ?        00:00:04 konqueror
 4565 ?        00:04:50 ktorrent
 4569 ?        00:00:00 knotify
 4572 ?        00:00:00 passkey-agent
 4575 ?        00:00:02 adept_notifier
 4576 ?        00:00:00 kbluetoothd
 4578 ?        00:00:00 klipper
 4586 ?        00:00:00 aspell
 4885 ?        00:00:00 kio_file
 4887 ?        00:00:00 firefox
 4898 ?        00:00:00 run-mozilla.sh
 4902 ?        00:00:18 firefox-bin
 4910 ?        00:00:00 gconfd-2
 4921 ?        00:00:00 netstat <defunct>
 4922 ?        00:00:01 kwrite
 4924 ?        00:00:00 kio_http
 4973 ?        00:00:00 kio_http
 5108 ?        00:00:00 kio_media
 5110 ?        00:00:00 kio_file
 5136 ?        00:00:00 scsi_eh_1
 5137 ?        00:00:00 usb-storage
 5144 ?        00:00:00 kio_file
 5145 ?        00:00:00 kio_thumbnail
 5162 ?        00:00:00 hald-addon-stor
 5201 ?        00:00:00 kio_file
 5232 ?        00:00:01 konsole
 5233 pts/1    00:00:00 bash
 5254 pts/1    00:00:00 ps

```

---

### Post by taurus on 2007-03-31
Try

```
sudo kill -9 4575
sudo aptitude update
sudo aptitude install ddclient
```

---

### Post by rbprogrammer on 2007-03-31
ok, initially it didnt work.....

but then for some reason i restarted, and now i'm good :) 

thanks for the help taurus.

---

### Post by taurus on 2007-03-31
You're welcome.

---

