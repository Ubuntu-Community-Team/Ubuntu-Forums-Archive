---
title: "reboot at 8 am"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by dve on 2007-06-18
Hi,

I am using ubuntu feisty as a server and found an odd behaviour. The system reboots itself apparently every morning between 7 and 8 am. Needless to say, for server this is not a good thing.

How do I turn this off? Why is it doing so? How do I debug this further? I mean I found the reboot messages at /var/log/messages (below) but no reason for the reboot. The preceeding and trailing lines seem to have no connection to the reboot. 

Juha

```
cat /var/log/messages |grep restart

Jun 16 08:01:19 michelle syslogd 1.4.1#20ubuntu4: restart.
Jun 17 07:59:35 michelle syslogd 1.4.1#20ubuntu4: restart.
Jun 18 07:38:45 michelle syslogd 1.4.1#20ubuntu4: restart.
```

---

### Post by energiya on 2007-06-18
Look if any of the cronjobs can do this or if any of them get executed in that time period. Also see what services/daemons are running on you PC, but I doubt you will find any strange thing because linux doesn't install anything by itself. Are you running a GUI or just CLI? When did you first noticed this behaviour? Did you install anything prior to this, or configured something?

---

### Post by schorsch on 2007-06-18
I guess there is only the syslog restarted after rotating the syslog-logfiles in /var/log and not the whole server rebooted.  What is the output of the "uptime" command? If the system is up for more than a day you have the proof.

---

### Post by dve on 2007-06-18
Hmm, thanks. Fixed one problem... and probably the second one too. The uptime is larger than one day, so its only syslogd that is restarting :oops:. So the computer is up more than 24h but the software is not. I also found on the net that I am not using a very stable software... So by changing the program should fix this problem entirely.

Juha

---

### Post by schorsch on 2007-06-18
If you think that restarting the syslog every day is a problem you are wrong! It is an normal and desired behaviour on nearly every Linux/Unix System.
There is a logrotate daemon running on your server to delete old log files that are not needed any longer to preserve disk space. As it can cause problems if you delete or move  files that are in use by a process/program (they get a file lock) this process/programm is stopped for a short moment, the files are rotated and the process ist started again. Pretty normal and not a bug!

```
ls -l /var/log/messages
```

will show you this behaviour. The logfile from yesterday will be renamed to messages.0, the log file from the day before yesterday (that was yesterday messages.0 !!) will be renamed and zipped to messages.1.gz and so on .... until the last logfile after 7 days (this is the default) will be deleted. So dont worry, it just works as designed! ... or am I getting you completely wrong ?

---

