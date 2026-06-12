---
title: "Help with /etc group membership"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Roque on 2007-09-21
I accidentally changed the group of all /etc folders (but not the owner, which is still root)
Could someone tell me which group they belong to?

Many thanks!

---

### Post by asmoore82 on 2007-09-21
:KS
```
:~$ ls -l /etc/
total 1232
drwxr-xr-x  8 root   root      4096 2007-04-15 07:55 acpi
-rw-r--r--  1 root   root      2657 2007-04-15 07:49 adduser.conf
-rw-r--r--  1 root   root        45 2007-08-08 23:47 adjtime
-rw-r--r--  1 root   root        52 2007-08-08 17:34 aliases
drwxr-xr-x  2 root   root      4096 2007-09-09 11:30 alternatives
-rw-r--r--  1 root   root       395 2007-03-05 01:38 anacrontab
drwxr-xr-x  7 root   root      4096 2007-04-15 07:55 apm
drwxr-xr-x  4 root   root      4096 2007-09-09 11:28 apt
-rw-r-----  1 root   daemon     144 2007-02-20 08:41 at.deny
drwxr-xr-x  4 root   root      4096 2007-04-15 07:55 avahi
-rw-r--r--  1 root   root      1566 2007-04-10 19:32 bash.bashrc
-rw-r--r--  1 root   root       278 2007-04-10 03:34 bash_command_not_found
-rw-r--r--  1 root   root    215938 2007-04-10 19:32 bash_completion
drwxr-xr-x  2 root   root      4096 2007-08-08 23:42 bash_completion.d
drwxr-xr-x  2 root   root      4096 2007-04-15 07:49 belocs
-rw-r--r--  1 root   root       248 2007-08-08 23:42 blkid.tab
-rw-r--r--  1 root   root       248 2007-08-08 17:38 blkid.tab.old
drwxr-xr-x  2 root   root      4096 2007-04-15 07:55 bluetooth
drwxr-xr-x  2 root   root      4096 2007-04-15 07:59 bonobo-activation
-rw-r--r--  1 root   root        33 2007-04-15 07:59 brlapi.key
drwxr-xr-x  2 root   root      4096 2007-04-15 08:02 brltty
-rw-r--r--  1 root   root     13262 2007-03-27 08:39 brltty.conf
-rw-r--r--  1 root   root      4832 2007-04-15 07:55 ca-certificates.conf
drwxr-xr-x  2 root   root      4096 2007-04-15 07:55 calendar
drwxr-s---  2 root   dip       4096 2007-04-15 07:55 chatscripts
drwxr-xr-x  2 root   root      4096 2007-04-15 07:49 console-setup
drwxr-xr-x  2 root   root      4096 2007-04-15 07:49 console-tools
drwxr-xr-x  2 root   root      4096 2007-04-15 07:55 cron.d
drwxr-xr-x  2 root   root      4096 2007-08-08 23:40 cron.daily
drwxr-xr-x  2 root   root      4096 2007-04-15 07:55 cron.hourly
drwxr-xr-x  2 root   root      4096 2007-04-15 07:55 cron.monthly
-rw-r--r--  1 root   root       724 2006-12-20 09:46 crontab
drwxr-xr-x  2 root   root      4096 2007-04-15 07:55 cron.weekly
drwxr-sr-t  5 cupsys lp        4096 2007-04-15 07:59 cups
drwxr-xr-x  4 root   root      4096 2007-08-08 23:40 dbus-1
-rw-r--r--  1 root   root      2673 2007-03-24 13:35 debconf.conf
-rw-r--r--  1 root   root         4 2006-10-28 09:20 debian_version
drwxr-xr-x  2 root   root      4096 2007-08-10 22:25 default
drwxr-xr-x  4 root   root      4096 2007-04-15 07:59 defoma
-rw-r--r--  1 root   root       600 2006-11-28 05:47 deluser.conf
drwxr-xr-x  4 root   root      4096 2007-04-15 07:53 devfs
drwxr-xr-x  4 root   root      4096 2007-04-15 07:49 dhcp3
drwxr-xr-x  2 root   root      4096 2007-04-15 08:03 dictionaries-common
drwxr-xr-x  3 root   root      4096 2007-04-15 07:55 dpkg
drwxr-xr-x  3 root   root      4096 2007-04-15 07:51 emacs
-rw-r--r--  1 root   root        98 2007-08-08 17:33 environment
drwxr-xr-x  2 root   root      4096 2007-04-15 07:54 esound
drwxr-xr-x  2 root   root      4096 2007-04-15 07:49 event.d
-rw-r--r--  1 root   root       354 2007-03-05 01:54 fdmount.conf
-rw-r--r--  1 root   root      8366 2007-01-28 17:48 ffserver.conf
drwxr-xr-x  4 root   root      4096 2007-08-08 23:40 firefox
drwxr-xr-x  4 root   root      4096 2007-04-15 07:53 fonts
drwxr-xr-x  3 root   root      4096 2007-04-15 07:53 foomatic
-rw-r--r--  1 root   root       540 2007-04-15 07:49 fstab
-rw-r--r--  1 root   root        37 2007-04-15 07:48 fstab.pre-uuid
drwxr-xr-x  2 root   root      4096 2007-04-15 07:56 gaim
drwxr-xr-x  2 root   root      4096 2007-04-15 07:59 gamin
drwxr-xr-x  5 root   root      4096 2007-04-15 07:50 gconf
drwxr-xr-x  7 root   root      4096 2007-04-15 08:01 gdm
drwxr-xr-x  3 root   root      4096 2007-09-09 10:48 ggi
drwxr-xr-x  3 root   root      4096 2007-04-15 07:52 gimp
drwxr-xr-x  3 root   root      4096 2007-04-15 07:55 gnome
drwxr-xr-x  2 root   root      4096 2007-08-08 23:40 gnome-app-install
drwxr-xr-x  3 root   root      4096 2007-04-15 07:53 gnome-system-tools
drwxr-xr-x  4 root   root      4096 2007-04-15 07:50 gnome-vfs-2.0
-rw-r--r--  1 root   root     10852 2006-11-09 14:16 gnome-vfs-mime-magic
drwxr-xr-x  2 root   root      4096 2007-08-08 23:40 gre.d
drwxr-xr-x  2 root   root      4096 2007-04-15 07:55 groff
-rw-r--r--  1 root   root       898 2007-08-08 17:34 group
-rw-------  1 root   root       891 2007-08-08 17:34 group-
-rw-r-----  1 root   shadow     765 2007-08-08 17:34 gshadow
-rw-------  1 root   root       758 2007-08-08 17:34 gshadow-
drwxr-xr-x  2 root   root      4096 2007-08-08 22:14 gtk
drwxr-xr-x  2 root   root      4096 2007-04-15 08:00 gtk-2.0
drwxr-xr-x  3 root   root      4096 2007-04-15 07:52 hal
-rw-r--r--  1 root   root      4793 2007-03-04 23:45 hdparm.conf
-rw-r--r--  1 root   root        92 2006-12-20 10:50 host.conf
-rw-r--r--  1 root   root        16 2007-08-08 17:34 hostname
-rw-r--r--  1 root   root       251 2007-08-08 17:34 hosts
drwxr-xr-x  2 root   root      4096 2007-04-15 07:59 hp
-rw-r--r--  1 root   root       121 2007-08-08 17:34 iftab
drwxr-xr-x  2 root   root      4096 2007-08-10 22:25 init.d
drwxr-xr-x  5 root   root      4096 2007-04-15 07:49 initramfs-tools
-rw-r--r--  1 root   root      1723 2007-04-10 17:46 inputrc
drwxr-xr-x  2 root   root      4096 2007-04-15 07:49 iproute2
-rw-r--r--  1 root   root        19 2007-04-12 05:11 issue
-rw-r--r--  1 root   root        12 2007-04-12 05:11 issue.net
drwxr-xr-x  3 root   root      4096 2007-04-15 07:52 java
drwxr-xr-x  4 root   root      4096 2007-08-08 22:37 java-6-sun
-rw-r--r--  1 root   root       294 2006-05-08 06:56 jvm
drwxr-xr-x  2 root   root      4096 2007-02-23 06:11 jvm.d
drwxr-xr-x  4 root   root      4096 2007-09-09 11:20 kde3
-rw-r--r--  1 root   root       167 2007-08-08 17:38 kernel-img.conf
drwxr-xr-x  8 root   root      4096 2007-04-15 07:55 laptop-mode
drwxr-xr-x  2 root   root      4096 2007-04-15 07:49 ldap
-rw-r--r--  1 root   root     53179 2007-09-09 11:30 ld.so.cache
-rw-r--r--  1 root   root        33 2007-04-15 07:48 ld.so.conf
drwxr-xr-x  2 root   root      4096 2007-04-15 07:49 ld.so.conf.d
-rw-r--r--  1 root   root        45 2007-04-15 07:49 ld.so.hwcappkgs
-rw-r--r--  1 root   root      3300 2007-03-07 08:57 lftp.conf
-rw-r--r--  1 root   root        22 2006-07-01 12:59 libao.conf
drwxr-xr-x  2 root   root      4096 2007-04-15 07:55 libgda
drwxr-xr-x  2 root   root      4096 2007-03-05 16:40 libpaper.d
-rw-r--r--  1 root   root      2586 2003-12-04 02:57 locale.alias
-rw-r--r--  1 root   root      1267 2007-08-08 23:37 localtime
drwxr-xr-x  5 root   root      4096 2007-04-15 07:51 logcheck
-rw-r--r--  1 root   root      9707 2006-12-19 15:35 login.defs
-rw-r--r--  1 root   root       599 2006-06-19 14:21 logrotate.conf
drwxr-xr-x  2 root   root      4096 2007-08-08 23:42 logrotate.d
drwxr-xr-x  2 root   root      4096 2007-04-10 14:44 lsb-base
-rw-r--r--  1 root   root      3786 2007-04-10 09:25 lsb-base-logging.sh
-rw-r--r--  1 root   root        97 2007-04-12 02:02 lsb-release
-rw-r--r--  1 root   root     10814 2006-02-20 16:55 ltrace.conf
-rw-r--r--  1 root   root       111 2007-03-24 12:09 magic
-rw-r--r--  1 root   root     16330 2007-09-09 11:30 mailcap
-rw-r--r--  1 root   root       449 2006-12-06 13:13 mailcap.order
-rw-r--r--  1 root   root      4696 2007-04-05 15:48 manpath.config
-rw-r--r--  1 root   root     11742 2007-03-05 01:54 mediaprm
drwxr-xr-x  2 root   root      4096 2007-08-08 23:41 menu-methods
-rw-r--r--  1 root   root     20847 2006-12-06 13:13 mime.types
-rw-r--r--  1 root   root       330 2007-03-28 09:45 mke2fs.conf
drwxr-xr-x  3 root   root      4096 2007-08-08 23:42 modprobe.d
-rw-r--r--  1 root   root       203 2007-08-08 17:37 modules
drwxr-xr-x  2 root   root      4096 2007-04-15 07:56 modutils
drwxr-xr-x  4 root   root      4096 2007-04-15 07:56 mono
lrwxrwxrwx  1 root   root        13 2007-08-08 17:21 motd -> /var/run/motd
-rw-r--r--  1 root   root       266 2007-04-15 07:49 motd.tail
drwxr-xr-x  2 root   root      4096 2007-09-09 10:48 mplayer
-rw-r--r--  1 root   root       578 2007-09-17 23:11 mtab
-rw-r--r--  1 root   root      7672 2007-02-07 06:32 nanorc
-rw-r--r--  1 root   root       611 2007-03-05 21:05 Net
-rw-r--r--  1 root   root      2064 2006-11-23 14:33 netscsid.conf
drwxr-xr-x  6 root   root      4096 2007-04-15 07:49 network
drwxr-xr-x  3 root   root      4096 2007-04-15 07:53 NetworkManager
-rw-r--r--  1 root   root        91 2006-12-20 10:50 networks
-rw-r--r--  1 root   root       513 2007-04-15 07:56 nsswitch.conf
drwxr-xr-x  2 root   root      4096 2006-06-15 16:37 ODBCDataSources
-rw-r--r--  1 root   root         0 2006-06-15 16:37 odbc.ini
-rw-r--r--  1 root   root         0 2006-06-15 16:37 odbcinst.ini
-rw-r--r--  1 root   root        60 2006-12-12 10:32 openalrc
drwxr-xr-x  2 root   root      4096 2007-08-08 23:42 openoffice
drwxr-xr-x  2 root   root      4096 2007-04-15 07:48 opt
-rw-r--r--  1 root   root       552 2006-12-20 12:58 pam.conf
drwxr-xr-x  2 root   root      4096 2007-09-09 11:20 pam.d
drwxr-xr-x  2 root   root      4096 2007-04-15 07:54 pango
-rw-r--r--  1 root   root         3 2007-04-15 07:55 papersize
-rw-r--r--  1 root   root      1385 2007-08-10 22:25 passwd
-rw-------  1 root   root      1335 2007-08-08 17:34 passwd-
drwxr-xr-x  2 root   root      4096 2007-04-15 07:49 pcmcia
drwxr-xr-x  4 root   root      4096 2007-04-15 07:49 perl
-rw-r--r--  1 root   root      7649 2007-04-15 07:59 pnm2ppa.conf
-rw-r--r--  1 root   root       342 2007-08-08 17:37 popularity-contest.conf
drwxr-xr-x  4 root   root      4096 2007-04-15 07:51 power
drwxr-xr-x  8 root   dip       4096 2007-04-15 07:55 ppp
drwxr-xr-x  2 root   root      4096 2006-11-27 10:39 pppstatus
-rw-r--r--  1 root   root       369 2007-04-15 07:49 profile
-rw-r--r--  1 root   root      2478 2007-03-30 05:46 protocols
drwxr-xr-x  2 root   root      4096 2007-09-09 10:48 pulse
drwxr-xr-x  2 root   root      4096 2007-04-15 07:49 python
drwxr-xr-x  2 root   root      4096 2007-08-08 23:36 python2.5
drwxr-xr-x  2 root   root      4096 2007-09-09 11:20 qt3
drwxr-xr-x  2 root   root      4096 2007-08-08 17:39 rc0.d
drwxr-xr-x  2 root   root      4096 2007-08-10 22:25 rc1.d
drwxr-xr-x  2 root   root      4096 2007-08-10 22:25 rc2.d
drwxr-xr-x  2 root   root      4096 2007-08-10 22:25 rc3.d
drwxr-xr-x  2 root   root      4096 2007-08-10 22:25 rc4.d
drwxr-xr-x  2 root   root      4096 2007-08-10 22:25 rc5.d
drwxr-xr-x  2 root   root      4096 2007-08-08 17:39 rc6.d
-rwxr-xr-x  1 root   root       306 2007-04-15 07:49 rc.local
drwxr-xr-x  2 root   root      4096 2007-04-15 07:59 rcS.d
drwxr-xr-x  2 root   root      4096 2007-04-15 07:56 readahead
drwxr-xr-x  3 root   root      4096 2007-04-15 07:52 resolvconf
-rw-r--r--  1 root   root        72 2007-09-20 21:06 resolv.conf
-rwxr-xr-x  1 root   root       268 2006-12-18 08:44 rmt
-rw-r--r--  1 root   root       887 2007-03-30 05:46 rpc
drwxr-xr-x  2 root   root      4096 2007-08-08 23:42 samba
drwxr-xr-x  3 root   root      4096 2007-04-15 07:56 sane.d
drwxr-xr-x  2 root   root      4096 2007-04-15 08:00 scim
-rw-r--r--  1 root   root      3578 2007-03-08 12:00 screenrc
-rw-r--r--  1 root   root        23 2007-03-09 08:38 scrollkeeper.conf
-rw-r--r--  1 root   root       994 2006-12-19 15:35 securetty
drwxr-xr-x  2 root   root      4096 2007-04-15 07:49 security
-rw-r--r--  1 root   root     18038 2007-03-30 05:46 services
drwxr-xr-x  3 root   root      4096 2007-08-08 23:41 sgml
-rw-r-----  1 root   shadow     848 2007-08-10 22:25 shadow
-rw-------  1 root   root       848 2007-08-10 22:25 shadow-
-rw-r--r--  1 root   root       181 2007-04-15 07:55 shells
drwxr-xr-x  2 root   root      4096 2007-04-15 07:52 skel
drwxr-xr-x  3 root   root      4096 2007-04-15 07:50 sound
drwxr-xr-x  2 root   root      4096 2007-08-10 22:25 ssh
drwxr-xr-x  4 root   root      4096 2007-04-15 07:55 ssl
-r--r-----  1 root   root       403 2007-08-08 17:34 sudoers
-rw-r--r--  1 root   root       764 2007-03-07 16:42 sysctl.conf
-rw-r--r--  1 root   root      1664 2007-03-08 11:46 syslog.conf
drwxr-xr-x  2 root   root      4096 2007-04-15 07:49 terminfo
-rw-r--r--  1 root   root        17 2007-08-08 17:35 timezone
-rw-r--r--  1 root   root      1260 2006-11-16 14:35 ucf.conf
drwxr-xr-x  3 root   root      4096 2007-04-15 07:56 udev
-rw-r--r--  1 root   root       142 2007-02-05 05:54 uniconf.conf
-rw-r--r--  1 root   root       805 2007-03-05 01:52 updatedb.conf
drwxr-xr-x  2 root   root      4096 2007-04-10 03:46 update-notifier
-rw-r--r--  1 root   root        48 2007-08-08 17:37 usplash.conf
drwxr-xr-x  2 root   root      4096 2007-08-08 23:27 vim
-rw-r--r--  1 root   root      4622 2007-03-08 16:58 vnc.conf
drwxr-xr-x  2 root   root      4096 2007-04-15 07:55 w3m
-rw-r--r--  1 root   root      4221 2006-12-13 06:35 wgetrc
-rw-r--r--  1 root   root      1343 2007-01-09 13:39 wodim.conf
drwxr-xr-x  2 root   root      4096 2007-04-15 07:49 wpa_supplicant
-rw-r-----  1 root   dialout     66 2007-04-15 07:59 wvdial.conf
drwxr-xr-x 10 root   root      4096 2007-09-17 23:11 X11
drwxr-xr-x  4 root   root      4096 2007-04-15 07:52 xdg
drwxr-xr-x  2 root   root      4096 2007-04-15 07:54 xml
-rw-r--r--  1 root   root       399 2007-03-30 05:52 zsh_command_not_found
```

---

### Post by Roque on 2007-09-21
Many thanks for your help!  
So it seems it won't be safe to do:
chown -R root:root /etc

I'll have to change them manually

---

### Post by Roque on 2007-09-21
I finally did it with this handy switch:
chown -Rv --from=root:wrong_group root:root /etc

:)

---

