---
title: "Cannot Install - Update Mgr Stuck"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by scwinn on 2008-03-25
When I try to install any package in Kobuntu, I get an error that another installer is running. I have rebooted many times. No other installers are running. When I first installed however not all updates were applied correctly. I think update manager is in some kind of infinite loop although it does not appear.

I can find no task manager (as in Windowz)

So how do I make sure that no other package manager is actually running?:popcorn:

---

### Post by dcstar on 2008-03-25
> **scwinn said:**
> When I try to install any package in Kobuntu, I get an error that another installer is running. I have rebooted many times. No other installers are running. When I first installed however not all updates were applied correctly. I think update manager is in some kind of infinite loop although it does not appear.

I can find no task manager (as in Windowz)

So how do I make sure that no other package manager is actually running?:popcorn:

In a terminal, try:

```
sudo rm /var/lib/dpkg/lock
```

---

### Post by azimuth on 2008-03-25
I don't know about Kubuntu, but in Ubuntu they are called processes not tasks and can be found under System>Administation>System Monitor.

---

### Post by scwinn on 2008-03-25
I went to the terminal as suggested. Copied and pasted the command given . Tried to run Synaptic and got the following error..
[B]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

Is this a help?

Thanks!

---

### Post by knightcoder on 2008-03-25
Try using 

```
ps aux
```

to actually see what processes are running on your system
Check if there are two package manager applications running.

---

### Post by scwinn on 2008-03-26
Sorry since [I] don't know enough to tell... here is what I got....

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.3   2948  1856 ?        Ss   Mar25   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   Mar25   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Mar25   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        SN   Mar25   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Mar25   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   Mar25   0:03 [events/0]
root         7  0.0  0.0      0     0 ?        S<   Mar25   0:00 [khelper]
root        26  0.0  0.0      0     0 ?        S<   Mar25   0:00 [kblockd/0]
root        27  0.0  0.0      0     0 ?        S<   Mar25   0:00 [kacpid]
root        28  0.0  0.0      0     0 ?        S<   Mar25   0:00 [kacpi_notify]
root       108  0.0  0.0      0     0 ?        S<   Mar25   0:00 [kseriod]
root       129  0.0  0.0      0     0 ?        S    Mar25   0:00 [pdflush]
root       130  0.0  0.0      0     0 ?        S    Mar25   0:00 [pdflush]
root       131  0.0  0.0      0     0 ?        S<   Mar25   0:00 [kswapd0]
root       183  0.0  0.0      0     0 ?        S<   Mar25   0:00 [aio/0]
root      2003  0.0  0.0      0     0 ?        S<   Mar25   0:00 [ata/0]
root      2004  0.0  0.0      0     0 ?        S<   Mar25   0:00 [ata_aux]
root      2006  0.0  0.0      0     0 ?        S<   Mar25   0:00 [scsi_eh_0]
root      2007  0.0  0.0      0     0 ?        S<   Mar25   0:00 [scsi_eh_1]
root      2028  0.0  0.0      0     0 ?        S<   Mar25   0:00 [ksuspend_usbd]
root      2029  0.0  0.0      0     0 ?        S<   Mar25   0:00 [khubd]
root      2368  0.0  0.0      0     0 ?        S<   Mar25   0:00 [kjournald]
root      2573  0.0  0.2   3036  1384 ?        S<s  Mar25   0:00 /sbin/udevd --d
root      3488  0.0  0.0      0     0 ?        S<   Mar25   0:00 [kpsmoused]
root      3538  0.0  0.0      0     0 ?        S<   Mar25   0:00 [kgameportd]
root      3565  0.0  0.0      0     0 ?        S<   Mar25   0:00 [zd1211rw]
root      4209  0.0  0.1   1696   520 tty4     Ss+  Mar25   0:00 /sbin/getty 384
root      4210  0.0  0.1   1696   520 tty5     Ss+  Mar25   0:00 /sbin/getty 384
root      4215  0.0  0.1   1696   520 tty2     Ss+  Mar25   0:00 /sbin/getty 384
root      4218  0.0  0.1   1696   516 tty3     Ss+  Mar25   0:00 /sbin/getty 384
root      4221  0.0  0.1   1696   516 tty1     Ss+  Mar25   0:00 /sbin/getty 384
root      4226  0.0  0.0   1692   512 tty6     Ss+  Mar25   0:00 /sbin/getty 384
root      4395  0.0  0.2   2432  1320 ?        Ss   Mar25   0:00 /usr/sbin/acpid
root      4425  0.0  0.0      0     0 ?        S<   Mar25   0:00 [kondemand/0]
syslog    4505  0.0  0.1   1912   700 ?        Ss   Mar25   0:00 /sbin/syslogd -
root      4560  0.0  0.1   1836   536 ?        S    Mar25   0:00 /bin/dd bs 1 if
klog      4562  0.0  0.2   2496  1400 ?        Ss   Mar25   0:00 /sbin/klogd -P
105       4583  0.3  0.2   2908  1100 ?        Ss   Mar25   0:31 /usr/bin/dbus-d
root      4599  0.0  0.4  28948  2148 ?        Ssl  Mar25   0:04 /usr/sbin/Netwo
root      4613  0.0  0.2   3276  1272 ?        Ss   Mar25   0:00 /usr/sbin/Netwo
107       4632  0.0  0.7   5644  3764 ?        Ss   Mar25   0:04 /usr/sbin/hald
root      4633  0.0  0.2   3096  1052 ?        S    Mar25   0:00 hald-runner
107       4674  0.0  0.1   2156   892 ?        S    Mar25   0:00 hald-addon-keyb
107       4675  0.0  0.1   2160   888 ?        S    Mar25   0:00 hald-addon-keyb
107       4676  0.0  0.1   2156   888 ?        S    Mar25   0:00 hald-addon-keyb
107       4677  0.0  0.1   2160   892 ?        S    Mar25   0:00 hald-addon-keyb
107       4680  0.0  0.1   2160   880 ?        S    Mar25   0:00 hald-addon-acpi
root      4731  0.0  0.1   2944   628 ?        Ss   Mar25   0:00 /usr/bin/kdm -c
root      4751  4.5  5.7  30720 29544 tty7     Ss+  Mar25   6:16 /usr/bin/X -br
107       4762  0.0  0.2   3260  1188 ?        S    Mar25   0:01 hald-addon-stor
107       4765  0.0  0.2   3260  1184 ?        S    Mar25   0:02 hald-addon-stor
root      4766  0.0  0.5   5956  2612 ?        Ss   Mar25   0:00 /usr/sbin/cupsd
root      4767  0.0  0.2   3928  1528 ?        S    Mar25   0:00 -:0
avahi     4880  0.0  0.2   2732  1376 ?        Ss   Mar25   0:00 avahi-daemon: r
avahi     4881  0.0  0.0   2732   460 ?        Ss   Mar25   0:00 avahi-daemon: c
root      4895  0.0  0.1   1996   896 ?        Ss   Mar25   0:00 /usr/sbin/dhcdb
root      4915  0.0  0.2   2920  1184 ?        Ss   Mar25   0:00 /usr/sbin/hcid
root      4925  0.0  0.2   2840  1204 ?        S    Mar25   0:00 /usr/lib/blueto
root      4931  0.0  0.0      0     0 ?        S<   Mar25   0:00 [krfcommd]
root      4944  0.0  0.1   2764   972 ?        S    Mar25   0:00 /usr/lib/blueto
daemon    4965  0.0  0.0   1956   424 ?        Ss   Mar25   0:00 /usr/sbin/atd
root      4979  0.0  0.1   2336   912 ?        Ss   Mar25   0:00 /usr/sbin/cron
dad       5071  0.0  0.1   1756   540 ?        Ss   Mar25   0:00 /bin/sh /usr/bi
dad       5113  0.0  0.1   4436   544 ?        Ss   Mar25   0:00 /usr/bin/ssh-ag
root      5144  0.0  0.0   1536   144 ?        S    Mar25   0:00 start_kdeinit -
dad       5145  0.0  0.8  26028  4436 ?        Ss   Mar25   0:00 kdeinit Running
dad       5148  0.0  0.6  25848  3104 ?        S    Mar25   0:05 dcopserver [kde
dad       5151  0.0  1.2  27072  6616 ?        S    Mar25   0:00 klauncher [kdei
dad       5153  0.0  3.0  35296 15972 ?        S    Mar25   0:07 kded [kdeinit]
dad       5158  0.0  0.0   1676   368 ?        S    Mar25   0:00 kwrapper ksmser
dad       5160  0.0  1.6  27272  8284 ?        S    Mar25   0:00 ksmserver [kdei
dad       5161  0.1  2.3  30592 11940 ?        S    Mar25   0:16 kwin [kdeinit]
dad       5163  0.1  4.2  40116 22104 ?        S    Mar25   0:15 kdesktop [kdein
dad       5165  0.3  3.5  35732 18216 ?        S    Mar25   0:30 kicker [kdeinit
dad       5169  0.0  2.4  30964 12560 ?        S    Mar25   0:00 kio_uiserver [k
dad       5184  0.1  1.3  20912  7032 ?        S    Mar25   0:16 /usr/bin/artsd
dad       5187  0.0  1.4  26804  7604 ?        S    Mar25   0:00 kaccess [kdeini
dad       5190  0.0  2.4  31440 12388 ?        S    Mar25   0:00 kmix [kdeinit]
dad       5191  0.0  3.1  29872 16244 ?        S    Mar25   0:00 katapult -sessi
dad       5197  0.0  0.4   8140  2204 ?        S    Mar25   0:00 aspell -a -S -C
dad       5199  0.0  1.9  33928 10284 ?        S    Mar25   0:00 knotify [kdeini
dad       5205  0.0  1.8  28092  9360 ?        S    Mar25   0:00 klipper [kdeini
dad       5206  0.0  2.2  30956 11672 ?        S    Mar25   0:00 /usr/bin/python
dad       5209  0.4  2.1  32480 11136 ?        S    Mar25   0:39 knetworkmanager
dad       5210  0.7  2.8  33876 14728 ?        S    Mar25   1:02 adept_notifier
root      5220  0.0  0.2   3848  1508 ?        S    Mar25   0:00 /sbin/wpa_suppl
dhcp      5230  0.0  0.2   2416  1168 ?        S    Mar25   0:00 /sbin/dhclient
root      5508  0.5  1.3  20920  7048 ?        S    Mar25   0:43 /usr/bin/artsd
dad       6371  0.0  0.1   1756   524 ?        S    Mar25   0:00 /bin/sh /usr/bi
dad       6383  0.0  0.1   1756   532 ?        S    Mar25   0:00 /bin/sh /usr/li
dad       6387 17.7 19.6 256720 101256 ?       Sl   Mar25  15:52 /usr/lib/firefo
dad       6414  0.0  1.0  27140  5664 ?        S    Mar25   0:00 kio_file [kdein
dad       6419  0.0  3.5  38496 18468 ?        S    Mar25   0:00 konqueror [kdei
dad       7242 13.5  2.9  34068 15424 ?        S    00:08   0:00 konsole [kdeini
dad       7243  7.2  0.5   5608  3000 pts/1    Ss   00:08   0:00 /bin/bash
dad       7259  0.0  0.1   2620  1000 pts/1    R+   00:09   0:00 ps aux

---

### Post by Oldsoldier2003 on 2008-03-26
> **scwinn said:**
> I went to the terminal as suggested. Copied and pasted the command given . Tried to run Synaptic and got the following error..
[B]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

Is this a help?

Thanks!
```
sudo dpkg --configure -a
```
that should straighten out the issue. if not also do

```
sudo apt-get install -f
```

---

