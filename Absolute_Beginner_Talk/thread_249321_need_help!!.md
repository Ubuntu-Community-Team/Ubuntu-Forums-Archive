---
title: "need help!!"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by jocho on 2006-09-02
it probably seems to be very stupid, but till now i can´t find the solution!...](*,). when i want to add or remove appears a messange like this:"Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one"...i did all i could do!!](*,) . what do you suggest me in order to solve this. i would appreciate it!

---

### Post by taurus on 2006-09-02
Sounds like you have synaptic running in the background so you need to kill it!!!  You need to know the PID, process ID, and you can do that with this command.

```
ps -A
```
The first column is what you after and assuming it's 1234, then kill it with

```
sudo kill -9 1234
```
And if you're not sure which one it is, just post the output of "ps -a" here then...

---

### Post by jocho on 2006-09-02
the output of "ps -a" is:

jocho@jocho-laptop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  171 ?        00:00:00 pdflush
  172 ?        00:00:00 pdflush
  174 ?        00:00:00 aio/0
  173 ?        00:00:00 kswapd0
  761 ?        00:00:00 kseriod
 1867 ?        00:00:00 khubd
 1978 ?        00:00:00 kjournald
 2204 ?        00:00:00 udevd
 2979 ?        00:00:00 shpchpd_event
 3134 ?        00:00:00 pccardd
 3155 ?        00:00:00 pccardd
 3255 ?        00:00:00 dhclient3
 3969 ?        00:00:00 acpid
 4084 ?        00:00:00 dd
 4086 ?        00:00:00 klogd
 4124 ?        00:00:00 hpiod
 4127 ?        00:00:00 python
 4199 ?        00:00:00 dbus-daemon
 4214 ?        00:00:07 hald
 4215 ?        00:00:00 hald-runner
 4220 ?        00:00:00 hald-addon-acpi
 4275 ?        00:00:00 hald-addon-keyb
 4290 ?        00:00:00 hald-addon-stor
 4291 ?        00:00:01 hald-addon-stor
 4317 ?        00:00:00 dirmngr
 4355 ?        00:00:00 powernowd
 4400 ?        00:00:00 hcid
 4404 ?        00:00:00 sdpd
 4419 ?        00:00:00 krfcommd
 4432 ?        00:00:00 mdadm
 4467 ?        00:00:00 atd
 4480 ?        00:00:00 cron
 4840 ?        00:00:00 kdm
 4862 tty7     00:07:34 Xorg
 4894 tty1     00:00:00 getty
 4895 tty2     00:00:00 getty
 4896 tty3     00:00:00 getty
 4897 tty4     00:00:00 getty
 4898 tty5     00:00:00 getty
 4899 tty6     00:00:00 getty
 4913 ?        00:00:00 kdm
 4934 ?        00:00:00 startkde
 4981 ?        00:00:00 ssh-agent
 4984 ?        00:00:00 dbus-launch
 4985 ?        00:00:00 dbus-daemon
 5012 ?        00:00:00 kdeinit
 5015 ?        00:00:03 dcopserver
 5017 ?        00:00:00 klauncher
 5019 ?        00:00:06 kded
 5021 ?        00:00:00 gam_server
 5029 ?        00:00:47 artsd
 5031 ?        00:00:00 kaccess
 5032 ?        00:00:00 kwrapper
 5034 ?        00:00:00 ksmserver
 5040 ?        00:00:07 kwin
 5048 ?        00:00:19 kdesktop
 5051 ?        00:01:16 kicker
 5056 ?        00:00:00 klipper
 5059 ?        00:00:00 kbluetoothd
 5061 ?        00:00:00 irkick
 5063 ?        00:00:08 adept_notifier
 5080 ?        00:00:00 katapult
 5081 ?        00:00:00 kacpid-work-0
 5082 ?        00:00:00 kacpid-work-1
 5084 ?        00:00:03 kscd
 5086 ?        00:00:00 kio_uiserver
 5088 ?        00:00:00 kwalletmanager
 5099 ?        00:00:09 akregator
 5101 ?        00:00:01 kmix
 5102 ?        00:00:00 evolution-alarm
 5104 ?        00:00:00 knotify
 5125 ?        00:01:32 kopete
 5128 ?        00:07:27 amarokapp
 5129 ?        00:00:01 gaim
 5131 ?        00:00:00 gconfd-2
 5138 ?        00:00:00 bonobo-activati
 5141 ?        00:00:00 evolution-excha
 5144 ?        00:00:00 evolution-data-
 5315 ?        00:00:00 cupsd
 5457 ?        00:00:00 syslogd
 5691 ?        00:04:06 firefox-bin
 7483 ?        00:00:18 konqueror
 7486 ?        00:00:00 kio_file
 7604 ?        00:00:00 amarokapp
 7721 ?        00:00:00 kdesud
 7788 ?        00:00:00 kio_http
 7889 ?        00:00:01 konsole
 7890 pts/1    00:00:00 bash
 7929 ?        00:00:00 kio_http
 7952 ?        00:00:00 kio_http
 7953 ?        00:00:00 kio_http
 7954 ?        00:00:00 kio_http
 7955 ?        00:00:00 kio_http
 7956 ?        00:00:00 kio_http
 7958 ?        00:00:00 kio_http
 7982 ?        00:00:00 kio_http
 7983 ?        00:00:00 kio_http
 8004 pts/1    00:00:00 ps
...it don´t shows the kill -9 1234 that you said.

---

### Post by HanZo on 2006-09-02
> ...it don´t shows the kill -9 1234 that you said.
Reply With Quote
he meant that if you see for example spt-get running, then you look at the number it has, example: 1234 ? 00:00:00 apt-get, then you just have to type kill -9 1234 to terminate the application.

---

