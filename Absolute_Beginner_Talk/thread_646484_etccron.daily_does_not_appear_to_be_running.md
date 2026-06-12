---
title: "/etc/cron.daily does not appear to be running"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by pi3832 on 2007-12-21
I'm running v. 6.06-LTS on an IMac 350.

AFAICT, cron.daily is not running automatically.  I can run it manually using [FONT="Fixedsys"]run-parts -v /etc/cron.daily[/FONT], and it doesn't report any errors.  But my logs don't appear to be rotated, nor are critical system files being updated.

Some directory listings to show the lack of updates:

```
$ls -l /var/backups
total 4284
-rw-r--r-- 1 root root   1709202 2007-06-29 12:22 aptitude.pkgstates.0
-rw-r--r-- 1 root root    976168 2007-11-30 12:03 dpkg.status.0
-rw-r--r-- 1 root root    273938 2007-04-02 08:36 dpkg.status.1.gz
-rw-r--r-- 1 root root    274045 2007-04-02 08:34 dpkg.status.2.gz
-rw-r--r-- 1 root root    273919 2007-03-29 00:05 dpkg.status.3.gz
-rw-r--r-- 1 root root    272686 2007-03-25 14:09 dpkg.status.4.gz
-rw-r--r-- 1 root root    267988 2007-03-24 13:14 dpkg.status.5.gz
-rw-r--r-- 1 root root    267059 2007-03-24 11:58 dpkg.status.6.gz
-rw------- 1 root root       810 2007-04-09 09:01 group.bak
-rw------- 1 root shadow     686 2007-04-09 09:01 gshadow.bak
-rw-r--r-- 1 root root      4457 2007-11-30 11:54 infodir.bak
-rw------- 1 root root      1358 2007-04-09 09:24 passwd.bak
-rw------- 1 root shadow     869 2007-04-09 09:24 shadow.bak
```

```
$ls -l /var/log
total 5972
drwxr-xr-x 2 root root    4096 2007-12-20 15:12 apache2
-rw-r--r-- 1 root root       0 2007-10-04 13:32 aptitude
-rw-r--r-- 1 root root     289 2007-06-29 12:22 aptitude.1.gz
-rw-r----- 1 root adm   537684 2007-12-21 09:00 auth.log
-rw-r----- 1 root adm  1326572 2007-10-04 15:00 auth.log.0
-rw-r----- 1 root adm     2486 2007-03-29 07:30 auth.log.1.gz
-rw-r----- 1 root adm      123 2007-03-24 12:04 auth.log.2.gz
-rw-r--r-- 1 root root   36042 2006-08-05 18:20 bootstrap.log
-rw-rw-r-- 1 root utmp       0 2007-12-12 14:59 btmp
-rw-rw-r-- 1 root utmp       0 2007-10-04 13:32 btmp.1
drwxr-xr-x 2 root root    4096 2007-12-20 15:12 cups
-rw-r----- 1 root adm   113491 2007-12-21 08:48 daemon.log
-rw-r----- 1 root adm  1224428 2007-12-12 14:48 daemon.log.0
-rw-r----- 1 root adm   160698 2007-10-04 14:59 daemon.log.1.gz
-rw-r----- 1 root adm     9307 2007-03-29 07:33 daemon.log.2.gz
-rw-r----- 1 root adm      604 2007-03-24 12:12 daemon.log.3.gz
-rw-r----- 1 root adm    70326 2007-12-12 15:56 debug
-rw-r----- 1 root adm      614 2007-03-24 12:03 debug.1.gz
-rw-r--r-- 1 root root   11240 2007-12-12 15:56 dmesg
-rw-r----- 1 root adm        0 2007-12-12 14:59 dpkg.log
-rw-r----- 1 root adm    32409 2007-11-30 12:03 dpkg.log.1
-rw-r----- 1 root adm     9908 2007-09-19 09:42 dpkg.log.2.gz
-rw-r----- 1 root adm    53017 2007-03-25 14:09 dpkg.log.3.gz
-rw-r--r-- 1 root root   15847 2007-11-30 12:06 evms-engine.1.log
-rw-r--r-- 1 root root   15847 2007-11-30 11:39 evms-engine.2.log
-rw-r--r-- 1 root root   15847 2007-10-04 13:41 evms-engine.3.log
-rw-r--r-- 1 root root   15847 2007-10-04 10:35 evms-engine.4.log
-rw-r--r-- 1 root root   15847 2007-09-19 09:04 evms-engine.5.log
-rw-r--r-- 1 root root   15847 2007-08-13 06:52 evms-engine.6.log
-rw-r--r-- 1 root root   15847 2007-06-29 12:27 evms-engine.7.log
-rw-r--r-- 1 root root   15847 2007-06-29 11:24 evms-engine.8.log
-rw-r--r-- 1 root root   15847 2007-06-29 11:08 evms-engine.9.log
-rw-r--r-- 1 root root   15847 2007-12-12 15:56 evms-engine.log
-rw-r--r-- 1 root root   24024 2007-11-30 11:42 faillog
-rw-r--r-- 1 root root    2556 2006-08-05 18:37 fontconfig.log
drwxr-xr-x 2 root root    4096 2007-11-30 11:42 gdm
drwxr-xr-x 2 root root    4096 2007-03-24 11:58 installer
-rw-r----- 1 root adm   357349 2007-12-21 09:00 kern.log
-rw-r----- 1 root adm     4676 2007-03-24 12:03 kern.log.1.gz
-rw-rw-r-- 1 root utmp  292292 2007-12-21 08:33 lastlog
-rw-r--r-- 1 root root       0 2007-03-24 12:03 lpr.log
-rw-r--r-- 1 root root       0 2007-03-24 12:03 mail.err
-rw-r--r-- 1 root root       0 2007-03-24 12:03 mail.info
-rw-r--r-- 1 root root       0 2007-03-24 12:03 mail.log
-rw-r--r-- 1 root root       0 2007-03-24 12:03 mail.warn
-rw-r----- 1 root adm    41167 2007-12-21 09:00 messages
-rw-r----- 1 root adm  1142027 2007-12-12 14:59 messages.0
-rw-r----- 1 root adm    13000 2007-03-29 07:40 messages.1.gz
-rw-r----- 1 root adm     4475 2007-03-24 12:13 messages.2.gz
drwxr-sr-x 2 news news    4096 2007-03-24 12:03 news
drwxr-xr-x 2 ntp  ntp     4096 2007-12-12 14:59 ntpstats
-rw-r--r-- 1 root root       0 2007-12-20 15:12 scrollkeeper.log
-rw-r--r-- 1 root root       0 2007-12-12 14:59 scrollkeeper.log.1
-rw-r--r-- 1 root root    3382 2007-11-30 11:58 scrollkeeper.log.2
-rw-r----- 1 root adm     7731 2007-12-21 09:00 syslog
-rw-r----- 1 root adm     6954 2007-12-20 23:14 syslog.0
-rw-r----- 1 root adm    16120 2007-12-20 15:12 syslog.1.gz
-rw-r----- 1 root adm      180 2007-12-12 15:53 syslog.2.gz
-rw-r----- 1 root adm      282 2007-12-12 15:48 syslog.3.gz
-rw-r----- 1 root adm      377 2007-12-12 15:33 syslog.4.gz
-rw-r----- 1 root adm      176 2007-12-12 15:00 syslog.5.gz
-rw-r----- 1 root adm      179 2007-12-12 15:00 syslog.6.gz
-rw-r--r-- 1 root root  226409 2007-12-12 21:56 udev
drwxr-xr-x 2 root root    4096 2006-05-29 06:46 unattended-upgrades
-rw-r----- 1 root adm   152507 2007-12-12 15:57 user.log
-rw-r----- 1 root adm    23754 2007-03-29 00:21 user.log.0
-rw-r----- 1 root adm      314 2007-03-24 12:05 user.log.1.gz
-rw-r--r-- 1 root root       0 2007-03-24 12:03 uucp.log
-rw-rw-r-- 1 root utmp   16896 2007-12-21 08:33 wtmp
-rw-rw-r-- 1 root utmp   44160 2007-12-12 14:48 wtmp.1
-rw-r--r-- 1 root root     308 2006-08-05 18:28 wvdialconf.log
-rw-r--r-- 1 root root   36046 2007-11-30 11:42 Xorg.0.log
-rw-r--r-- 1 root root   36046 2007-09-19 09:05 Xorg.0.log.old

```

My cron.daily folder contains:
```
$ls -l /etc/cron.daily
total 56
-rwxr-xr-x 1 root root  311 2005-05-02 21:08 0anacron
-rwxr-xr-x 1 root root 5566 2006-04-18 14:47 apt
-rwxr-xr-x 1 root root  314 2006-04-03 09:46 aptitude
-rwxr-xr-x 1 root root  275 2007-10-04 15:46 fs_backup
-rwxr-xr-x 1 root root  117 2007-12-21 08:43 logrotate
-rwxr-xr-x 1 root root  946 2005-09-26 10:12 man-db
-rwxr-xr-x 1 root root 1118 2006-05-28 21:49 ntp-server
-rwxr-xr-x 1 root root  189 2006-01-07 10:43 slocate
-rwxr-xr-x 1 root root 3227 2005-11-15 07:46 standard
-rwxr-xr-x 1 root root 1307 2006-04-24 13:36 sysklogd
-rwxr-xr-x 1 root root   85 2007-12-12 15:48 z_sbackup_mjf
```

My crontab is:
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

# I'm removing "test -x /usr/sbon/anacron || " from the command lines.
# I'm not sure it's doing anything useful.  MJF

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts -v /etc/cron.hourly
14 23   * * *   root    run-parts -v /etc/cron.daily
14 22   * * 7   root    run-parts -v /etc/cron.weekly
14 21   13 * *  root    run-parts -v /etc/cron.monthly

```

I've checked, and cron is running:
```
$ ps aux | grep cron
root      3730  0.0  0.2   2876   876 ?        Ss   Dec12   0:00 /usr/sbin/cron
pi3832    9636  0.0  0.2   2892   684 pts/0    R+   09:36   0:00 grep cron
```

I'm mighty clueless here.  The scripts seem well-formed, and if I run them manually with [FONT="Fixedsys"]run-parts[/FONT] they all appear to run without error, and *some* actually do what I expect them to.

But almost none of the scripts seem to be doing what I expect them to do, automatically on a daily basis.

Any ideas?

---

### Post by dwblas on 2007-12-21
See what is in /etc/cron.daily.  Those are the scripts that are run daily-if there are any.  On my XUbuntu system, the file /var/spool/anacron/cron.daily contains the last date for the daily cron run.  I don't know if Ubuntu uses Vixie Cron or not so your locations may be different.  man crontab (5) has all of the options if you want to put some daily stuff in the user's crontab.

---

### Post by pi3832 on 2007-12-21
> **dwblas said:**
> See what is in /etc/cron.daily.

The third box in my original posts shows the /etc/cron.daily contents.

---

### Post by dwblas on 2007-12-22
What's in /var/spool/anacron/cron.daily? Does it show that daily was run yesterday or today?  Also, there may be a problem with the crontab file.  On my machine, including "root" is not a good idea as it will not run properly-see man crontab (5) and/or Google.  It's gets the permissions from the user so if you want to run something as root you will have to use
sudo crontab -e 
and see what is in the file.  There Is A 99% Chance That Cron Is Not The Problem, so get off of that and start checking for other things.

---

### Post by andrew.46 on 2008-01-29
Hi,

 Saw you having some frustration with cron:

> **pi3832 said:**
> 

```
# m h dom mon dow user  command
17 *    * * *   root    run-parts -v /etc/cron.hourly
14 23   * * *   root    run-parts -v /etc/cron.daily
14 22   * * 7   root    run-parts -v /etc/cron.weekly
14 21   13 * *  root    run-parts -v /etc/cron.monthly

```

Any ideas?

Please forgive me if this seems too obvious to be considered but is your computer running at 9.14 pm, 10.14 pm and 11.14 pm?

     Andrew

---

