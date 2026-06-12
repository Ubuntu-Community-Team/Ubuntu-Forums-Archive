---
title: "read-only filesystem on remote box"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by iBix on 2007-04-01
hi! 

Last night my ubuntu webserver had changed it's filesystem to read-only. I know that the most obvious reason for this is that there is some error in the filesystem itself or that the HD is malfunctioning. 

Is there any safe way of checking the system with fsck on a remote box. I am currently on another continent and cannot access the machine in otherways than ssh.

---

### Post by chalex on 2007-04-01
What do the logs say?  There should be something useful in /var/log/messages or /var/log/syslog.

---

### Post by iBix on 2007-04-01
i've already checked the logs and they did not really help. 

last entry in /var/log/messages is 

Apr^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@ ...

and the last entry in syslog is

Apr  1 06:39:01 kyra /USR/^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@  ...

all activity untill about Apr 1 06.30 seems normal. 

Hmm.. could someone suggest reasons for the filesystem changing into read-only ?

---

### Post by iBix on 2007-04-01
after looking through my logfiles again I found following events: 

Apache2/error.log: 
[Sun Apr 01 07:35:09 2007] [notice] caught SIGTERM, shutting down

daemon.log
Mar 29 16:12:43 kyra dhclient: DHCPACK from 184.221.8^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^

faillog:
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@...

kern.log: 
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@...

anyway there seems to be nothing else but long lines of "^@^@^@^@^@^@^@^@^@^@^@^@^@..." after Sun Apr 01 07:35:09 2007, many of the logs have been recycled at that time so I guess last thing that happened on writable system was a cronjob ? 
 
:confused:

---

### Post by iBix on 2007-04-02
so... 

i have this in my /etc/fstab

# /dev/hdb1
UUID=c195daef-eca6-40c8-afb3-8e5c2cbac27a /               ext3    defaults,errors=remount-ro 0       1

I assume that since the last entry i.e. the <pass> is marked "1" for my hd in fstab, the system would execute fsck on reboot on that disk. Am I right on this? 

Does anyone know how I could be sure that the fsck would run as "fsck -fy" so that i wuld not need to be present physically as the box goes through the fs check?

---

### Post by iBix on 2007-04-02
ok after getting some advice from couple of friends in IRC I tried fsck. this reported some minor errors on first-time and after repeating i got a "clean" result. 

I rebooted with: 

sudo shutdown now -rF and the server came up again quite fast with rw-filesystem... 

after five minutes though the filesystem reverted back to read-only... 

The fact that i had opened phpmyadmin just before the fs turned to read-only gave me some glue to what was going on. I checked the syslog and found out that there was a long list of mysql database errors on a drupal database. It seems that i have my self to blame on this issue... after all i had not configured drupal with cron. 

So no it seems that at least i can get the system to mount as read-write after reboot, this is a good start for me. I'll monitor the system without drupal for a while now and see if the problem disappears after i have setup drupal's conf.php to run with cron.

---

### Post by iBix on 2007-04-11
oh no, it seems that i did not solve my problem after all... 

i made a cron job for drupal a week ago, but today i was updating the system and in the middle of apt-get distupgrde the system changed to a read only fs... 

so it seems that my problem might not be in the drupal installation after all... 

any suggestions on what else migh be causing this annoyance?

---

