---
title: "ClamAV update fails"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Robbyx on 2007-08-16
I have installed the daemon for clamav. 

I think there have been no virus sigs updates and so I ran the following:

> robin@robin-desktop:~$ sudo freshclam
Password:
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
robin@robin-desktop:~$ 


I do not know how to clear the problem with the logger. Any help appreciated.

Robin

---

### Post by bodhi.zazen on 2007-08-16
Well, lest look at the log :

```
gksu gedit /var/log/clamav/freshclam.log
```

---

### Post by Robbyx on 2007-08-16
Following your code it seems to me that it is updated. There are a lot of entries for today, I have not bothered you with the earlier days:

[PHP]Received signal: wake up
ClamAV update process started at Thu Aug 16 00:03:48 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3964, sigs: 14108, f-level: 20, builder: arnaud)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 01:03:48 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3964, sigs: 14108, f-level: 20, builder: arnaud)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 02:03:48 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
Downloading daily-3965.cdiff [100%]
Downloading daily-3966.cdiff [100%]
daily.inc updated (version: 3966, sigs: 14111, f-level: 20, builder: sven)
Database updated (147274 signatures) from db.local.clamav.net (IP: 206.154.202.13)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 03:03:48 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 04:03:48 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 05:03:48 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 06:03:48 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 07:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 08:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 09:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 10:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 11:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 12:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 13:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 14:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 15:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 16:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3966, sigs: 14111, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 17:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
Downloading daily-3967.cdiff [100%]
daily.inc updated (version: 3967, sigs: 14072, f-level: 20, builder: sven)
Database updated (147235 signatures) from db.local.clamav.net (IP: 129.64.99.170)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 18:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3967, sigs: 14072, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 19:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3967, sigs: 14072, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 20:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3967, sigs: 14072, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 21:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3967, sigs: 14072, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 22:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3967, sigs: 14072, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Thu Aug 16 23:03:49 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3967, sigs: 14072, f-level: 20, builder: sven)
--------------------------------------[/PHP]

---

### Post by bodhi.zazen on 2007-08-16
Not sure. I guess I was hoping to see an error message of some kind.

You can look through this thread to see if you can sort it out further :

[https://answers.launchpad.net/ubuntu/+question/10799](https://answers.launchpad.net/ubuntu/+question/10799)

---

### Post by euler_fan on 2007-08-17
please post 

```
gedit /usr/local/etc/freshclam.conf
```

---

### Post by Robbyx on 2007-08-18
> **euler_fan said:**
> please post 

```
gedit /usr/local/etc/freshclam.conf
```

It is empty.

---

### Post by Robbyx on 2007-08-18
> **euler_fan said:**
> please post 

```
gedit /usr/local/etc/freshclam.conf
```


On my system the freshclam.conf is in /etc/clamav:

# Automatically created by the clamav-freshclam postinst
# Comments will get lost when you reconfigure the clamav-freshclam package

DatabaseOwner clamav
UpdateLogFile /var/log/clamav/freshclam.log
LogVerbose false
LogSyslog false
LogFacility LOG_LOCAL6
LogFileMaxSize 0
Foreground false
Debug false
MaxAttempts 5
DatabaseDirectory /var/lib/clamav/
DNSDatabaseInfo current.cvd.clamav.net
AllowSupplementaryGroups false
PidFile /var/run/clamav/freshclam.pid
ConnectTimeout 30
ReceiveTimeout 30
ScriptedUpdates yes
# Check for new database 24 times a day
Checks 24
DatabaseMirror db.local.clamav.net
DatabaseMirror database.clamav.net

---

### Post by euler_fan on 2007-08-18
Okay . . . you must have installed the package whereas I always install it from source.

Post the results from

```
ls /var/log
```

and 

```
ls /var/log/clamav
```

if that doesn't work, run them again as sudo.

---

### Post by Robbyx on 2007-08-18
> **euler_fan said:**
> Okay . . . you must have installed the package whereas I always install it from source.

Post the results from

```
ls /var/log
```.

```
robin@robin-desktop:~$ ls /var/log
acpid            daemon.log.0        fontconfig.log        pycentral.log
acpid.1.gz       daemon.log.1.gz     fsck                  rkhunter.log
acpid.2.gz       daemon.log.2.gz     gdm                   samba
acpid.3.gz       daemon.log.3.gz     installer             scrollkeeper.log
acpid.4.gz       daemon.log.4.gz     kern.log              scrollkeeper.log.1
apcupsd.events   daemon.log.5.gz     kern.log.0            scrollkeeper.log.2
apport.log       daemon.log.6.gz     kern.log.1.gz         syslog
apport.log.1     debug               kern.log.2.gz         syslog.0
apport.log.2.gz  debug.0             kern.log.3.gz         syslog.1.gz
apport.log.3.gz  debug.1.gz          kern.log.4.gz         syslog.2.gz
apport.log.4.gz  debug.2.gz          kern.log.5.gz         syslog.3.gz
apport.log.5.gz  debug.3.gz          kern.log.6.gz         syslog.4.gz
apport.log.6.gz  debug.4.gz          lastlog               syslog.5.gz
apport.log.7.gz  debug.5.gz          lpr.log               syslog.6.gz
aptitude         debug.6.gz          mail.err              tor
aptitude.1.gz    dist-upgrade        mail.info             udev
aptitude.2.gz    dmesg               mail.log              unattended-upgrades
aptitude.3.gz    dmesg.0             mail.warn             user.log
auth.log         dmesg.1.gz          messages              user.log.0
auth.log.0       dmesg.2.gz          messages.0            user.log.1.gz
auth.log.1.gz    dmesg.3.gz          messages.1.gz         user.log.2.gz
auth.log.2.gz    dmesg.4.gz          messages.2.gz         user.log.3.gz
auth.log.3.gz    dpkg.log            messages.3.gz         uucp.log
bittorrent       dpkg.log.1          messages.4.gz         wtmp
boot             dpkg.log.2.gz       messages.5.gz         wtmp.1
bootstrap.log    dpkg.log.3.gz       messages.6.gz         wvdialconf.log
btmp             dpkg.log.4.gz       mgetty                Xorg.0.log
btmp.1           efax                news                  Xorg.0.log.old
clamav           envy-installer.log  nvidia-installer.log  Xorg.1.log
cups             exim4               prelink.log           Xorg.20.log
daemon.log       faillog             privoxy

```


and 

```
ls /var/log/clamav
```

```
robin@robin-desktop:~$ ls /var/log/clamav
clamav.log       clamav.log.4.gz  freshclam.log       freshclam.log.4.gz
clamav.log.1     clamav.log.5.gz  freshclam.log.1     freshclam.log.5.gz
clamav.log.2.gz  clamav.log.6.gz  freshclam.log.2.gz  freshclam.log.6.gz
clamav.log.3.gz  clamav.log.7.gz  freshclam.log.3.gz  freshclam.log.7.gz

```

---

### Post by euler_fan on 2007-08-18
Let's take a look at what's in /var/log/clamav/freshclam.log.

Post ```
gedit /var/log/clamav/freshclam.log
```

Use sudo if you have to.

So you're not wondering why you're posting all your log files, I'm trying to eliminate some possibilities before we start messing with your config file--which we might end up doing sooner or later.

The contents of you /var/log/clamav folder seem to be indicating that logging IS ocouring. This is what I hope is the case. ClamAV logging I have found to be a little tricky to get to work right personally.

---

### Post by Robbyx on 2007-08-18
> **euler_fan said:**
> Let's take a look at what's in /var/log/clamav/freshclam.log.

Post ```
gedit /var/log/clamav/freshclam.log
```



Here are just today's part of the log:

```
Received signal: wake up
ClamAV update process started at Sat Aug 18 01:03:55 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
Downloading daily-3976.cdiff [100%]
daily.inc updated (version: 3976, sigs: 14194, f-level: 20, builder: sven)
Database updated (147357 signatures) from db.local.clamav.net (IP: 205.139.192.13)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 02:03:56 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
Downloading daily-3977.cdiff [100%]
daily.inc updated (version: 3977, sigs: 14186, f-level: 20, builder: sven)
Database updated (147349 signatures) from db.local.clamav.net (IP: 64.142.100.50)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 03:03:57 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3977, sigs: 14186, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 04:03:57 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3977, sigs: 14186, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 05:03:57 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3977, sigs: 14186, f-level: 20, builder: sven)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 06:03:57 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
Downloading daily-3978.cdiff [100%]
daily.inc updated (version: 3978, sigs: 14506, f-level: 20, builder: ccordes)
Database updated (147669 signatures) from db.local.clamav.net (IP: 64.246.44.108)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 07:03:58 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
Downloading daily-3979.cdiff [100%]
daily.inc updated (version: 3979, sigs: 14507, f-level: 20, builder: ccordes)
Database updated (147670 signatures) from db.local.clamav.net (IP: 72.21.63.182)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 08:03:58 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
Downloading daily-3980.cdiff [100%]
Downloading daily-3981.cdiff [100%]
daily.inc updated (version: 3981, sigs: 14515, f-level: 20, builder: ccordes)
Database updated (147678 signatures) from db.local.clamav.net (IP: 206.154.203.13)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 09:03:58 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
Downloading daily-3982.cdiff [100%]
daily.inc updated (version: 3982, sigs: 14522, f-level: 20, builder: ccordes)
Database updated (147685 signatures) from db.local.clamav.net (IP: 205.139.192.13)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 10:03:59 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3982, sigs: 14522, f-level: 20, builder: ccordes)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 11:03:59 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3982, sigs: 14522, f-level: 20, builder: ccordes)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 12:03:59 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3982, sigs: 14522, f-level: 20, builder: ccordes)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 13:03:59 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3982, sigs: 14522, f-level: 20, builder: ccordes)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 14:03:59 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3982, sigs: 14522, f-level: 20, builder: ccordes)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 15:03:59 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
Downloading daily-3983.cdiff [100%]
daily.inc updated (version: 3983, sigs: 14523, f-level: 20, builder: arnaud)
Database updated (147686 signatures) from db.local.clamav.net (IP: 65.120.238.2)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 16:03:59 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3983, sigs: 14523, f-level: 20, builder: arnaud)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 17:03:59 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3983, sigs: 14523, f-level: 20, builder: arnaud)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 18:03:59 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3983, sigs: 14523, f-level: 20, builder: arnaud)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 19:04:00 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3983, sigs: 14523, f-level: 20, builder: arnaud)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 20:04:00 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3983, sigs: 14523, f-level: 20, builder: arnaud)
--------------------------------------
Received signal: wake up
ClamAV update process started at Sat Aug 18 21:04:00 2007
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.inc is up to date (version: 3983, sigs: 14523, f-level: 20, builder: arnaud)
--------------------------------------
```

Thank you very much for your help so far.

---

### Post by euler_fan on 2007-08-18
> **Robbyx said:**
> On my system the freshclam.conf is in /etc/clamav:

# Automatically created by the clamav-freshclam postinst
# Comments will get lost when you reconfigure the clamav-freshclam package

DatabaseOwner clamav
UpdateLogFile /var/log/clamav/freshclam.log
LogVerbose false
LogSyslog false
LogFacility LOG_LOCAL6
LogFileMaxSize 0
Foreground false
Debug false
MaxAttempts 5
DatabaseDirectory /var/lib/clamav/
DNSDatabaseInfo current.cvd.clamav.net
AllowSupplementaryGroups false
PidFile /var/run/clamav/freshclam.pid
ConnectTimeout 30
ReceiveTimeout 30
ScriptedUpdates yes
# Check for new database 24 times a day
Checks 24
DatabaseMirror db.local.clamav.net
DatabaseMirror database.clamav.net

Okay . . . you're logging. This is good. But for some reason it doesn't like the internal logger.

So let's try one little thing:

Run and post all results from:

```
sudo freshclam -v
```

Then in the config file change

```
LogSyslog false
```
to
```
LogSyslog true
```

You've have to open it with sudo gedit.

Then run:

```
sudo freshclam -v
```

and post the output.

---

### Post by Robbyx on 2007-08-18
> **euler_fan said:**
> Okay . . . you're logging. This is good. But for some reason it doesn't like the internal logger.

So let's try one little thing:

Run and post all results from:

```
sudo freshclam -v
```

robin@robin-desktop:~$ sudo freshclam -v
Password:
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
robin@robin-desktop:~$ 


Then in the config file change

Could you please give me the code for opening the config file ie where is it?

```
LogSyslog false
```
to
```
LogSyslog true
```

You've have to open it with sudo gedit.

Done

Then run:

```
sudo freshclam -v
```

robin@robin-desktop:~$ gksudo gedit /etc/clamav/freshclam.conf
robin@robin-desktop:~$ sudo freshclam -v
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).




and post the output.

see above

---

### Post by euler_fan on 2007-08-18
I'll be honest . . . I've run out of good ideas. Go ahead and change the logging option back that I had you change since it was logging anyway.

Since the cronjob for updating your virus signatures is working, I'm going to say don't worry about it and just make sure you periodically read through your freshclam.log file to ensure it is still updating.

My final suggestion would be to specify a different log file when running freshclam manually using the --log=/path/to/log.log option along with the -v option. It could be something with the way the log files are being put together. If you still get the error, then don't worry about that either. If it suddenly goes away, then cool.

Sorry I couldn't be of more help.

---

### Post by Robbyx on 2007-08-19
> **euler_fan said:**
> .

Thank you for your comments and guidance. It is good enough for me to know that the updates are taking place and being used.

I have a question about actually using ClamAV. I would like to scan by computer for viruses. I do not think I am getting it to happen. I choose scan a directory and then my documents. It only seems to check one item.

---

### Post by euler_fan on 2007-08-19
> **Robbyx said:**
> Thank you for your comments and guidance. It is good enough for me to know that the updates are taking place and being used.

I have a question about actually using ClamAV. I would like to scan by computer for viruses. I do not think I am getting it to happen. I choose scan a directory and then my documents. It only seems to check one item.

I like the following command:

```
clamscan -i -r /
```

which will scan your entire root directory recursively and only show infected files.

If you want to just scan say one folder, then replace the"/" with the full path to the folder.

For other options, just type

```
clamscan -h
```

or ```
man clamscan
```

---

