---
title: "Sound Juicer + Ripping Media = CRASH!!"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Sou Portugues on 2007-02-08
So-
I've downloaded the repositories for restricted formats, and got all that up and running, but now when I try to rip cds, my whole sytem crashes.  Funny thing is, it isn't format specific (tried oog and mp3), or cd specific (tried an old and new cd), and it does it 'bout halfway throught the cd (I have the first half of the cd ripped, then it crashes).

I'm fairly new to linux/ubuntu, so I'm not exactly sure where to start looking, but when I searched for some things (like "sound juicer" and "crashed") I didn't get too far.

If it comes down to using a different program, I'm ok with that, but this is the only one I've got loaded right now that even lets me begin to rip files.

---

### Post by dbbolton on 2007-02-08
whenever i encounter a weird error that no one else seems to know about, i file a bug report.

---

### Post by Sou Portugues on 2007-02-08
> **dbbolton said:**
> whenever i encounter a weird error that no one else seems to know about, i file a bug report.

Ok
1. What do I file, I have no idea why it's crashing?
2. Um.... how, ah, I mean... Yeah, I have no idea how to file a bug report.:oops:

---

### Post by Sou Portugues on 2007-02-14
Ok-
Here's an update.....
I got tired of sound juicer, so I switched to Grip (more options anyway, who doesn't like options, eh?).  Guess what, [SIZE="4"][FONT="Impact"]**BAM!**[/FONT][/SIZE] Same problem.  Ripping process gets 'bout halfway through and the whole computer crashes.

I don't know what to do here.  I sthere a log that I can check that might tell me whats going on?

---

### Post by Sou Portugues on 2007-02-15
I also noticed that most of the other media players I'm using won't play the files they are supposed to be able to (most video players wnt play DVDs, only totem).  Could I be missing a file somewhere?  
I feel like I'm being terribly needy, for which I'm sorry, but I could really use a shove in the right direction here.

Thanks to anyone who replies (in advance), even if only with recipies for cookies...

---

### Post by houstonbofh on 2007-02-15
Go into /var/log and cause a crash.  The "tail syslog" or anything else that seems likely.  Also do a "df -h" and tell us where you are ripping to.

---

### Post by Sou Portugues on 2007-02-15
> **houstonbofh said:**
> Go into /var/log and cause a crash.  The "tail syslog" or anything else that seems likely.  Also do a "df -h" and tell us where you are ripping to.

This is the df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G  3.1G   66G   5% /
varrun                506M   84K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  152K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M  9.3M  497M   2% /lib/modules/2.6.15-28-386/volatile
/dev/sdb1             231G  100G  120G  46% /media/sdb1
/dev/sdc1             153G   99G   54G  65% /media/usbdisk

I'm not sure what you meant by the rest, you want me to crash the system again, or am I just to try and lookup a log file from /var/log?

This is the ls -l for /var/log:
-rw-r----- 1 root   adm      1298 2007-02-14 23:42 acpid
-rw-r----- 1 root   adm     20952 2007-02-15 00:17 auth.log
-rw-r----- 1 root   adm       216 2007-02-13 22:48 auth.log.0
-rw-r--r-- 1 root   root    35210 2006-08-05 18:20 bootstrap.log
-rw-rw-r-- 1 root   utmp        0 2006-08-05 18:19 btmp
drwxr-xr-x 2 clamav clamav   4096 2006-09-13 00:57 clamav
drwxr-xr-x 2 root   root     4096 2007-02-14 01:03 cups
-rw-r----- 1 root   adm    198965 2007-02-15 00:38 daemon.log
-rw-r----- 1 root   adm      2348 2007-02-13 22:55 daemon.log.0
-rw-r----- 1 root   adm     28088 2007-02-14 23:42 debug
-rw-r----- 1 root   adm      5380 2007-02-13 22:46 debug.0
-rw-r--r-- 1 root   root    27690 2007-02-14 23:42 dmesg
-rw-r----- 1 root   adm    848146 2007-02-14 21:54 dpkg.log
-rw-r--r-- 1 root   root    17076 2007-02-14 21:59 evms-engine.1.log
-rw-r--r-- 1 root   root    17071 2007-02-14 12:00 evms-engine.2.log
-rw-r--r-- 1 root   root    16717 2007-02-14 00:57 evms-engine.3.log
-rw-r--r-- 1 root   root    16717 2007-02-13 23:02 evms-engine.4.log
-rw-r--r-- 1 root   root    16717 2007-02-13 22:46 evms-engine.5.log
-rw-r--r-- 1 root   root    17076 2007-02-14 23:42 evms-engine.log
-rw-r--r-- 1 root   root    24024 2007-02-14 01:06 faillog
-rw-r--r-- 1 root   root     3428 2007-02-14 00:49 fontconfig.log
drwxr-xr-x 2 root   root     4096 2007-02-14 23:42 gdm
drwxr-xr-x 2 root   root     4096 2007-02-13 20:16 installer
-rw-r----- 1 root   adm    283107 2007-02-14 23:56 kern.log
-rw-r----- 1 root   adm     43173 2007-02-13 22:46 kern.log.0
-rw-rw-r-- 1 root   utmp   292292 2007-02-14 23:56 lastlog
-rw-r--r-- 1 root   root        0 2007-02-13 22:46 lpr.log
-rw-r--r-- 1 root   root        0 2007-02-13 22:46 mail.err
-rw-r--r-- 1 root   root        0 2007-02-13 22:46 mail.info
-rw-r--r-- 1 root   root        0 2007-02-13 22:46 mail.log
-rw-r--r-- 1 root   root        0 2007-02-13 22:46 mail.warn
-rw-r----- 1 root   adm    280007 2007-02-15 00:22 messages
-rw-r----- 1 root   adm     39584 2007-02-13 22:56 messages.0
drwxr-sr-x 2 news   news     4096 2007-02-13 22:46 news
-rw-r--r-- 1 root   root    26700 2007-02-14 01:09 nvidia-installer.log
-rw-r--r-- 1 root   root   245954 2007-02-14 21:54 scrollkeeper.log
-rw-r----- 1 root   adm    394980 2007-02-15 00:38 syslog
-rw-r----- 1 root   adm    122433 2007-02-14 01:03 syslog.0
-rw-r----- 1 root   adm      8531 2007-02-13 22:51 syslog.1.gz
-rw-r--r-- 1 root   root   308777 2007-02-14 23:41 udev
drwxr-xr-x 2 root   root     4096 2006-05-29 06:46 unattended-upgrades
-rw-r----- 1 root   adm     27852 2007-02-14 23:56 user.log
-rw-r----- 1 root   adm      2085 2007-02-13 22:56 user.log.0
-rw-r--r-- 1 root   root        0 2007-02-13 22:46 uucp.log
-rw-rw-r-- 1 root   utmp    72960 2007-02-15 00:37 wtmp
-rw-r--r-- 1 root   root      308 2006-08-05 18:25 wvdialconf.log
-rw-r--r-- 1 root   root    27910 2007-02-15 00:35 Xorg.0.log
-rw-r--r-- 1 root   root    28060 2007-02-14 22:01 Xorg.0.log.old

but I've rebooted since the last crash 2 times now...

---

### Post by houstonbofh on 2007-02-16
Go to the /var/log directory in a terminal.

Rip a cd and let it crash.

In the terminal type "tail syslog" which will give you the last few entries.  Also tail anything else that has new entries like "auth.log" or whatever else looks interesting.

---

