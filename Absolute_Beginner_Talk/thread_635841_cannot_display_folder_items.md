---
title: "cannot display folder items"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by monstersdad on 2007-12-09
while accessing home/music folders several times a message appears "cannot display folder items"     and closing the subsequent folder repeats the message for that folder and the others in that directory ? only a reboot seems to fix the problem (Temporarily). Any ideas? I am using Gutsy

---

### Post by ptn107 on 2007-12-09
Can you post or pastebin the output of

```
ls -la ~/
```

---

### Post by monstersdad on 2007-12-09
How do I do this ?

---

### Post by ptn107 on 2007-12-09
Click *Applications -> Accessories -> Terminal*

and type (or paste)

```
ls -la ~/ 
```

---

### Post by monstersdad on 2007-12-14
total 252
drwxr-xr-x 44 dad  dad   4096 2007-12-14 19:15 .
drwxr-xr-x  3 root root  4096 2007-11-24 22:40 ..
drwx------  2 dad  avg   4096 2007-12-09 13:57 .AbiSuite
drwxr-xr-x  4 dad  avg   4096 2007-12-09 18:55 .alien-arena
drwxr-xr-x  4 dad  dad   4096 2007-12-14 21:30 .aMule
drwxr-xr-x  4 dad  dad   4096 2007-11-25 14:25 .avg7
-rw-------  1 dad  dad     78 2007-12-09 14:28 .bash_history
-rw-r--r--  1 dad  dad    220 2007-11-24 22:40 .bash_logout
-rw-r--r--  1 dad  dad   2298 2007-11-24 22:40 .bashrc
drwxr-xr-x  6 dad  dad   4096 2007-11-25 09:08 .cache
drwxr-xr-x  8 dad  dad   4096 2007-11-25 09:10 .config
drwxr-xr-x  2 dad  dad   4096 2007-12-08 13:35 Desktop
-rw-------  1 dad  avg     26 2007-12-14 19:15 .dmrc
drwxr-xr-x  8 dad  dad   4096 2007-12-08 13:35 Documents
-rw-------  1 dad  dad     16 2007-11-24 22:47 .esd_auth
drwxr-xr-x  8 dad  avg   4096 2007-12-10 05:22 .evolution
lrwxrwxrwx  1 dad  dad     26 2007-11-24 22:40 Examples -> /usr/share/example-content
drwxr-xr-x  2 dad  dad   4096 2007-11-30 15:23 .fontconfig
drwxr-xr-x  2 dad  avg   4096 2007-11-30 15:23 .fonts
drwx------  5 dad  dad   4096 2007-12-14 19:15 .gconf
drwx------  2 dad  dad   4096 2007-12-14 21:29 .gconfd
-rw-r-----  1 dad  dad      0 2007-12-14 19:27 .gksu.lock
drwxr-xr-x  3 dad  dad   4096 2007-11-24 22:47 .gnome
drwx------ 14 dad  dad   4096 2007-12-10 05:22 .gnome2
drwx------  2 dad  dad   4096 2007-11-24 22:47 .gnome2_private
drwxr-xr-x  2 dad  dad   4096 2007-11-25 00:37 .gstreamer-0.10
-rw-r--r--  1 dad  avg    133 2007-12-14 19:15 .gtk-bookmarks
-rw-r--r--  1 dad  dad     85 2007-11-24 22:47 .gtkrc-1.2-gnome2
-rw-------  1 dad  avg   1243 2007-12-14 19:15 .ICEauthority
drwxr-xr-x  2 dad  dad   4096 2007-11-24 23:21 .icons
drwxr-xr-x  3 dad  avg   4096 2007-12-03 14:42 .java
drwx------  4 dad  dad   4096 2007-11-26 08:56 .kde
-rw-------  1 dad  avg    160 2007-11-26 08:56 .kderc
drwxr-xr-x  3 dad  dad   4096 2007-11-24 22:47 .local
drwx------  3 dad  dad   4096 2007-11-25 00:49 .macromedia
drwxr-xr-x  3 dad  dad   4096 2007-11-25 09:55 .mcop
-rw-------  1 dad  avg     31 2007-12-08 18:31 .mcoprc
drwx------  3 dad  dad   4096 2007-11-24 23:32 .mozilla
drwx------  3 dad  dad   4096 2007-11-24 23:28 .mozilla-thunderbird
drwxr-xr-x 22 dad  dad   4096 2007-12-09 13:01 Music
drwxr-xr-x  3 dad  dad   4096 2007-12-10 05:22 .nautilus
-rw-r--r--  1 dad  avg  11751 2007-12-09 09:53 nautilus-debug-log.txt
drwx------  3 dad  dad   4096 2007-12-09 14:05 .openoffice.org2
drwxr-xr-x  5 dad  dad   4096 2007-12-09 12:08 Pictures
-rw-r--r--  1 dad  dad    566 2007-11-24 22:40 .profile
drwxr-xr-x  2 dad  dad   4096 2007-11-24 22:47 Public
drwxr-xr-x  2 dad  dad   4096 2007-11-26 08:56 .qt
-rw-------  1 dad  dad   1195 2007-12-02 11:56 .recently-used
-rw-r--r--  1 dad  avg    218 2007-12-10 05:22 .recently-used.xbel
-rw-r--r--  1 dad  dad      0 2007-11-24 22:48 .sudo_as_admin_successful
drwxr-xr-x  2 dad  dad   4096 2007-11-24 22:47 Templates
drwxr-xr-x  2 dad  dad   4096 2007-11-24 23:21 .themes
drwx------  5 dad  dad   4096 2007-11-25 15:58 .thumbnails
drwx------  2 dad  dad   4096 2007-12-10 05:22 .Trash
drwxr-xr-x  2 dad  dad   4096 2007-11-24 22:48 .update-manager-core
drwx------  2 dad  dad   4096 2007-11-24 22:47 .update-notifier
drwxr-xr-x  2 dad  dad   4096 2007-12-09 19:08 Videos
drwx------  2 dad  dad   4096 2007-11-25 09:14 .w3m
drwxr-xr-x  2 dad  avg   4096 2007-12-02 12:50 .wapi
-rw-------  1 dad  avg    122 2007-12-14 19:15 .Xauthority
drwxr-xr-x  2 dad  dad   4096 2007-11-25 09:55 .xine
drwx------  5 dad  avg   4096 2007-12-02 11:15 .xmoto
-rw-r--r--  1 dad  avg   5376 2007-12-14 20:56 .xsession-errors
dad@dad-desktop:~$

---

