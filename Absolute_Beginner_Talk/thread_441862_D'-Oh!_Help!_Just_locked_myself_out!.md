---
title: "D'-Oh! Help! Just locked myself out!"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by YoungCthulhu on 2007-05-13
Gidday, embarrassing revalation follows: ,

I've just partially locked myself out of my computer!  What an idiot!  :lolflag:  

I no longer have permission to access my home folder or ls the contents without using sudo!  I messed it up using GUI: "Places | Home Folder" to view my home folder where I have just installed Wine.  I selected the "show hidden files and directories" option and changed the permissions on .wine directory to read/write/execute for me (stuart) and this is when all the fun started.

I had been trying to un-hide the folder /home/stuart/.wine using chmod (see below) but to no avail.  Is it just a matter of renaming the directory from .wine to wine?

I also don't know why "sudo apt-get install wine" installed it in my home directory, and not /usr/share/.  Is this part of the problem?

Recent terminal output, following my "adjustments". 


> stuart@GORT:~$ sudo ls ~ -l
total 38196
-rw-r--r--   1 stuart stuart   486942 2007-05-09 19:55 ankylosaur a.xcf
-rw-r--r--   1 stuart stuart     7084 2007-04-26 19:15 contacts.csv
-rw-r--r--   1 stuart stuart    20228 2007-04-26 19:10 contacts.ods
-rw-r--r--   1 stuart stuart    26624 2007-04-26 19:06 contacts.xls
drwxr-xr-x   2 stuart stuart     4096 2007-05-12 17:02 Desktop
-rw-r--r--   1 stuart stuart    69455 2007-04-29 11:05 Dyson_walking_i.xcf
lrwxrwxrwx   1 stuart stuart       26 2007-04-22 20:25 Examples -> /usr/share/example-content
drwxr-xr-x   9 stuart stuart     4096 2007-04-23 20:28 google-earth
-rw-r--r--   1 stuart stuart   310272 2007-05-09 11:53 Mini Golf.xls
drwx------ 101 stuart stuart     4096 2006-06-19 19:06 My Music
-rw-r--r--   1 stuart stuart   102912 2007-05-09 11:53 PacMan.xls
drwxr-xr-x   8 stuart stuart    12288 2007-05-12 09:39 pictures
drwxr-xr-x  11 stuart stuart     4096 2007-05-12 16:11 RealPlayer
-rwxrwxrwx   1 stuart stuart  5802563 2007-05-11 16:41 RealPlayer10GOLD.bin
-rw-r--r--   1 stuart stuart     1591 2007-05-07 14:41 signature_1.html
-rw-r--r--   1 stuart stuart    46134 2007-05-07 14:41 signature_1_html_m105a8608.jpg
-rw-r--r--   1 stuart stuart    57653 2007-05-07 14:40 signature_1.odt
-rw-r--r--   1 stuart stuart  1535488 2007-05-09 11:52 Sonic The Hedgehog.xls
-rw-r--r--   1 stuart stuart    72192 2007-05-09 11:52 Tetris.xls
-rw-r--r--   1 stuart stuart 29258784 2007-05-11 22:10 The Golden Book of Chemistry Experiments (banned in the 60-s).pdf
drwxr-xr-x   3 stuart stuart     4096 2007-04-22 21:11 usr
-rw-------   1 stuart stuart  1177650 2007-05-11 12:22 Video(003).3gp
stuart@GORT:~$ sudo chmod +r+w+x .wine
stuart@GORT:~$ ls
ls: .: Permission denied
stuart@GORT:~$ sudo chmod -r-w-x .wine
stuart@GORT:~$ ls
ls: .: Permission denied
stuart@GORT:~$ 



Your comments and help would be much appreciated. :confused: 

Cheers

---

### Post by taurus on 2007-05-13
Can you post the whole output of this command?

```
ls -la ~
```

---

### Post by YoungCthulhu on 2007-05-13
Well, that was fun!... (not).  I am back again having just been locked out completely.  I got back in under safe terminal mode and changed the permissions on my home directory using "chmod 0644 ~" .

Thanks for your reply, Taurus.  Here's the listing you asked for:

> stuart@GORT:~$ ls -la ~
total 38656
drwxr--r--  49 stuart stuart     4096 2007-05-13 16:01 .
drwxr-xr-x   3 root   root       4096 2007-04-22 20:25 ..
-rw-r--r--   1 stuart stuart   486942 2007-05-09 19:55 ankylosaur a.xcf
-rw-------   1 stuart stuart     1643 2007-05-13 15:59 .bash_history
-rw-r--r--   1 stuart stuart      220 2007-04-22 20:25 .bash_logout
-rw-r--r--   1 stuart stuart     2298 2007-04-22 20:25 .bashrc
drwx------   2 stuart stuart     4096 2007-04-27 22:08 .camel_certs
drwxr-xr-x   2 stuart stuart     4096 2007-04-29 12:40 .cddb
drwx------   4 stuart stuart     4096 2007-04-24 22:20 .config
-rw-r--r--   1 stuart stuart     7084 2007-04-26 19:15 contacts.csv
-rw-r--r--   1 stuart stuart    20228 2007-04-26 19:10 contacts.ods
-rw-r--r--   1 stuart stuart    26624 2007-04-26 19:06 contacts.xls
drwx------   3 stuart stuart     4096 2007-05-07 14:54 .dbus
-rw-r--r--   1 stuart stuart       51 2007-05-10 01:07 .DCOPserver_GORT__0
lrwxrwxrwx   1 stuart stuart       32 2007-05-10 01:07 .DCOPserver_GORT_:0 -> /home/stuart/.DCOPserver_GORT__0
drwxr-xr-x   2 stuart stuart     4096 2007-05-12 17:02 Desktop
-rw-------   1 stuart stuart       24 2007-05-07 14:59 .dmrc
-rw-r--r--   1 stuart stuart    69455 2007-04-29 11:05 Dyson_walking_i.xcf
-rw-------   1 stuart stuart       16 2007-04-22 20:30 .esd_auth
drwxr-xr-x   9 stuart stuart     4096 2007-05-12 22:45 .evolution
lrwxrwxrwx   1 stuart stuart       26 2007-04-22 20:25 Examples -> /usr/share/example-content
drwxr-xr-x   2 stuart stuart     4096 2007-04-23 22:12 .fontconfig
drwx------   7 stuart stuart     4096 2007-05-13 16:01 .gconf
drwx------   2 stuart stuart     4096 2007-05-13 16:02 .gconfd
drwxr-xr-x  21 stuart stuart     4096 2007-05-12 14:22 .gimp-2.2
-rw-r-----   1 stuart stuart        0 2007-05-11 13:56 .gksu.lock
drwxr-xr-x   4 stuart stuart     4096 2007-04-23 20:28 .gnome
drwx------  16 stuart stuart     4096 2007-05-12 22:45 .gnome2
drwx------   2 stuart stuart     4096 2007-04-23 18:53 .gnome2_private
drwx------   5 stuart stuart     4096 2007-05-12 16:15 .googleearth
drwxr-xr-x   9 stuart stuart     4096 2007-04-23 20:28 google-earth
drwxr-xr-x   2 stuart stuart     4096 2007-04-27 22:19 .gpilotd
-rw-r--r--   1 stuart stuart        4 2007-04-27 22:19 .gpilotd.pid
drwxr-xr-x   2 stuart stuart     4096 2007-04-28 22:24 .gstreamer-0.10
-rw-------   1 stuart stuart       34 2007-05-09 15:25 .gtk-bookmarks
-rw-r--r--   1 stuart stuart      141 2007-04-29 11:24 .gtkrc-1.2-gnome2
-rw-------   1 stuart stuart     2076 2007-05-13 16:01 .ICEauthority
drwxr-xr-x   3 stuart stuart     4096 2007-04-29 10:41 .icons
drwx------   3 stuart stuart     4096 2007-05-07 14:49 .kde
drwx------   3 stuart stuart     4096 2007-04-23 20:28 .local
drwx------   3 stuart stuart     4096 2007-04-23 20:28 .loki
drwx------   3 stuart stuart     4096 2007-04-23 20:02 .macromedia
-rw-r--r--   1 stuart stuart     3099 2007-05-11 17:08 .mailcap
drwxr-xr-x   3 stuart stuart     4096 2007-04-24 20:01 .mcop
-rw-------   1 stuart stuart       31 2007-05-10 00:27 .mcoprc
drwx------   3 stuart stuart     4096 2007-04-22 20:30 .metacity
-rw-r--r--   1 stuart stuart   310272 2007-05-09 11:53 Mini Golf.xls
drwx------   4 stuart stuart     4096 2007-05-03 09:49 .mozilla
drwx------   3 stuart stuart     4096 2007-05-03 09:49 .mozilla-thunderbird
drwx------ 101 stuart stuart     4096 2006-06-19 19:06 My Music
drwxr-xr-x   3 stuart stuart     4096 2007-05-12 22:45 .nautilus
drwx------   3 stuart stuart     4096 2007-05-12 11:41 .openoffice.org2
-rw-r--r--   1 stuart stuart   102912 2007-05-09 11:53 PacMan.xls
drwxr-xr-x   8 stuart stuart    12288 2007-05-12 09:39 pictures
drwxr-xr-x   2 stuart stuart     4096 2007-04-24 22:23 .ppracer
-rw-r--r--   1 stuart stuart      566 2007-04-22 20:25 .profile
drwxr-xr-x   2 stuart stuart     4096 2007-04-24 20:00 .qt
drwxr-xr-x  11 stuart stuart     4096 2007-05-12 16:11 RealPlayer
-rwxrwxrwx   1 stuart stuart  5802563 2007-05-11 16:41 RealPlayer10GOLD.bin
-rw-------   1 stuart stuart    34704 2007-05-12 16:15 .realplayerrc
-rw-------   1 stuart stuart    71892 2007-05-12 14:22 .recently-used
-rw-r--r--   1 stuart stuart    95769 2007-05-13 13:04 .recently-used.xbel
drwx------   3 stuart stuart     4096 2007-04-23 00:46 .scim
-rw-r--r--   1 stuart stuart     1591 2007-05-07 14:41 signature_1.html
-rw-r--r--   1 stuart stuart    46134 2007-05-07 14:41 signature_1_html_m105a8608.jpg
-rw-r--r--   1 stuart stuart    57653 2007-05-07 14:40 signature_1.odt
drwxr-xr-x   3 stuart stuart     4096 2007-04-28 17:59 .solfege
-rw-r--r--   1 stuart stuart     3153 2007-05-03 19:57 .solfegerc
-rw-r--r--   1 stuart stuart  1535488 2007-05-09 11:52 Sonic The Hedgehog.xls
-rw-r--r--   1 stuart stuart      766 2007-05-09 19:55 .starplotrc
-rw-r--r--   1 stuart stuart        0 2007-04-22 20:30 .sudo_as_admin_successful
-rw-r--r--   1 stuart stuart    72192 2007-05-09 11:52 Tetris.xls
-rw-r--r--   1 stuart stuart 29258784 2007-05-11 22:10 The Golden Book of Chemistry Experiments (banned in the 60-s).pdf
drwxr-xr-x  17 stuart stuart     4096 2007-04-29 10:55 .themes
drwx------   5 stuart stuart     4096 2007-04-28 15:38 .thumbnails
drwxr-xr-x   3 stuart stuart     4096 2007-04-25 22:25 .tomboy
-rw-r--r--   1 stuart stuart      916 2007-05-06 17:13 .tomboy.log
drwx------   3 stuart stuart     4096 2007-05-12 17:02 .Trash
drwx------   2 stuart stuart     4096 2007-04-27 22:42 .tsclient
drwxr-xr-x   2 stuart stuart     4096 2007-04-22 20:50 .update-manager-core
drwx------   2 stuart stuart     4096 2007-04-22 20:30 .update-notifier
drwxr-xr-x   3 stuart stuart     4096 2007-04-22 21:11 usr
-rw-------   1 stuart stuart  1177650 2007-05-11 12:22 Video(003).3gp
drwxr-xr-x   3 stuart stuart     4096 2007-04-24 19:59 .vlc
drwxr-xr-x   2 stuart stuart     4096 2007-05-06 17:13 .wapi
d---------   4 stuart stuart     4096 2007-05-13 14:21 .wine
-rw-------   1 stuart stuart      115 2007-05-13 16:01 .Xauthority
drwxr-xr-x   2 stuart stuart     4096 2007-04-24 20:01 .xine
-rw-r--r--   1 stuart stuart     4141 2007-05-13 16:02 .xsession-errors
stuart@GORT:~$ 


It's possibly fixed now, but I'm still not fully sure of what happened so I can _learn something_ from this "adventure".

PS: Given my track record it is probably not a good idea anyway, but I can't get root privileges.  I typed "su -l" but it wouldn't accept my login password.  What's happening?

Cheers

---

