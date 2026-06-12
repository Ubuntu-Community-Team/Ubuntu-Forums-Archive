---
title: "Adept Manager problems"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by ineedmunchies on 2006-12-17
I open Adept manager and get this message:

"You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one."

There are no other programs running that I can see, so I have no idea why this is happening.

It may have something to do with the fact I was trying to install a Java runtime environment which stalled so I canceled it. Then adept wouldn't open so I restarted the computer. Now its only opening in readonly mode.

help please anyone??
Greatly appreciated

---

### Post by taurus on 2006-12-17
What's the output of this command from a terminal?

```
ps -A
```

---

### Post by ineedmunchies on 2006-12-17
it's:
```
PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  116 ?        00:00:00 kseriod
  152 ?        00:00:00 pdflush
  153 ?        00:00:00 pdflush
  154 ?        00:00:00 kswapd0
  155 ?        00:00:00 aio/0
 1624 ?        00:00:00 ata/0
 1626 ?        00:00:00 scsi_eh_0
 1627 ?        00:00:00 scsi_eh_1
 1742 ?        00:00:00 khubd
 1827 ?        00:00:00 kjournald
 1903 ?        00:00:00 logd
 2016 ?        00:00:00 udevd
 2757 ?        00:00:00 shpchpd
 2898 ?        00:00:00 kpsmoused
 2935 ?        00:00:00 kgameportd
 3064 ?        00:00:00 dhclient3
 3444 tty1     00:00:00 getty
 3445 tty2     00:00:00 getty
 3446 tty3     00:00:00 getty
 3447 tty4     00:00:00 getty
 3448 tty5     00:00:00 getty
 3449 tty6     00:00:00 getty
 3658 ?        00:00:00 acpid
 3781 ?        00:00:00 dd
 3783 ?        00:00:00 klogd
 3796 ?        00:00:00 kdm
 3803 tty7     00:00:38 Xorg
 3813 ?        00:00:00 kdm
 3848 ?        00:00:00 hpiod
 3851 ?        00:00:00 python
 3896 ?        00:00:00 apt-index-watch
 3912 ?        00:00:00 dbus-daemon
 3927 ?        00:00:01 hald
 3928 ?        00:00:00 hald-runner
 3934 ?        00:00:00 hald-addon-acpi
 3939 ?        00:00:00 hald-addon-keyb
 3951 ?        00:00:00 hald-addon-stor
 4021 ?        00:00:00 hcid
 4028 ?        00:00:00 sdpd
 4039 ?        00:00:00 krfcommd
 4072 ?        00:00:00 atd
 4085 ?        00:00:00 cron
 4155 ?        00:00:00 x-session-manag
 4194 ?        00:00:00 ssh-agent
 4197 ?        00:00:00 dbus-launch
 4198 ?        00:00:00 dbus-daemon
 4230 ?        00:00:00 start_kdeinit
 4231 ?        00:00:00 kdeinit
 4234 ?        00:00:00 dcopserver
 4237 ?        00:00:00 klauncher
 4239 ?        00:00:02 kded
 4245 ?        00:00:00 kwrapper
 4247 ?        00:00:00 ksmserver
 4248 ?        00:00:02 kwin
 4250 ?        00:00:01 kdesktop
 4252 ?        00:00:04 kicker
 4253 ?        00:00:00 kio_file
 4256 ?        00:00:00 kio_uiserver
 4271 ?        00:00:01 artsd
 4273 ?        00:00:00 kaccess
 4277 ?        00:00:00 kmix
 4278 ?        00:00:00 katapult
 4284 ?        00:00:00 knotify
 4286 ?        00:00:00 passkey-agent
 4289 ?        00:00:00 kbluetoothd
 4292 ?        00:00:00 klipper
 4293 ?        00:00:06 adept_notifier
 4298 ?        00:00:00 aspell
 4306 ?        00:00:00 kdesud
 4353 ?        00:00:31 firefox-bin
 4362 ?        00:00:00 gconfd-2
 4446 ?        00:00:00 cupsd
 4655 ?        00:00:00 syslogd
 4706 ?        00:00:21 kopete
 4708 ?        00:00:00 kwalletmanager
 4712 ?        00:00:00 kio_http
 4720 ?        00:00:04 konqueror
 4721 ?        00:00:00 kio_file
 4722 ?        00:00:00 kio_file
 4723 ?        00:00:00 kio_file
 4724 ?        00:00:00 kio_file
 4725 ?        00:00:00 kio_http
 4729 ?        00:00:00 kio_http
 4730 ?        00:00:00 kio_http
 4738 ?        00:00:00 kio_http
 4744 ?        00:00:00 kio_http
 4745 ?        00:00:00 kio_http
 4749 ?        00:00:00 kio_http
 4758 ?        00:00:00 kio_http
 4764 ?        00:00:00 kio_http
 4829 ?        00:00:00 konsole
 4830 pts/1    00:00:00 bash
 4846 pts/1    00:00:00 ps

```

---

### Post by taurus on 2006-12-17
This could be the one!!!

```
4293 ?        00:00:06 adept_notifier
```
Kill it and and run aptitude again to see if you still have the same problem!

```
sudo kill -9 4293
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ineedmunchies on 2006-12-17
ahhh well this time it just didnt open at all, then after waiting i tried to open it again, and the same message came up

---

### Post by Jucato on 2006-12-17
@Taurus: There is no need to kill adept_notifier as it runs silently in the background and doesn't lock up APT. It's like the update manager of Synaptic. Now that he has killed it and didn't run it before he logs out (presuming he has "Restore previous session" enabled), it won't run anymore and won't automatically be informed of updates.

@ineedmunchies
```
sudo dpkg --configure -a
```
might help

---

### Post by KarlXII on 2007-01-05
Here's my working solution to the adept lock file prob: [http://www.ubuntuforums.org/showthread.php?t=331923](http://www.ubuntuforums.org/showthread.php?t=331923)

---

### Post by zain7478 on 2007-10-22
hi,
I put a new respository ulr - i guess wrongly and get this messege...

The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

how could i reinstall the default configuration - or to get things working again?
couldnt get the add remove programs working either.

any help is highly appreciate, for a newbie :confused:

---

### Post by zain7478 on 2007-10-22
:):) hhaaa...
just got the answer

sudo kwrite /etc/apt/sources.list

delete the last line or what ever you think causes the problem..
:popcorn:

---

