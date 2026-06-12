---
title: "I followed something I shouldn't have, please help..."
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by SunnyM on 2006-09-28
Okay, I followed the advice in [this thread]("http://www.ubuntuforums.org/showthread.php?t=97243"), which was to > **aysiu said:**
> The /var directory is owned by root and cannot be written to by the user.

You have two options:

1. Change ownership of the directory, using the *chown* command ```
sudo chown -R yourusername:yourusergroupname /var/www
```

2. Open your /home directory. Then Run (Alt-F2) the command ```
gksudo nautilus
``` and open up /var/www. Create a directory in your /home directory (say, /home/www) that you middle-click-drag to /var/www and select "link here."

I prefer the latter option, but it's your choice.

I did the first one, and now I get this error when trying to do anything using sudo.

```
sudo: /etc/sudoers is owned by uid 1000, should be 0
```

How can I undo this?

---

### Post by llamakc on 2006-09-28
Sounds as if you chown'ed / instead of /var/www. Can you confirm by typing:

ls -l /etc/

Is everything owned by you?

---

### Post by SunnyM on 2006-09-28
*nods* It all came up as being owned by mojo (me).

---

### Post by llamakc on 2006-09-28
How about the contents of /

ls -lh /

---

### Post by SunnyM on 2006-09-28
That came up as root.

---

### Post by llamakc on 2006-09-28
cd into directories in /etc and see if _those_ files are owned by you.

My Edgy /etc looks like:

```

drwxr-xr-x 8 root   root      4096 2006-09-21 20:05 acpi
-rw-r--r-- 1 root   root      2584 2006-09-15 04:14 adduser.conf
-rw-r--r-- 1 root   root        45 2006-09-27 13:00 adjtime
-rw-r--r-- 1 root   root        48 2006-09-21 19:50 aliases
drwxr-xr-x 2 root   root      4096 2006-09-27 07:48 alternatives
-rw-r--r-- 1 root   root       364 2006-07-20 17:07 anacrontab
drwxr-xr-x 7 root   root      4096 2006-09-15 04:18 apm
drwxr-xr-x 4 root   root      4096 2006-09-22 06:44 apt
-rw-r----- 1 root   daemon     144 2006-07-20 21:15 at.deny
-rw-r--r-- 1 root   root      1565 2006-09-19 17:24 bash.bashrc
-rw-r--r-- 1 root   root    215918 2006-09-19 17:24 bash_completion
drwxr-xr-x 2 root   root      4096 2006-09-23 09:03 bash_completion.d
drwxr-xr-x 2 root   root      4096 2006-09-21 20:05 belocs
-rw-r--r-- 1 root   root       526 2006-09-27 07:47 blkid.tab
-rw-r--r-- 1 root   root       526 2006-09-22 21:30 blkid.tab.old
drwxr-xr-x 2 root   root      4096 2006-09-15 04:18 bluetooth
drwxr-xr-x 2 root   root      4096 2006-09-15 04:19 bonobo-activation
-rw-r--r-- 1 root   root        33 2006-09-15 04:19 brlapi.key
drwxr-xr-x 2 root   root      4096 2006-09-15 04:24 brltty
-rw-r--r-- 1 root   root     13262 2006-08-17 01:57 brltty.conf
-rw-r--r-- 1 root   root      4800 2006-09-15 04:18 ca-certificates.conf
drwxr-xr-x 2 root   root      4096 2006-09-15 04:18 calendar
drwxr-xr-x 2 root   root      4096 2006-09-15 04:16 cdrecord
drwxr-s--- 2 root   dip       4096 2006-09-15 04:18 chatscripts
drwxr-xr-x 2 root   root      4096 2006-09-15 04:14 console
drwxr-xr-x 2 root   root      4096 2006-09-23 09:03 console-setup
drwxr-xr-x 2 root   root      4096 2006-09-21 20:05 console-tools
drwxr-xr-x 2 root   root      4096 2006-09-21 20:05 cron.d
drwxr-xr-x 2 root   root      4096 2006-09-28 07:38 cron.daily
drwxr-xr-x 2 root   root      4096 2006-09-15 04:18 cron.hourly
drwxr-xr-x 2 root   root      4096 2006-09-25 06:02 cron.monthly
-rw-r--r-- 1 root   root       651 2006-07-20 21:14 crontab
drwxr-xr-x 2 root   root      4096 2006-09-21 20:05 cron.weekly
drwxr-sr-t 5 cupsys lp        4096 2006-09-27 07:46 cups
drwxr-xr-x 4 root   root      4096 2006-09-21 20:05 dbus-1
-rw-r--r-- 1 root   root      2673 2006-07-24 10:19 debconf.conf
-rw-r--r-- 1 root   root        17 2006-06-30 09:03 debian_version
drwxr-xr-x 2 root   root      4096 2006-09-27 07:48 default
drwxr-xr-x 4 root   root      4096 2006-09-15 04:20 defoma
-rw-r--r-- 1 root   root       600 2006-07-10 10:35 deluser.conf
drwxr-xr-x 4 root   root      4096 2006-09-15 04:17 devfs
drwxr-xr-x 4 root   root      4096 2006-09-21 20:05 dhcp3
drwxr-xr-x 2 root   root      4096 2006-09-15 04:25 dictionaries-common
drwxr-xr-x 3 root   root      4096 2006-09-15 04:18 dpkg
drwxr-xr-x 3 root   root      4096 2006-09-21 19:56 emacs
drwxr-xr-x 3 root   root      4096 2006-09-21 19:56 emacs21
-rw-r--r-- 1 root   root       111 2006-09-21 19:50 environment
drwxr-xr-x 2 root   root      4096 2006-09-15 04:18 esound
drwxr-xr-x 2 root   root      4096 2006-09-27 07:46 event.d
-rw-r--r-- 1 root   root       354 2006-06-23 09:16 fdmount.conf
-rw-r--r-- 1 root   root       183 2006-05-21 09:46 festival.scm
drwxr-xr-x 4 root   root      4096 2006-09-22 06:53 firefox
drwxr-xr-x 3 root   root      4096 2006-09-21 20:04 fonts
drwxr-xr-x 3 root   root      4096 2006-09-15 04:19 foomatic
-rw-r--r-- 1 root   root       748 2006-09-15 04:14 fstab
-rw-r--r-- 1 root   root        37 2006-09-15 04:13 fstab.pre-uuid
-rw-r--r-- 1 root   root       132 2006-07-22 07:09 ftpusers
drwxr-xr-x 2 root   root      4096 2006-09-21 20:05 gaim
drwxr-xr-x 2 root   root      4096 2006-09-15 04:19 gamin
drwxr-xr-x 5 root   root      4096 2006-09-15 04:16 gconf
drwxr-xr-x 7 root   root      4096 2006-09-21 20:06 gdm
drwxr-xr-x 3 root   root      4096 2006-09-21 20:24 ggi
drwxr-xr-x 3 root   root      4096 2006-09-15 04:17 gimp
drwxr-xr-x 2 root   root      4096 2006-09-28 12:32 gmailfs
drwxr-xr-x 3 root   root      4096 2006-09-15 04:18 gnome
drwxr-xr-x 3 root   root      4096 2006-09-15 04:18 gnome-system-tools
drwxr-xr-x 4 root   root      4096 2006-09-15 04:17 gnome-vfs-2.0
-rw-r--r-- 1 root   root     10852 2006-06-19 07:05 gnome-vfs-mime-magic
drwxr-xr-x 2 root   root      4096 2006-09-22 06:53 gre.d
drwxr-xr-x 2 root   root      4096 2006-09-15 04:18 groff
-rw-r--r-- 1 root   root       799 2006-09-25 15:49 group
-rw------- 1 root   root       787 2006-09-23 13:52 group-
-rw-r----- 1 root   shadow     677 2006-09-25 15:49 gshadow
-rw------- 1 root   root       668 2006-09-23 13:52 gshadow-
drwxr-xr-x 2 root   root      4096 2006-09-25 08:29 gtk
drwxr-xr-x 2 root   root      4096 2006-09-15 04:22 gtk-2.0
drwxr-xr-x 3 root   root      4096 2006-09-15 04:16 hal
-rw-r--r-- 1 root   root      4728 2006-07-20 19:03 hdparm.conf
-rw-r--r-- 1 root   root        26 2006-06-30 09:03 host.conf
-rw-r--r-- 1 root   root         8 2006-09-21 19:51 hostname
-rw-r--r-- 1 root   root       243 2006-09-21 19:51 hosts
-rw-r--r-- 1 root   root       677 2006-09-15 04:14 hosts.allow
-rw-r--r-- 1 root   root       901 2006-09-15 04:14 hosts.deny
drwxr-xr-x 2 root   root      4096 2006-09-27 07:44 hp
-rw-r--r-- 1 root   root       154 2006-09-21 19:51 iftab
-rw-r--r-- 1 root   root        68 2006-09-25 06:44 inetd.conf
drwxr-xr-x 2 root   root      4096 2006-09-27 07:48 init.d
drwxr-xr-x 5 root   root      4096 2006-09-21 20:07 initramfs-tools
-rw-r--r-- 1 root   root      1698 2006-03-21 06:42 inputrc
drwxr-xr-x 2 root   root      4096 2006-09-15 04:14 iproute2
-rw-r--r-- 1 root   root        40 2006-07-03 14:55 issue
-rw-r--r-- 1 root   root        33 2006-07-03 14:55 issue.net
drwxr-xr-x 3 root   root      4096 2006-09-15 04:16 java
drwxr-xr-x 3 root   root      4096 2006-09-25 09:38 java-1.5.0-sun
-rw-r--r-- 1 root   root       294 2006-05-08 05:56 jvm
drwxr-xr-x 2 root   root      4096 2006-06-15 05:24 jvm.d
-rw-r--r-- 1 root   root       179 2006-09-21 19:52 kernel-img.conf
drwxr-xr-x 8 root   root      4096 2006-09-21 20:05 laptop-mode
drwxr-xr-x 2 root   root      4096 2006-09-15 04:14 ldap
-rw-r--r-- 1 root   root     40713 2006-09-28 17:47 ld.so.cache
-rw-r--r-- 1 root   root        15 2006-09-15 04:18 ld.so.conf
drwxr-xr-x 2 root   root      4096 2006-09-21 20:02 ld.so.conf.d
-rw-r--r-- 1 root   root        70 2006-09-21 20:04 ld.so.hwcappkgs
-rw-r--r-- 1 root   root      3300 2006-07-05 23:08 lftp.conf
-rw-r--r-- 1 root   root        22 2006-07-01 11:59 libao.conf
drwxr-xr-x 2 root   root      4096 2006-09-15 04:18 libgda
drwxr-xr-x 2 root   root      4096 2006-07-10 12:53 libpaper.d
-rw-r--r-- 1 root   root      2586 2003-12-04 01:57 locale.alias
-rw-r--r-- 1 root   root      1279 2006-09-22 15:08 localtime
drwxr-xr-x 5 root   root      4096 2006-09-15 04:16 logcheck
-rw-r--r-- 1 root   root     10679 2006-09-23 13:52 login.defs
-rw-r--r-- 1 root   root       599 2006-06-19 13:21 logrotate.conf
drwxr-xr-x 2 root   root      4096 2006-09-22 15:08 logrotate.d
drwxr-xr-x 2 root   root      4096 2006-07-27 12:05 lsb-base
-rw-r--r-- 1 root   root      3770 2006-09-21 12:12 lsb-base-logging.sh
-rw-r--r-- 1 root   root       116 2006-06-08 04:41 lsb-release
-rw-r--r-- 1 root   root     10814 2006-02-20 15:55 ltrace.conf
-rw-r--r-- 1 root   root       111 2006-07-04 13:06 magic
-rw-r--r-- 1 root   root     14227 2006-09-25 09:38 mailcap
-rw-r--r-- 1 root   root       449 2006-06-15 15:13 mailcap.order
-rw-r--r-- 1 root   root      4696 2005-09-26 10:11 manpath.config
-rw-r--r-- 1 root   root     11742 2006-06-23 09:17 mediaprm
drwxr-xr-x 2 root   root      4096 2006-09-22 06:53 menu-methods
-rw-r--r-- 1 root   root     20423 2006-06-15 15:13 mime.types
-rw-r--r-- 1 root   root       330 2006-06-29 20:02 mke2fs.conf
drwxr-xr-x 3 root   root      4096 2006-09-27 07:48 modprobe.d
-rw-r--r-- 1 root   root       198 2006-09-21 19:52 modules
drwxr-xr-x 2 root   root      4096 2006-09-15 04:19 modutils
drwxr-xr-x 4 root   root      4096 2006-09-21 20:05 mono
lrwxrwxrwx 1 root   root        13 2006-09-21 19:43 motd -> /var/run/motd
-rw-r--r-- 1 root   root       266 2006-09-15 04:14 motd.tail
drwxr-xr-x 2 root   root      4096 2006-09-27 07:48 mplayer
-rw-r--r-- 1 root   root       293 2006-09-13 16:46 mplayerplug-in.conf
-rw-r--r-- 1 root   root       857 2006-09-13 16:46 mplayerplug-in.types
-rw-r--r-- 1 root   root       530 2006-09-27 13:01 mtab
drwxr-xr-x 2 root   root      4096 2006-09-25 06:02 mysql
-rw-r--r-- 1 root   root      7620 2006-07-10 10:07 nanorc
drwxr-xr-x 6 root   root      4096 2006-09-22 14:11 network
drwxr-xr-x 3 root   root      4096 2006-09-22 07:24 NetworkManager
-rw-r--r-- 1 root   root       465 2006-02-09 11:35 nsswitch.conf
drwxr-xr-x 2 root   root      4096 2006-06-15 15:37 ODBCDataSources
-rw-r--r-- 1 root   root         0 2006-06-15 15:37 odbc.ini
-rw-r--r-- 1 root   root         0 2006-06-15 15:37 odbcinst.ini
drwxr-xr-x 2 root   root      4096 2006-09-23 09:03 openoffice
drwxr-xr-x 2 root   root      4096 2006-09-15 04:13 opt
-rw-r--r-- 1 root   root       552 2006-06-29 12:57 pam.conf
drwxr-xr-x 2 root   root      4096 2006-09-25 06:02 pam.d
drwxr-xr-x 2 root   root      4096 2006-09-15 04:20 pango
-rw-r--r-- 1 root   root         3 2006-09-15 04:18 papersize
-rw-r--r-- 1 root   root      1347 2006-09-25 06:02 passwd
-rw------- 1 root   root      1309 2006-09-25 06:02 passwd-
drwxr-xr-x 2 root   root      4096 2006-09-15 04:14 pcmcia
drwxr-xr-x 4 root   root      4096 2006-09-15 04:15 perl
-rw-r--r-- 1 root   root       104 2006-08-30 07:46 pmount.allow
-rw-r--r-- 1 root   root      7649 2006-09-15 04:19 pnm2ppa.conf
-rw-r--r-- 1 root   root       342 2006-09-21 19:52 popularity-contest.conf
drwxr-xr-x 4 root   root      4096 2006-09-15 04:16 power
drwxr-xr-x 8 root   dip       4096 2006-09-15 04:18 ppp
-rw-r--r-- 1 root   root       316 2006-09-28 07:35 printcap
-rw-r--r-- 1 root   root       369 2006-09-15 04:14 profile
drwxr-xr-x 2 root   root      4096 2006-09-25 06:03 proftpd
-rw-r--r-- 1 root   root      2478 2006-07-20 20:06 protocols
drwxr-xr-x 2 root   root      4096 2006-09-15 04:14 python
drwxr-xr-x 2 root   root      4096 2006-09-15 04:14 python2.4
drwxr-xr-x 2 root   root      4096 2006-09-25 06:02 rc0.d
drwxr-xr-x 2 root   root      4096 2006-09-25 06:02 rc1.d
drwxr-xr-x 2 root   root      4096 2006-09-25 06:02 rc2.d
drwxr-xr-x 2 root   root      4096 2006-09-25 06:02 rc3.d
drwxr-xr-x 2 root   root      4096 2006-09-25 06:02 rc4.d
drwxr-xr-x 2 root   root      4096 2006-09-25 06:02 rc5.d
drwxr-xr-x 2 root   root      4096 2006-09-25 06:02 rc6.d
-rwxr-xr-x 1 root   root       306 2006-09-15 04:14 rc.local
drwxr-xr-x 2 root   root      4096 2006-09-21 20:03 rcS.d
drwxr-xr-x 2 root   root      4096 2006-09-21 20:05 readahead
-rw-r--r-- 1 root   root        42 2006-09-28 16:24 resolv.conf
-rwxr-xr-x 1 root   root       268 2006-07-10 09:53 rmt
-rw-r--r-- 1 root   root       887 2006-07-20 20:06 rpc
drwxr-xr-x 2 root   root      4096 2006-09-15 04:19 samba
drwxr-xr-x 3 root   root      4096 2006-09-15 04:19 sane.d
drwxr-xr-x 2 root   root      4096 2006-09-15 04:22 scim
-rw-r--r-- 1 root   root      3578 2006-04-26 16:40 screenrc
-rw-r--r-- 1 root   root        23 2006-05-29 17:35 scrollkeeper.conf
-rw-r--r-- 1 root   root       994 2006-07-11 10:11 securetty
drwxr-xr-x 2 root   root      4096 2006-09-15 04:14 security
-rw-r--r-- 1 root   root     17750 2006-07-20 20:06 services
drwxr-xr-x 3 root   root      4096 2006-09-25 07:03 sgml
-rw-r----- 1 root   shadow     924 2006-09-25 06:02 shadow
-rw------- 1 root   root       924 2006-09-25 06:02 shadow-
-rw-r--r-- 1 root   root       192 2006-09-23 13:52 shells
drwxr-xr-x 2 root   root      4096 2006-09-21 20:02 skel
drwxr-xr-x 3 root   root      4096 2006-09-15 04:16 sound
drwxr-xr-x 2 root   root      4096 2006-09-21 19:57 ssh
drwxr-xr-x 4 root   root      4096 2006-09-15 04:18 ssl
-r--r----- 1 root   root       403 2006-09-21 19:50 sudoers
-rw-r--r-- 1 root   root       764 2006-09-08 10:24 sysctl.conf
-rw-r--r-- 1 root   root      1664 2006-07-29 18:20 syslog.conf
drwxr-xr-x 2 root   root      4096 2006-09-15 04:14 terminfo
-rw-r--r-- 1 root   root        16 2006-09-21 19:51 timezone
-rw-r--r-- 1 root   root      1260 2004-10-28 13:50 ucf.conf
drwxr-xr-x 3 root   root      4096 2006-09-27 07:45 udev
-rw-r--r-- 1 root   root       142 2006-07-12 12:53 uniconf.conf
-rw-r--r-- 1 root   root       805 2006-06-29 19:59 updatedb.conf
drwxr-xr-x 2 root   root      4096 2006-09-03 05:39 update-notifier
-rw-r--r-- 1 root   root        48 2006-09-15 04:19 usplash.conf
drwxr-xr-x 2 root   root      4096 2006-09-15 04:14 vim
-rw-r--r-- 1 root   root      4622 2006-07-04 05:06 vnc.conf
drwxr-xr-x 2 root   root      4096 2006-09-15 04:18 w3m
-rw-r--r-- 1 root   root      4221 2006-06-30 08:03 wgetrc
drwxr-xr-x 2 root   root      4096 2006-09-15 04:14 wpa_supplicant
-rw-r----- 1 root   dialout     66 2006-09-15 04:19 wvdial.conf
drwxr-xr-x 9 root   root      4096 2006-09-25 16:27 X11
drwxr-xr-x 4 root   root      4096 2006-09-15 04:17 xdg
drwxr-xr-x 2 root   root      4096 2006-09-25 07:03 xml

```

---

### Post by SunnyM on 2006-09-28
Yup, they all said mojo, too.:(

---

### Post by llamakc on 2006-09-28
I would chown them all recursively to root:root and then fix the ones you need to, like /etc/shadow and /etc/gshadow as in the example I have above.

```

cd /etc && sudo chown -R root:root .

```

Will chown recursively in /etc, then fix the stragglers like shadow.

---

### Post by SunnyM on 2006-09-28
When I tried that, I got the same error.

```
sudo: /etc/sudoers is owned by uid 1000, should be 0

```

---

### Post by sbergman27 on 2006-09-28
> **SunnyM said:**
> When I tried that, I got the same error.

```
sudo: /etc/sudoers is owned by uid 1000, should be 0

```

If you have set a root passwd, you can:

```
$ su -
```

and give it the root password to become root. (You'll get a "#" prompt instead of a "$".)

If you have not set a root password, you need to go to single user mode. (Recovery mode)

Reboot and hit escape when grub is loading.

Select Recovery mode for whatever kernel you are running and you should boot into a "#" prompt.

You're now root.  Be careful.

I'll look around and see if there is an automated way in Ubuntu to set your file ownerships back to something sane.  Stay tuned.

-Steve

---

### Post by SunnyM on 2006-09-28
Ok, thanks... *waits and hopes*

---

### Post by llamakc on 2006-09-28
Make sure to fix gshadow and shadow.

---

### Post by llamakc on 2006-09-28
Doh! Good catch. I forgot that was your original error you asked about.

---

### Post by SunnyM on 2006-09-28
lol, it's okay. Thanks for trying.:KS

---

### Post by sbergman27 on 2006-09-28
I don't see an automated way to do this.  But I'm redhat and rpm-centric.

So, as llmakc suggests, as root:

```

# cd /etc
# chown -R root:root .

```

Then go back to each of the files that does not have a user or group of root, and:

```

# chown the_owner_name:the_group_name filename

```

where the_owner_name is the owner,
the_group_name is the group,
and filename is the file.

This, hopefully, will get you back to a reasonable starting point.

---

### Post by sbergman27 on 2006-09-28
Here is a script, based upon my dapper installation that should set your ownerships and group membership back to what they should be.  

This assumes that you have already set everything to root:root as outlined in the last message.

Cut and paste it into a file called fix_etc.sh.  Put it on the machine in question, and as root, and in the directory where it exists:

sh ./fix_etc.sh

```

#!/bin/bash
cd /etc
chown root:root ./sysctl.conf
chown root:dip ./chatscripts
chown root:dip ./chatscripts/provider
chown root:dialout ./wvdial.conf
chown smmta:smmsp ./mail
chown smmta:smmsp ./mail/tls
chown root:smmsp ./mail/tls/sendmail-common.key
chown root:smmsp ./mail/tls/sendmail-server.crt
chown root:smmsp ./mail/tls/sendmail-client.crt
chown root:smmsp ./mail/trusted-users
chown smmta:smmsp ./mail/access.db
chown root:smmsp ./mail/Makefile
chown root:smmsp ./mail/sasl
chown root:smmsp ./mail/submit.mc
chown smmta:smmsp ./mail/m4
chown root:smmsp ./mail/m4/provider.m4
chown root:smmsp ./mail/m4/dialup.m4
chown smmta:smmsp ./mail/aliases.db
chown root:smmsp ./mail/sendmail.cf
chown root:smmsp ./mail/local-host-names
chown root:smmsp ./mail/sendmail.mc
chown root:smmsp ./mail/submit.cf
chown smmta:smmsp ./mail/smrsh
chown cupsys:lp ./cups
chown cupsys:lp ./cups/printers.conf.O
chown cupsys:lp ./cups/ppd
chown cupsys:lp ./cups/ppd/laser.ppd
chown cupsys:lp ./cups/printers.conf
chown cupsys:lp ./cups/ssl
chown root:dip ./ppp
chown root:dip ./ppp/peers
chown root:dip ./ppp/peers/kppp-options
chown root:dip ./ppp/peers/provider
chown root:daemon ./at.deny
chown root:shadow ./gshadow
chown root:shadow ./shadow

```

---

### Post by llamakc on 2006-09-28
He may not have sendmail or any equivalent installed. Also, he'll need to make any script executable.

---

### Post by sbergman27 on 2006-09-28
> **llamakc said:**
> He may not have sendmail or any equivalent installed. Also, he'll need to make any script executable.

True, but if not, it'll just print an error.  He could have files in /etc that I don't, though.

By executing with 'sh ./fix_etc.sh' it doesn't need to be set executable.

Personally, if I didn't have a lot invested in the current install, I'd be inclined to save my home directory off somewhere and start from scratch.

---

### Post by llamakc on 2006-09-28
I agree. I started doing the separate partition for /home some time ago and it makes life much easier.

the `sh ./name.sh` thing makes sense. I didn't put two and two together. Neat. Thanks.

---

