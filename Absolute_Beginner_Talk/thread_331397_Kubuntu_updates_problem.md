---
title: "Kubuntu updates problem"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2007-01-04
After my friend installed kubuntu 6.10 he updated it and after he installed automatix2 to put some programs he wanted about 10 programs.In the end of the installation automatix poped up an error that some of the programs were not installed and after all that another update poped up,we clicked on it to download the updates put it poped an error that was saying that another program was using adept updater.Now every time we turn on the kubuntu it says that has an update put it cannot download it because another program was using adept updater.

what we have to do to fix the problem ???

---

### Post by taurus on 2007-01-04
Probably another program, adept, running in the background.  At the prompt, paste the output of this command here?

```
ps -A
```

---

### Post by fasoulas on 2007-01-04
> **taurus said:**
> Probably another program, adept, running in the background.  At the prompt, paste the output of this command here?

```
ps -A
```

  PID TTY          TIME CMD     1 ?        00:00:01 init     2 ?        00:00:00 migration/0     3 ?        00:00:00 ksoftirqd/0     4 ?        00:00:00 watchdog/0     5 ?        00:00:00 events/0     6 ?        00:00:00 khelper     7 ?        00:00:00 kthread     9 ?        00:00:00 kblockd/0    10 ?        00:00:00 kacpid    11 ?        00:00:00 kacpi_notify    86 ?        00:00:00 kseriod   117 ?        00:00:00 pdflush   118 ?        00:00:00 pdflush   119 ?        00:00:00 kswapd0   120 ?        00:00:00 aio/0  1718 ?        00:00:00 khubd  1783 ?        00:00:00 kjournald  1860 ?        00:00:00 logd  2006 ?        00:00:00 udevd  2718 ?        00:00:00 shpchpd  2759 ?        00:00:00 kgameportd  2918 ?        00:00:00 kpsmoused  3491 tty1     00:00:00 getty  3492 tty2     00:00:00 getty  3493 tty3     00:00:00 getty  3494 tty4     00:00:00 getty  3495 tty5     00:00:00 getty  3496 tty6     00:00:00 getty  3699 ?        00:00:00 acpid  3819 ?        00:00:00 dd  3821 ?        00:00:00 klogd  3834 ?        00:00:00 kdm  3862 tty7     00:04:49 Xorg  3865 ?        00:00:00 kdm  3886 ?        00:00:00 hpiod  3891 ?        00:00:00 python  3952 ?        00:00:00 dbus-daemon  3967 ?        00:00:03 hald  3968 ?        00:00:00 hald-runner  3975 ?        00:00:00 hald-addon-acpi  3978 ?        00:00:00 hald-addon-keyb  3994 ?        00:00:02 hald-addon-stor  4074 ?        00:00:00 hcid  4081 ?        00:00:00 sdpd  4092 ?        00:00:00 krfcommd  4124 ?        00:00:00 atd  4137 ?        00:00:00 cron  4209 ?        00:00:00 x-session-manag  4248 ?        00:00:00 ssh-agent  4284 ?        00:00:00 start_kdeinit  4285 ?        00:00:00 kdeinit  4288 ?        00:00:01 dcopserver  4291 ?        00:00:00 klauncher  4293 ?        00:00:04 kded  4299 ?        00:00:00 kwrapper  4301 ?        00:00:01 ksmserver  4302 ?        00:00:14 kwin  4304 ?        00:01:20 kdesktop  4306 ?        00:00:27 kicker  4310 ?        00:00:02 kio_uiserver  4327 ?        00:00:00 kaccess  4333 ?        00:00:01 kmix  4334 ?        00:00:01 katapult  4342 ?        00:00:00 passkey-agent  4344 ?        00:00:01 knotify  4349 ?        00:00:01 kbluetoothd  4360 ?        00:00:00 aspell  4385 ?        00:00:00 kdesud  4552 ?        00:00:00 cupsd  7231 ?        00:00:00 syslogd  7385 ?        00:00:07 konqueror  7627 ?        00:00:00 kio_file  7707 ?        00:00:11 artsd  8385 ?        00:00:04 konsole  8386 pts/1    00:00:00 bash  8472 ?        00:00:00 dcopserver  8481 ?        00:00:02 firefox-bin  8491 ?        00:00:00 artsd  8494 ?        00:00:00 gconfd-2  8503 pts/1    00:00:00 ps  **these is the result of the command but idon't now how to find the problem**

---

### Post by fasoulas on 2007-01-04
I really need some help here!!!!!

---

### Post by taurus on 2007-01-04
> **fasoulas said:**
> PID TTY          TIME CMD     1 ?        00:00:01 init     2 ?        00:00:00 migration/0     3 ?        00:00:00 ksoftirqd/0     4 ?        00:00:00 watchdog/0     5 ?        00:00:00 events/0     6 ?        00:00:00 khelper     7 ?        00:00:00 kthread     9 ?        00:00:00 kblockd/0    10 ?        00:00:00 kacpid    11 ?        00:00:00 kacpi_notify    86 ?        00:00:00 kseriod   117 ?        00:00:00 pdflush   118 ?        00:00:00 pdflush   119 ?        00:00:00 kswapd0   120 ?        00:00:00 aio/0  1718 ?        00:00:00 khubd  1783 ?        00:00:00 kjournald  1860 ?        00:00:00 logd  2006 ?        00:00:00 udevd  2718 ?        00:00:00 shpchpd  2759 ?        00:00:00 kgameportd  2918 ?        00:00:00 kpsmoused  3491 tty1     00:00:00 getty  3492 tty2     00:00:00 getty  3493 tty3     00:00:00 getty  3494 tty4     00:00:00 getty  3495 tty5     00:00:00 getty  3496 tty6     00:00:00 getty  3699 ?        00:00:00 acpid  3819 ?        00:00:00 dd  3821 ?        00:00:00 klogd  3834 ?        00:00:00 kdm  3862 tty7     00:04:49 Xorg  3865 ?        00:00:00 kdm  3886 ?        00:00:00 hpiod  3891 ?        00:00:00 python  3952 ?        00:00:00 dbus-daemon  3967 ?        00:00:03 hald  3968 ?        00:00:00 hald-runner  3975 ?        00:00:00 hald-addon-acpi  3978 ?        00:00:00 hald-addon-keyb  3994 ?        00:00:02 hald-addon-stor  4074 ?        00:00:00 hcid  4081 ?        00:00:00 sdpd  4092 ?        00:00:00 krfcommd  4124 ?        00:00:00 atd  4137 ?        00:00:00 cron  4209 ?        00:00:00 x-session-manag  4248 ?        00:00:00 ssh-agent  4284 ?        00:00:00 start_kdeinit  4285 ?        00:00:00 kdeinit  4288 ?        00:00:01 dcopserver  4291 ?        00:00:00 klauncher  4293 ?        00:00:04 kded  4299 ?        00:00:00 kwrapper  4301 ?        00:00:01 ksmserver  4302 ?        00:00:14 kwin  4304 ?        00:01:20 kdesktop  4306 ?        00:00:27 kicker  4310 ?        00:00:02 kio_uiserver  4327 ?        00:00:00 kaccess  4333 ?        00:00:01 kmix  4334 ?        00:00:01 katapult  4342 ?        00:00:00 passkey-agent  4344 ?        00:00:01 knotify  4349 ?        00:00:01 kbluetoothd  4360 ?        00:00:00 aspell  4385 ?        00:00:00 kdesud  4552 ?        00:00:00 cupsd  7231 ?        00:00:00 syslogd  7385 ?        00:00:07 konqueror  7627 ?        00:00:00 kio_file  7707 ?        00:00:11 artsd  8385 ?        00:00:04 konsole  8386 pts/1    00:00:00 bash  8472 ?        00:00:00 dcopserver  8481 ?        00:00:02 firefox-bin  8491 ?        00:00:00 artsd  8494 ?        00:00:00 gconfd-2  8503 pts/1    00:00:00 ps  **these is the result of the command but idon't now how to find the problem**

I can't read this whole thing like this (and I am not going to try)!  Can you  at least paste the output like the way it looks from the terminal!!!

---

