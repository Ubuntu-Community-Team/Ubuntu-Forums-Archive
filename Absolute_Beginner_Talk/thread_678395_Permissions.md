---
title: "Permissions"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by spookyct on 2008-01-25
I had to cancel a vmware install in progress...  and from reading other posts on this forum, I found that you could just delete the /etc/vmware folder.


My user for some reason doesn't have permission to delete those files...  so i ran the command, 

```
sudo chown -R james:james /

```

james is my userid....  now whenever i try to sudo anything I get this...

```
james@james-desktop:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl 
sudo: must be setuid root

```

I tried setting the chown -r to "root:root" that didn't help.

---

### Post by UltraMathMan on 2008-01-25
Wow, you changed the ownership permissions to you, throughout the entire filesystem. From what I got from Google, the simplest fix is probably to just reinstall. That said you could alse try fixing them by booting a live cd and changing the ownership on your install to match the ownerships on the files on the CD.  

For future reference to delete that folder you should have used ```
sudo rm -Rf /etc/vmware
``` or to change the ownership on just that folder (and its subfolders/files) ```
sudo chown james:james /etc/vmware
```

What you did: ```
ls /
``` See those folders? You changed the ownership of ALL of them and ALL their contents to you.

---

### Post by spookyct on 2008-01-25
its that bad?

---

### Post by UltraMathMan on 2008-01-25
Yeah, different files and folders on the system have different owners, and groups which define who and what in the system can access them. In running that chown you effectively overwrote all of that. For example ```
ls -l /etc
``` looks like ```
ls -l /etc/
total 1000
-rw-r--r-- 1 root root     2584 2007-04-04 15:26 adduser.conf
-rw-r--r-- 1 root root       50 2008-01-22 10:24 adjtime
-rw-r--r-- 1 root root       54 2007-04-04 15:31 aliases
drwxr-xr-x 2 root root     4096 2008-01-25 15:11 alternatives
drwxr-xr-x 6 root root     4096 2007-04-04 15:29 apm
drwxr-xr-x 4 root root     4096 2007-04-04 15:29 apt
-rw-r----- 1 root daemon    144 2006-07-20 22:16 at.deny
-rw-r--r-- 1 root root     1565 2006-09-19 18:01 bash.bashrc
-rw-r--r-- 1 root root   215918 2006-09-19 18:01 bash_completion
drwxr-xr-x 2 root root     4096 2007-04-04 15:29 bash_completion.d
drwxr-xr-x 2 root root     4096 2007-04-04 15:24 belocs
-rw-r--r-- 1 root root      319 2007-04-04 19:32 blkid.tab
drwxr-xr-x 2 root root     4096 2007-04-04 15:29 calendar
drwxr-s--- 2 root dip      4096 2007-04-04 15:29 chatscripts
-rw-r--r-- 1 root root     3694 2006-08-26 08:48 checkinstallrc
drwxr-xr-x 2 root root     4096 2007-04-04 15:26 console-setup
drwxr-xr-x 2 root root     4096 2007-04-04 15:26 console-tools
drwxr-xr-x 2 root root     4096 2007-04-04 15:29 cron.d
drwxr-xr-x 2 root root     4096 2007-04-13 20:18 cron.daily
drwxr-xr-x 2 root root     4096 2007-04-04 15:29 cron.hourly
drwxr-xr-x 2 root root     4096 2007-04-04 15:29 cron.monthly
-rw-r--r-- 1 root root      651 2006-07-20 22:15 crontab
drwxr-xr-x 2 root root     4096 2007-04-11 19:33 cron.weekly
drwxr-xr-x 3 root lp       4096 2008-01-07 18:55 cups
-rw-r--r-- 1 root root     2673 2006-07-24 11:19 debconf.conf
-rw-r--r-- 1 root root       17 2006-06-30 10:03 debian_version
drwxr-xr-x 2 root root     4096 2007-11-28 20:35 default
drwxr-xr-x 4 root root     4096 2007-04-11 18:05 defoma
-rw-r--r-- 1 root root      600 2006-07-10 11:35 deluser.conf
drwxr-xr-x 4 root root     4096 2007-04-04 15:26 dhcp3
drwxr-xr-x 3 root root     4096 2007-04-04 19:38 dpkg
-rw-r--r-- 1 root root      111 2007-04-04 15:27 environment
drwxr-xr-x 2 root root     4096 2007-11-28 20:34 event.d
-rw-r--r-- 1 root root      354 2006-06-23 10:24 fdmount.conf
drwxr-xr-x 3 root root     4096 2007-04-12 18:58 foomatic
-rw-r--r-- 1 root root      474 2007-04-04 15:21 fstab
-rw-r--r-- 1 root root      511 2007-04-04 15:21 fstab.pre-uuid
drwxr-xr-x 2 root root     4096 2007-04-04 15:29 groff
-rw-r--r-- 1 root root      685 2007-04-04 20:02 group
-rw------- 1 root root      670 2007-04-04 15:31 group-
-rw-r----- 1 root shadow    582 2007-04-04 20:02 gshadow
-rw------- 1 root root      570 2007-04-04 15:31 gshadow-
-rw-r--r-- 1 root root     4728 2006-07-20 20:14 hdparm.conf
-rw-r--r-- 1 root root       26 2006-06-30 10:03 host.conf
-rw-r--r-- 1 root root        6 2007-04-04 15:21 hostname
-rw-r--r-- 1 root root      262 2007-04-04 15:21 hosts
-rw-r--r-- 1 root root      677 2007-04-04 15:26 hosts.allow
-rw-r--r-- 1 root root      901 2007-04-04 15:26 hosts.deny
-rw-r--r-- 1 root root      121 2007-04-04 15:21 iftab
-rw-r--r-- 1 root root     1338 2007-04-13 20:22 inetd.conf
drwxr-xr-x 2 root root     4096 2007-11-28 20:35 init.d
drwxr-xr-x 5 root root     4096 2007-04-04 15:26 initramfs-tools
-rw-r--r-- 1 root root     1698 2006-03-21 07:42 inputrc
drwxr-xr-x 2 root root     4096 2007-04-04 15:26 iproute2
-rw-r--r-- 1 root root       19 2006-10-19 18:49 issue
-rw-r--r-- 1 root root       12 2006-10-19 18:49 issue.net
-rw-r--r-- 1 root root      112 2007-04-04 15:27 kernel-img.conf
drwxr-xr-x 2 root root     4096 2007-04-04 15:26 ldap
-rw-r--r-- 1 root root    12379 2007-11-28 20:34 ld.so.cache
-rw-r--r-- 1 root root       48 2007-04-11 18:05 ld.so.conf
drwxr-xr-x 2 root root     4096 2007-04-04 19:38 ld.so.conf.d
drwxr-xr-x 2 root root     4096 2006-07-10 12:45 libpaper.d
-rw-r--r-- 1 root root      620 2004-12-01 00:04 links.cfg
-rw-r--r-- 1 root root     2586 2003-12-04 02:57 locale.alias
-rw-r--r-- 1 root root     1267 2007-11-28 20:34 localtime
drwxr-xr-x 3 root root     4096 2007-04-04 15:25 logcheck
-rw-r--r-- 1 root root    10684 2006-10-19 18:53 login.defs
-rw-r--r-- 1 root root      599 2006-06-19 12:51 logrotate.conf
drwxr-xr-x 2 root root     4096 2007-04-04 15:29 logrotate.d
drwxr-xr-x 2 root root     4096 2006-09-21 23:26 lsb-base
-rw-r--r-- 1 root root     3770 2006-09-21 13:12 lsb-base-logging.sh
-rw-r--r-- 1 root root       95 2006-10-19 04:15 lsb-release
-rw-r--r-- 1 root root    10814 2006-02-20 16:55 ltrace.conf
-rw-r--r-- 1 root root   139827 2006-07-04 18:32 lynx.cfg
-rw-r--r-- 1 root root      111 2006-07-04 14:14 magic
-rw-r--r-- 1 root root     2534 2008-01-25 15:11 mailcap
-rw-r--r-- 1 root root      449 2006-06-15 16:13 mailcap.order
-rw-r--r-- 1 root root     4696 2005-09-26 11:12 manpath.config
-rw-r--r-- 1 root root    11742 2006-06-23 10:24 mediaprm
-rw-r--r-- 1 root root    20423 2006-06-15 16:13 mime.types
-rw-r--r-- 1 root root      330 2006-06-29 21:18 mke2fs.conf
drwxr-xr-x 3 root root     4096 2007-11-28 20:35 modprobe.d
-rw-r--r-- 1 root root      208 2007-04-04 15:27 modules
lrwxrwxrwx 1 root root       13 2007-04-04 15:24 motd -> /var/run/motd
-rw-r--r-- 1 root root      266 2007-04-04 15:24 motd.tail
-rw-r--r-- 1 root root      450 2008-01-22 10:25 mtab
-rw-r--r-- 1 root root     7620 2006-07-10 09:14 nanorc
drwxr-xr-x 6 root root     4096 2007-08-23 20:13 network
-rw-r--r-- 1 root root      465 2006-02-09 12:35 nsswitch.conf
drwxr-xr-x 2 root root     4096 2007-04-04 15:23 opt
-rw-r--r-- 1 root root      552 2006-06-29 13:57 pam.conf
drwxr-xr-x 2 root root     4096 2007-11-28 20:34 pam.d
-rw-r--r-- 1 root root        7 2007-04-11 18:05 papersize
-rw-r--r-- 1 root root      952 2007-04-04 19:38 passwd
-rw------- 1 root root      902 2007-04-04 15:31 passwd-
drwxr-xr-x 2 root root     4096 2007-04-04 15:26 pcmcia
drwxr-xr-x 4 root root     4096 2007-04-04 15:25 perl
-rw-r--r-- 1 root root      342 2007-04-04 15:29 popularity-contest.conf
drwxr-xr-x 8 root dip      4096 2007-04-04 15:29 ppp
-rw-r--r-- 1 root root     1386 2008-01-23 17:37 printcap
-rw-r--r-- 1 root root      369 2007-04-04 15:24 profile
-rw-r--r-- 1 root root     2478 2006-07-20 21:06 protocols
drwxr-xr-x 2 root root     4096 2007-04-04 15:26 python
drwxr-xr-x 2 root root     4096 2007-04-04 15:24 python2.4
drwxr-xr-x 2 root root     4096 2007-11-28 20:33 rc0.d
drwxr-xr-x 2 root root     4096 2007-04-13 20:19 rc1.d
drwxr-xr-x 2 root root     4096 2007-04-13 20:19 rc2.d
drwxr-xr-x 2 root root     4096 2007-04-13 20:19 rc3.d
drwxr-xr-x 2 root root     4096 2007-04-13 20:19 rc4.d
drwxr-xr-x 2 root root     4096 2007-04-13 20:19 rc5.d
drwxr-xr-x 2 root root     4096 2007-11-28 20:33 rc6.d
-rwxr-xr-x 1 root root      306 2007-04-04 15:24 rc.local
drwxr-xr-x 2 root root     4096 2007-11-28 20:33 rcS.d
-rw-r--r-- 1 root root       89 2007-08-23 20:20 resolv.conf
-rwxr-xr-x 1 root root      268 2006-07-10 09:11 rmt
-rw-r--r-- 1 root root      887 2006-07-20 21:06 rpc
-rw-r--r-- 1 root root      994 2006-10-19 18:53 securetty
drwxr-xr-x 2 root root     4096 2007-04-04 15:24 security
-rw-r--r-- 1 root root    17750 2006-07-20 21:06 services
drwxr-xr-x 2 root root     4096 2007-04-12 18:58 sgml
-rw-r----- 1 root shadow    678 2008-01-22 14:19 shadow
-rw------- 1 root root      645 2007-04-04 19:38 shadow-
-rw-r--r-- 1 root root      165 2007-04-04 15:24 shells
drwxr-xr-x 2 root root     4096 2007-04-04 15:24 skel
drwxr-xr-x 2 root root     4096 2007-04-04 19:38 ssh
-r--r----- 1 root root      403 2007-04-04 15:31 sudoers
-rw-r--r-- 1 root root      949 2006-09-08 11:31 sysctl.conf
-rw-r--r-- 1 root root     1664 2006-10-06 09:46 syslog.conf
drwxr-xr-x 2 root root     4096 2007-04-04 15:24 terminfo
-rw-r--r-- 1 root root       11 2007-04-04 15:31 timezone
-rw-r--r-- 1 root root     1260 2004-10-28 14:50 ucf.conf
drwxr-xr-x 3 root root     4096 2007-04-11 19:31 udev
-rw-r--r-- 1 root root      805 2006-06-29 21:13 updatedb.conf
drwxr-xr-x 2 root root     4096 2007-11-28 20:34 vim
drwxr-xr-x 2 root root     4096 2007-04-11 19:33 w3m
-rw-r--r-- 1 root root     4221 2006-06-30 09:07 wgetrc
drwxr-xr-x 2 root root     4096 2007-04-04 15:26 wpa_supplicant
drwxr-xr-x 5 root root     4096 2007-04-11 19:30 X11
drwxr-xr-x 2 root root     4096 2007-04-12 18:58 xml
-rw-r--r-- 1 root root      674 2007-04-04 15:30 yaboot.conf
-rw-r--r-- 1 root root     4942 2001-06-04 11:59 zlibc.conf
```
Not everything belongs to one group in this case, they are very specific to the individual files and folders.

---

### Post by spookyct on 2008-01-25
Great...

What is the process for reinstalling?  Is there an easy way, or do I have to back everything up and re-format?

---

### Post by UltraMathMan on 2008-01-25
Backup /home/james (the entire folder) and when you reinstall you should be able to replace the /home/james that is created with the backed up one and set the ownership ```
sudo chown james:james /home/james
``` This should reset most of your personal settings at least, but backup files you want regardless. Good luck!

---

