---
title: "ls or dir?"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by OmnificienT on 2006-12-29
Is there any diffirence between the commands ls and dir? I only notice that ls displays things in colours and dir doesn't.


Thank You.

---

### Post by dbott67 on 2006-12-29
They're both essentially the same (to provide a directory listing).  You can get colors with dir:
```
dir --color=always
```

You can find all the options & switches using **man dir**.

-Dave

---

### Post by OmnificienT on 2006-12-29
What are options and switches exactly?

---

### Post by dbott67 on 2006-12-29
They are the optional parts of many commands that can be added to provide more information.  For example, a very common switch is to type **--help** or **-h** after the command to see the help screen.

For **ls**, the switch **-al** shows all files (including hidden files) and lists them in a long format (showing permissions, owner, date/time, etc.)
```
dbott@thedrake:~$ ls -al | more
total 133832
drwxr-xr-x 75 dbott dbott     4096 2006-12-29 09:14 .
drwxr-xr-x  6 root  root      4096 2006-08-03 06:59 ..
-rw-r--r--  1 root  root         0 2006-12-10 22:39 1
-rw-r--r--  1 dbott dbott   203320 2006-11-16 15:18 1_NAT_2_Routers.png
drwxr-xr-x  2 dbott dbott     4096 2006-12-24 21:11 2006-12-24--21.10.39
-rw-r-----  1 dbott dbott   205562 2006-12-03 15:33 2006_JK_Lindsay.jpeg
drwxr-xr-x  2 dbott dbott     4096 2006-12-11 11:14 archive
-rw-r--r--  1 dbott dbott      189 2006-12-11 11:41 .asoundrc
-rw-r--r--  1 dbott dbott      360 2006-12-11 11:42 .asoundrc.asoundconf
-rwxr-xr-x  1 dbott dbott 57776757 2006-12-11 12:02 ati-driver-installer-8.29.6.run
-rwxr-xr-x  1 dbott dbott  1185962 2006-11-10 23:29 auth.log.0
drwxr-xr-x  2 dbott root      4096 2006-12-12 21:05 .automatix
-rw-------  1 dbott dbott     9382 2006-12-29 09:18 .bash_history
-rw-r--r--  1 dbott dbott      220 2006-11-10 21:07 .bash_logout
-rw-r--r--  1 dbott dbott      414 2006-11-10 21:07 .bash_profile
-rw-r--r--  1 dbott dbott     2227 2006-11-10 21:07 .bashrc
drwxr-xr-x  2 dbott dbott     4096 2006-11-18 16:34 .beryl
-rw-r--r--  1 dbott dbott       74 2006-11-18 18:45 .beryl-managerrc
drwxr-xr-x  4 dbott dbott     4096 2006-11-10 23:43 .bmp
-rw-r--r--  1 dbott dbott    23325 2006-12-24 21:38 Card2006.odg
drwxr-xr-x  5 dbott dbott     4096 2006-12-16 13:39 .childsplay
-rw-r--r--  1 dbott dbott      243 2006-12-27 19:02 .childsplay.score
drwx------  2 dbott dbott     4096 2006-12-24 21:10 .comments
drwxr-xr-x  4 dbott dbott     4096 2006-11-10 22:47 .config
-rwxr-xr-x  1 dbott dbott 30412318 2006-11-10 21:14 cube_2005_08_29_unix.tar.gz
drwx------  2 dbott dbott     4096 2006-11-27 15:01 .cups
-rw-------  1 dbott dbott       77 2006-11-28 19:43 .cvspass
drwxr-xr-x  2 dbott dbott     4096 2006-11-10 22:22 data
drwxr-xr-x  6 dbott dbott     4096 2006-12-10 12:37 .democracy
drwxr-xr-x  4 dbott dbott     4096 2006-12-28 23:25 Desktop
-rw-r--r--  1 dbott dbott   321703 2006-12-20 20:38 D-Link-Port-Forward.png
-rw-------  1 dbott dbott       24 2006-11-18 21:59 .dmrc
-rw-r--r--  1 dbott dbott   212246 2006-11-16 14:54 Dual_NAT.png
-rw-r--r--  1 dbott dbott   215272 2006-11-16 15:57 Dual_NAT_Untrusted.png
drwxr-xr-x  2 dbott dbott     4096 2006-12-11 15:24 dvd
drwxr-xr-x  2 dbott dbott     4096 2006-12-11 15:22 .dvdrip
-rw-r--r--  1 dbott dbott    21486 2006-12-11 15:28 .dvdriprc
-rw-r--r--  1 dbott dbott      543 2006-11-18 22:35 .dvrrc
drwxr-xr-x  4 dbott dbott     4096 2006-11-18 16:32 .emerald
-rw-------  1 dbott dbott       16 2006-11-10 21:13 .esd_auth
drwxr-xr-x  7 dbott dbott     4096 2006-12-29 09:13 .evolution
lrwxrwxrwx  1 dbott dbott       26 2006-11-10 21:07 Examples -> /usr/share/example-content
-rw-r--r--  1 dbott dbott   915450 2006-12-10 09:04 Firefox_crash.png
-rw-r--r--  1 dbott dbott   816066 2006-11-10 21:59 Firefox_wallpaper.png
-rw-r--r--  1 dbott dbott        0 2006-12-10 19:19 .fonts.cache-1
drwx------  4 dbott dbott     4096 2006-12-29 14:22 .gaim
drwxr-xr-x  6 dbott dbott     4096 2006-12-28 16:05 .gcompris
drwx------  5 dbott dbott     4096 2006-12-29 09:14 .gconf
drwx------  2 dbott dbott     4096 2006-12-29 15:32 .gconfd
drwxr-xr-x  7 dbott dbott     4096 2006-12-12 23:01 .gdesklets
drwx------  3 dbott dbott     4096 2006-12-18 22:04 .gftp
drwxr-xr-x 21 dbott dbott     4096 2006-12-24 21:58 .gimp-2.2
-rw-r-----  1 dbott dbott        0 2006-12-28 21:50 .gksu.lock
drwxr-xr-x  5 dbott dbott     4096 2006-12-11 11:41 .gnome
drwx------ 16 dbott dbott     4096 2006-12-29 09:13 .gnome2
drwx------  2 dbott dbott     4096 2006-11-10 21:13 .gnome2_private
drwx------  2 dbott dbott     4096 2006-11-10 23:04 .gnupg
lrwxrwxrwx  1 dbott dbott       37 2006-12-10 22:39 googleearth -> /home/dbott/google-earth//googleearth
drwxr-xr-x  9 dbott dbott     4096 2006-12-10 22:39 google-earth
-rwxr-xr-x  1 dbott dbott 21466938 2006-11-30 16:13 GoogleEarthLinux.bin
drwxr-xr-x  2 dbott dbott     4096 2006-12-10 23:25 .gstreamer-0.10
-rw-r--r--  1 dbott dbott       87 2006-11-10 21:13 .gtkrc-1.2-gnome2
--More--

```
Type **man** followed by any command to see the options & switches available
-Dave

---

### Post by OmnificienT on 2006-12-29
So -al is a switch, but what is an option then?

---

### Post by confused57 on 2006-12-29
Maybe something here that will help clarify:

[http://www.ubuntuforums.org/showthread.php?t=171507](http://www.ubuntuforums.org/showthread.php?t=171507)

---

