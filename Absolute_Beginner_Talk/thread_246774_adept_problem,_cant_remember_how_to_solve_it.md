---
title: "adept problem, cant remember how to solve it"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Naegling23 on 2006-08-29
I was trying to update some programs, and adept crashed in the middle of the process.  Now I get the following message when I try to start adept

You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

There are no open adept programs.  How do I "kill" this mysterious adept program that I cannot find?

---

### Post by chuckyp on 2006-08-29
Well you need to kill what ever adept program hung.  Make sure the update manager isn't running etc... Only one piece of software may be obtaining packages at a time using apt.

---

### Post by Naegling23 on 2006-08-29
update manager is not running.  I tried hitting ctrl+esc, but I cant find any program with apt or adept running, but I still get the error.  I tried restarting, and this did not solve the problem.

---

### Post by Naegling23 on 2006-08-29
This is the list generated when I run ps-e
PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  166 ?        00:00:00 pdflush
  167 ?        00:00:00 pdflush
  169 ?        00:00:00 aio/0
  168 ?        00:00:00 kswapd0
  756 ?        00:00:00 kseriod
 1770 ?        00:00:00 ata/0
 1771 ?        00:00:00 ata_hotplug/0
 1774 ?        00:00:00 scsi_eh_0
 1775 ?        00:00:00 scsi_eh_1
 1779 ?        00:00:00 scsi_eh_2
 1780 ?        00:00:00 scsi_eh_3
 1965 ?        00:00:00 khubd
 1960 ?        00:00:00 khpsbpkt
 1971 ?        00:00:00 knodemgrd_0
 1972 ?        00:00:00 knodemgrd_1
 2082 ?        00:00:00 kjournald
 2317 ?        00:00:00 udevd
 3182 ?        00:00:00 shpchpd_event
 3288 ?        00:00:00 scsi_eh_4
 3289 ?        00:00:00 usb-storage
 3422 ?        00:00:00 kgameportd
 3464 ?        00:00:00 cx88 tvaudio
 3953 ?        00:00:00 dhclient3
 4364 ?        00:00:00 acpid
 4451 ?        00:00:00 syslogd
 4477 ?        00:00:00 dd
 4479 ?        00:00:00 klogd
 4505 ?        00:00:00 hpiod
 4508 ?        00:00:00 python
 4555 ?        00:00:00 cupsd
 4589 ?        00:00:00 dbus-daemon
 4604 ?        00:00:01 hald
 4605 ?        00:00:00 hald-runner
 4611 ?        00:00:00 hald-addon-acpi
 4625 ?        00:00:00 hald-addon-keyb
 4629 ?        00:00:00 hald-addon-keyb
 4680 ?        00:00:00 hald-addon-keyb
 4690 ?        00:00:00 hald-addon-stor
 4691 ?        00:00:00 hald-addon-stor
 4693 ?        00:00:00 hald-addon-stor
 4694 ?        00:00:00 hald-addon-stor
 4696 ?        00:00:00 hald-addon-stor
 4697 ?        00:00:00 hald-addon-stor
 4699 ?        00:00:00 hald-addon-stor
 4700 ?        00:00:00 hald-addon-stor
 4703 ?        00:00:00 hald-addon-stor
 4704 ?        00:00:00 hald-addon-stor
 4745 ?        00:00:00 MoBlock-ipq.sh
 4817 ?        00:00:03 moblock
 4845 ?        00:00:00 mysqld_safe
 4918 ?        00:00:00 mysqld
 4919 ?        00:00:00 logger
 5016 ?        00:00:00 powernowd
 5083 ?        00:00:00 hcid
 5087 ?        00:00:00 sdpd
 5101 ?        00:00:00 krfcommd
 5115 ?        00:00:00 mdadm
 5154 ?        00:00:00 atd
 5168 ?        00:00:00 cron
 5516 ?        00:00:00 kdm
 5548 tty7     00:00:56 Xorg
 5567 tty1     00:00:00 getty
 5568 tty2     00:00:00 getty
 5569 tty3     00:00:00 getty
 5570 tty4     00:00:00 getty
 5571 tty5     00:00:00 getty
 5572 tty6     00:00:00 getty
 5869 ?        00:00:00 artsd
 6205 ?        00:00:00 kdm
 6211 ?        00:00:00 startkde
 6248 ?        00:00:00 ssh-agent
 6251 ?        00:00:00 dbus-daemon
 6252 ?        00:00:00 dbus-launch
 6280 ?        00:00:00 kdeinit
 6283 ?        00:00:00 dcopserver
 6285 ?        00:00:00 klauncher
 6287 ?        00:00:00 kded
 6293 ?        00:00:00 kwrapper
 6295 ?        00:00:00 ksmserver
 6296 ?        00:00:00 kwin
 6300 ?        00:00:00 kdesktop
 6302 ?        00:00:01 kicker
 6304 ?        00:00:00 kio_uiserver
 6305 ?        00:00:00 kio_system
 6313 ?        00:00:00 kio_file
 6315 ?        00:00:00 kio_file
 6318 ?        00:00:00 kio_thumbnail
 6320 ?        00:00:00 artsd
 6323 ?        00:00:00 kaccess
 6324 ?        00:00:00 katapult
 6329 ?        00:00:00 kwalletmanager
 6352 ?        00:00:00 kmix
 6355 ?        00:00:03 amarokapp
 6359 ?        00:00:00 kdesud
 6367 ?        00:00:00 cgwd
 6368 ?        00:00:13 firefox-bin
 6375 ?        00:00:02 adept_notifier
 6382 ?        00:00:00 kbluetoothd
 6386 ?        00:00:00 klipper
 6387 ?        00:00:00 knotify
 6393 ?        00:00:00 kio_file
 6394 ?        00:00:00 kio_file
 6395 ?        00:00:00 ruby
 6396 ?        00:00:00 ruby
 6412 ?        00:00:00 kio_file
 6413 ?        00:00:00 kio_file
 6414 ?        00:00:00 kio_file
 6417 ?        00:00:00 gconfd-2
 6453 ?        00:00:06 ksysguard
 6454 ?        00:00:01 ksysguardd
 6491 ?        00:00:00 konsole
 6492 pts/0    00:00:00 bash
 6510 pts/0    00:00:00 ps

killing adept notifier does not help the situation

---

### Post by chuckyp on 2006-08-29
Well restarting would have definately killed the alleged program.  I remember there being some sort of clean command perhaps man adept and search for clean.

---

### Post by Naegling23 on 2006-08-29
wow, fixed the problem, I had to run dpkg --configure -a or something like that, im not sure what I did, but its working now.

---

### Post by JohnnyMi25 on 2006-08-31
yes that is definately it!!!
I had the same issue
and all i did was  (kubuntu) run comand from the menu exactly this: dpkg -- configure.

it brought bac the original error that i recieved .
then i rebooted and voila!!!!!


thanks Naegling23  - greatful n00b


p.s. did i mention ILOVE LINUX!!

---

