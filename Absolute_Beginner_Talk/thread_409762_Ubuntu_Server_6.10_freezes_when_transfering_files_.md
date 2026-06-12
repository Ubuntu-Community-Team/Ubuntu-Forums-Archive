---
title: "Ubuntu Server 6.10 freezes when transfering files to/from"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-14
I am running Ubuntu Server 6.10 as a file server.  I have the primary drive, plus 3 250GB secondary drives.  I just got all this up and running, formatted, shared, etc and now I am trying to move some files from one secondary drive to another... each time I try this, it starts going and will lock up the whole machine after 5-10 minutes, forcing me to do a hard shut down to get back in.

Does Ubuntu keep some sort of system log, like a Windows log agent, where I can look and see if there is an error being reported as the cause of the system freeze?  Anyone have any ideas how to stop this?  I am affraid that I am going to mess up my partition with all the hard reboots...

---

### Post by speeves on 2007-04-14
All the logs are kept in:

/var/log

I would check the syslog and dmesg to see if you see something there.  If you don't see anything there, then try debug or kern.log.  (I'm just guessing on the last two).

---

### Post by kc5hwb on 2007-04-15
Ok, this was the last log entry at the end of the day yesterday after I rebooted for the last time and it froze up again while trying to copy some files.  I simply shut it off and went to bed after this last time.  Does any of this make sense to someone?

```
Apr 14 22:34:31 josephus syslogd 1.4.1#18ubuntu6: restart.
Apr 14 22:34:31 josephus kernel: Inspecting /boot/System.map-2.6.17-10-server
Apr 14 22:34:32 josephus kernel: Loaded 22821 symbols from /boot/System.map-2.6$
Apr 14 22:34:32 josephus kernel: Symbols match kernel version 2.6.17.
Apr 14 22:34:32 josephus kernel: No module symbols loaded - kernel modules not $
Apr 14 22:34:32 josephus kernel: [42950872.350000] apm: BIOS version 1.2 Flags $
Apr 14 22:34:32 josephus kernel: [42950872.350000] apm: disabled on user reques$
Apr 14 22:34:32 josephus kernel: [42950883.750000] ibm_acpi: ec object not found
Apr 14 22:34:32 josephus kernel: [42950884.150000] powernow: No powernow capabi$
Apr 14 22:34:33 josephus hpiod: 1.6.9 accepting connections at 2208...
Apr 14 22:34:34 josephus kernel: [42950886.490000] apm: BIOS version 1.2 Flags $
Apr 14 22:34:34 josephus kernel: [42950886.490000] apm: disabled on user reques$
Apr 14 22:34:43 josephus hcid[6050]: Bluetooth HCI daemon
Apr 14 22:34:43 josephus hcid[6050]: Register path:/org/bluez fallback:1
Apr 14 22:34:43 josephus sdpd[6053]: Bluetooth SDP daemon
Apr 14 22:34:43 josephus anacron[6073]: Anacron 2.3 started on 2007-04-14
Apr 14 22:34:43 josephus anacron[6073]: Normal exit (0 jobs run)
Apr 14 22:34:43 josephus /usr/sbin/cron[6099]: (CRON) INFO (pidfile fd = 3)
Apr 14 22:34:43 josephus /usr/sbin/cron[6100]: (CRON) STARTUP (fork ok)
Apr 14 22:34:33 josephus hpiod: 1.6.9 accepting connections at 2208...
Apr 14 22:34:34 josephus kernel: [42950886.490000] apm: BIOS version 1.2 Flags $
Apr 14 22:34:34 josephus kernel: [42950886.490000] apm: disabled on user reques$
Apr 14 22:34:43 josephus hcid[6050]: Bluetooth HCI daemon
Apr 14 22:34:43 josephus hcid[6050]: Register path:/org/bluez fallback:1
Apr 14 22:34:43 josephus sdpd[6053]: Bluetooth SDP daemon
Apr 14 22:34:43 josephus anacron[6073]: Anacron 2.3 started on 2007-04-14
Apr 14 22:34:43 josephus anacron[6073]: Normal exit (0 jobs run)
Apr 14 22:34:43 josephus /usr/sbin/cron[6099]: (CRON) INFO (pidfile fd = 3)
Apr 14 22:34:43 josephus /usr/sbin/cron[6100]: (CRON) STARTUP (fork ok)
Apr 14 22:34:43 josephus /usr/sbin/cron[6100]: (CRON) INFO (Skipping @reboot jo$
Apr 14 22:34:43 josephus gdm[5743]: Master halting...
Apr 14 22:34:44 josephus init: tty1 process (5455) killed by signal 15
Apr 14 22:34:44 josephus init: tty2 process (5456) killed by signal 15
Apr 14 22:34:44 josephus init: tty3 process (5457) killed by signal 15
Apr 14 22:34:44 josephus init: tty4 process (5458) killed by signal 15
Apr 14 22:34:44 josephus init: tty5 process (5459) killed by signal 15
Apr 14 22:34:44 josephus init: tty6 process (5460) killed by signal 15
Apr 14 22:34:44 josephus init: rc2 process (5461) killed by signal 15
Apr 14 22:34:43 josephus /usr/sbin/cron[6100]: (CRON) STARTUP (fork ok)
Apr 14 22:34:43 josephus /usr/sbin/cron[6100]: (CRON) INFO (Skipping @reboot jo$
Apr 14 22:34:43 josephus gdm[5743]: Master halting...
Apr 14 22:34:44 josephus init: tty1 process (5455) killed by signal 15
Apr 14 22:34:44 josephus init: tty2 process (5456) killed by signal 15
Apr 14 22:34:44 josephus init: tty3 process (5457) killed by signal 15
Apr 14 22:34:44 josephus init: tty4 process (5458) killed by signal 15
Apr 14 22:34:44 josephus init: tty5 process (5459) killed by signal 15
Apr 14 22:34:44 josephus init: tty6 process (5460) killed by signal 15
Apr 14 22:34:44 josephus init: rc2 process (5461) killed by signal 15
Apr 14 22:34:51 josephus hcid[6050]: Got disconnected from the system message b$
Apr 14 22:34:54 josephus exiting on signal 15
```

---

### Post by kc5hwb on 2007-04-16
anyone have any ideas on this?

---

