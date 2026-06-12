---
title: "Need help badly permissions seem really ruined!"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by MkfIbK7a on 2007-02-22
ok i dont know what did it but i have a sneaking suspicion wine had something to do with it...

anyhow my problem is this, at first i couldnt log into my comp because of messed up permissions but i fixed it. it turned out /home/user/ belonged to root...

now its doing this when i try to remove something,


```
jon@albert:~$ sudo apt-get remove ekiga
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

```

and this when i do "gksudo" anything,


```
jon@albert:~$ gksudo xfe
GConf Error: Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
GConf Error: Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
GConf Error: Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
GConf Error: Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0

(gksudo:4418): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
GConf Error: Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Read-only file systemjon@albert:~$ xfe
warning: can't save config file - /home/jon/.config/mousepad/mousepadrc

```

i really need help here or else im going to have to reinstall ubuntu:( 

PS: i forgot i also cant open nautilus OR firefox. and when i try to install something it complains also.

thx,
wert

---

### Post by taurus on 2007-02-22
What's the output of this command?

```
ls -la /home/jon
```

---

### Post by MkfIbK7a on 2007-02-22
here is the output

> jon@albert:~$ ls -la /home/jon/
total 159448
drwxr-xr-x 129 jon  jon          8192 2007-02-22 10:59 .
drwxr-xr-x   4 root root         4096 2007-02-06 18:22 ..
-rw-r--r--   1 jon  jon        354492 2007-02-08 12:47 3145.tar.gz
-rw-r--r--   1 jon  jon      18241399 2007-02-06 03:24 ActionCube_v0.92.tar.bz2
-rw-r--r--   1 jon  jon           557 2007-02-12 19:18 add.pl
-rw-r--r--   1 jon  jon           593 2007-02-08 15:32 add.pl~
-rw-r--r--   1 jon  jon           444 2007-01-23 02:17 .adesklets
-rw-r--r--   1 jon  jon         13590 2007-02-20 14:39 alien.jpg
drwx------   2 jon  jon          4096 2007-02-05 11:29 .aptitude
-rw-r--r--   1 jon  jon            42 2007-01-08 11:50 .aspell.en.prepl
-rw-r--r--   1 jon  jon            22 2007-01-08 11:50 .aspell.en.pws
drwxr-xr-x   2 jon  root         4096 2007-01-29 20:04 .automatix
drwxr-xr-x   2 jon  jon          4096 2007-01-14 20:32 .avidemux
drwx------   4 jon  jon          4096 2007-01-19 00:08 .ayttm
-rw-r--r--   1 jon  jon           404 2007-01-29 22:28 .balazar
drwxr-xr-x   3 jon  jon          4096 2007-01-29 22:27 .balazar_saved_games
-rw-------   1 jon  jon          8681 2007-02-21 17:07 .bash_history
-rw-r--r--   1 jon  jon           220 2006-12-28 07:43 .bash_logout
-rw-r--r--   1 jon  jon           414 2006-12-28 07:43 .bash_profile
-rw-r--r--   1 jon  jon          2227 2006-12-28 07:43 .bashrc
drwxr-xr-x  17 jon  jon          4096 2000-06-09 08:16 BegPerl
-rw-r--r--   1 jon  jon         26120 2007-02-20 20:54 betterpalmtree.jpg
-rw-r--r--   1 jon  jon            84 2007-02-21 19:05 .BillardGL.conf.v7
drwxr-xr-x   5 jon  jon          4096 2007-02-21 20:46 .blender
-rw-r--r--   1 jon  jon           100 2007-02-21 16:27 .Blog
drwxr-xr-x   2 jon  jon          4096 2007-01-22 19:57 .bluefish
-rw-r--r--   1 jon  jon         24164 2007-02-22 09:45 bomb.zip
-rw-r--r--   1 jon  jon         28526 2007-02-22 09:45 bridge.zip
drwxr-xr-x   3 jon  jon          4096 2007-01-29 18:50 .briquolo
-rw-r--r--   1 jon  jon         61440 2007-02-05 23:22 bze-1.4-20050405.tar.gz
-rw-r--r--   1 jon  jon        882263 2007-02-07 13:31 BZEditW32_1.6.5_Installer.exe
drwxr-xr-x   8 jon  jon          4096 2007-02-12 15:24 .bzf
-rw-r--r--   1 jon  jon        203459 2007-02-07 00:13 bzfed-0.1.tar.gz
-rw-r--r--   1 jon  jon      10474544 2007-02-12 13:16 bzflag_2.0.9.20070128-1_i386.deb
drwx------   5 jon  jon          4096 2007-01-09 21:07 .cache
-rw-------   1 jon  jon           632 2007-02-19 13:18 .camstream
drwxr-xr-x   2 jon  jon          4096 2007-02-01 19:36 .camstream-upload
drwxr-xr-x   5 jon  jon          4096 2007-02-14 01:15 .childsplay
-rw-r--r--   1 jon  jon           597 2007-02-14 01:15 .childsplay.score
drwxr-xr-x   2 jon  jon          4096 2007-01-09 21:31 .circlebuttonbar
drwx------  10 jon  jon          4096 2007-01-21 01:35 .config
drwxr-x---   2 jon  conquest     4096 2007-02-02 00:09 .conquest
-rw-r--r--   1 jon  jon         75310 2007-02-05 22:49 consts.bzw
drwxr-xr-x   3 jon  jon          4096 2007-01-14 14:33 .crossfire
-rw-r--r--   1 jon  jon           110 2007-02-21 19:07 .csmashrc
-rw-r--r--   1 jon  jon           181 2007-01-28 20:18 .cuyo
drwxr-xr-x   3 jon  jon          4096 2007-01-23 00:39 .desklets
drwx------   7 jon  jon          4096 2007-02-18 22:18 Desktop
drwx------   2 jon  jon          4096 2007-01-15 20:58 .dillo
-rw-r--r--   1 jon  jon            24 2007-02-20 16:32 .dmrc
drwxr-xr-x   4 jon  jon          4096 2007-01-22 20:04 .e
drwxr-xr-x   3 jon  jon          4096 2007-01-22 19:18 .e16menuedit2
drwx------   4 jon  jon          4096 2007-01-22 20:03 .ecore
drwxr-xr-x  15 jon  jon          4096 2007-02-22 09:58 egoboo
drwxr-xr-x   8 jon  jon          4096 2007-02-22 09:58 .egoboo
-rw-r--r--   1 jon  jon         10009 2007-02-17 22:57 egoboo.txt
-rw-r--r--   1 jon  jon       8723442 2007-02-22 08:42 egoextra.zip
drwx------   2 jon  jon          4096 2007-01-30 10:46 .elc
drwx------   2 jon  games        4096 2007-02-10 23:28 .emilia
-rw-r--r--   1 jon  jon        471736 2007-02-05 11:17 empsave.dat
drwxr-xr-x   4 jon  jon          4096 2007-02-05 11:23 .enigma
-rw-r--r--   1 jon  jon          1123 2007-02-20 23:20 .enigmarc2
drwx------   6 jon  jon          4096 2007-02-18 19:02 .enlightenment
-rw-r--r--   1 jon  jon            62 2007-02-19 16:05 errorlog.txt
drwxr-xr-x   3 jon  jon          4096 2007-01-29 10:09 .evolution
drwxr-xr-x   5 jon  jon          4096 2007-01-25 13:48 .exaile
-rw-r--r--   1 jon  jon         22834 2007-01-29 10:11 .face
-rw-r--r--   1 jon  jon          6132 2007-02-19 18:37 .fbhighlevelshistory
-rw-r--r--   1 jon  jon           195 2007-01-25 09:18 .fbhighscores
drwxr-xr-x   2 jon  jon          4096 2007-01-28 20:08 .fblevels
-rw-r--r--   1 jon  jon           543 2007-02-19 18:35 .fbrc
drwx------   7 jon  jon          4096 2007-02-05 01:35 .fceultra
drwx------   2 jon  jon          4096 2007-01-30 09:45 .fgfs
drwxr-xr-x   2 jon  jon          4096 2007-01-25 14:30 .file_store_32
-rw-r--r--   1 jon  jon         28999 2007-02-22 09:46 fireswor.zip
-rw-r--r--   1 jon  jon           107 2007-02-06 20:36 first.pl
-rw-r--r--   1 jon  jon           613 2007-01-25 19:19 .flobopuyorc
drwx------   3 jon  jon          4096 2007-01-27 22:10 .flock
drwxr-xr-x   5 jon  jon          4096 2007-01-07 23:50 .fluxbox
-rw-r--r--   1 jon  jon        169048 2007-01-23 02:05 .fonts.cache-1
drwxr-xr-x   3 jon  jon          4096 2007-01-08 02:28 .foxrc
drwxr-xr-x   2 jon  jon          4096 2007-01-21 01:38 .fvwm
drwxr-xr-x   5 jon  jon          4096 2007-01-28 16:23 .fvwm-crystal
drwx------   5 jon  jon          4096 2007-02-22 08:52 .gaim
drwxr-xr-x   6 jon  jon          4096 2007-01-21 18:59 .gcompris
drwx------   4 jon  jon          4096 2007-02-22 09:26 .gconf
drwx------   2 jon  jon          4096 2007-02-22 10:55 .gconfd
drwxr-xr-x   7 jon  jon          4096 2007-01-23 15:59 .gdesklets
drwxr-xr-x   3 jon  jon          4096 2007-02-02 00:08 .gearhead
-rw-r--r--   1 jon  jon          4607 2007-02-07 21:05 GG_END
-rw-r--r--   1 jon  jon          2095 2007-02-05 23:16 GG_S_03
-rw-r--r--   1 jon  jon          3504 2007-02-05 10:35 GG_S_05
-rw-r--r--   1 jon  jon          3277 2007-02-12 12:09 GG_S_06
-rw-r--r--   1 jon  jon          3698 2007-02-06 20:11 GG_S_12
drwxr-xr-x  21 jon  jon          4096 2007-02-20 23:39 .gimp-2.2
-rw-r-----   1 jon  jon             0 2007-02-22 09:47 .gksu.lock
drwx------   2 jon  jon          4096 2007-02-03 20:21 .gl-117
-rw-r--r--   1 jon  jon          2345 2007-02-04 21:04 .gltronrc
drwxr-xr-x   4 jon  jon          4096 2007-01-29 20:11 .gnome
drwx------  15 jon  jon          4096 2007-02-19 22:10 .gnome2
drwx------   2 jon  jon          4096 2006-12-28 19:31 .gnome2_private
drwx------   2 jon  jon          4096 2006-12-28 17:03 .gnupg
lrwxrwxrwx   1 jon  jon            35 2007-01-29 20:10 googleearth -> /home/jon/google-earth//googleearth
drwx------   5 jon  jon          4096 2007-02-21 17:11 .googleearth
drwxr-xr-x   9 jon  jon          4096 2007-01-29 20:11 google-earth
-rwxr-xr-x   1 jon  jon      21607720 2007-01-05 23:53 GoogleEarthLinux.bin
drwx------   2 jon  jon          4096 2006-12-28 17:34 .gphoto
drwxr-xr-x   5 jon  jon          4096 2007-02-21 14:27 .gqview
drwxr-xr-x   2 jon  jon          4096 2007-01-13 18:47 .gstreamer-0.10
drwxr-xr-x   5 jon  jon          4096 2007-01-28 20:24 .gtkboard
-rw-------   1 jon  jon             0 2007-01-15 20:53 .gtk-bookmarks
-rw-r--r--   1 jon  jon            85 2007-01-01 19:13 .gtkrc-1.2-gnome2
drwx------   2 jon  jon          4096 2007-02-01 19:25 .gxine
-rw-r--r--   1 jon  jon        159076 2007-02-07 13:57 half.blend
-rw-r--r--   1 jon  jon        691412 2007-02-21 16:27 halfyingyang.blend
-rw-r--r--   1 jon  jon          3109 2007-02-10 19:40 HH01_64kb.m3u
-rw-------   1 jon  jon          8735 2007-02-20 23:22 .ICEauthority
-rw-r--r--   1 jon  jon        452364 2007-02-16 16:33 icebeach.jpg
-rw-r--r--   1 jon  jon           668 2007-02-18 23:27 .icebreaker
drwxr-xr-x   2 jon  jon          4096 2007-02-20 14:54 .icewm
-rw-r--r--   1 jon  jon         68589 2007-02-07 17:16 iChat Image(Rts).jpeg
drwxr-xr-x   3 jon  jon          4096 2007-01-21 01:35 .icons
drwxr-xr-x   3 jon  jon          4096 2007-02-01 19:18 .ida
drwxr-xr-x   2 jon  jon          4096 2007-01-25 22:26 .imgseek
drwxr-xr-x   3 jon  jon          4096 2006-12-28 20:16 .java
-rw-r--r--   1 jon  jon        436510 2007-02-20 21:20 jon.png
-rw-r--r--   1 jon  jon       1369263 2007-02-14 18:49 jon.tar.gz
drwx------   4 jon  jon          4096 2007-01-21 03:03 .kde
-rw-r--r--   1 jon  jon             7 2007-01-17 18:59 .komirc
-rw-r--r--   1 jon  jon            45 2007-01-09 16:38 .ktemperatue
-rw-------   1 jon  jon            35 2007-02-19 01:14 .lesshst
drwx------   4 jon  games        4096 2007-01-26 13:59 .lgames
-rw-r--r--   1 jon  jon        168102 2007-02-12 13:52 libcurl3_7.15.5-1_i386.deb
-rw-r--r--   1 jon  jon       2716198 2007-02-12 13:48 libssl0.9.8_0.9.8c-4_i386.deb
drwx------   2 jon  jon          4096 2007-01-27 22:58 .links2
drwxr-xr-x   3 jon  jon          4096 2007-01-27 21:39 .listen
drwxr-xr-x   3 jon  jon          4096 2006-12-28 12:50 .local
drwx------   3 jon  jon          4096 2007-01-29 20:11 .loki
drwxr-xr-x   3 jon  jon          4096 2007-01-23 20:41 .luola
-rw-r--r--   1 jon  jon        133084 2007-02-07 13:13 m2-1.3-20061220.tar.gz
drwx------   4 jon  jon          4096 2006-12-31 00:51 .macromedia
drwxr-xr-x   3 jon  jon          4096 2006-12-28 17:36 .mcop
-rw-------   1 jon  jon            31 2007-01-09 02:00 .mcoprc
drwx------   3 jon  jon          4096 2007-01-01 19:13 .metacity
-rw-r--r--   1 jon  jon          5689 2007-02-06 11:45 mine.bzw
-rw-r--r--   1 jon  jon            46 2007-01-03 19:09 .missilecommandrc
drwx------   2 jon  jon          4096 2007-02-09 01:11 .moagg
drwxr-x---   2 jon  jon          4096 2007-02-01 23:53 .mog
drwx------   4 jon  jon          4096 2007-01-27 23:13 .mozilla
drwx------   3 jon  jon          4096 2007-01-27 23:13 .mozilla-thunderbird
-rw-r--r--   1 jon  jon         75310 2007-02-05 22:44 myworld.bzw
drwx------   3 jon  jon          4096 2007-01-14 20:29 .naimlog
drwxr-xr-x   3 jon  jon          4096 2007-01-08 02:17 .nautilus
drwxr-xr-x   2 jon  jon          4096 2007-02-20 21:24 .neverball
-rw-r--r--   1 jon  jon           904 2007-01-31 12:40 .nvidia-settings-rc
drwxr-xr-x   4 jon  jon          4096 2007-01-07 14:42 .nvu
drwxr-xr-x   3 jon  jon          4096 2007-02-05 14:44 .openarena
-rw-r--r--   1 jon  jon      80273216 2007-02-05 12:43 openarena_0.6.0-1getdeb1_i386.deb
drwx------   3 jon  jon          4096 2007-01-28 02:17 .openoffice.org2
drwxr-xr-x  13 jon  jon          4096 2007-02-22 10:09 .opera
drwxr-xr-x   2 jon  jon          4096 2007-02-14 01:24 .orbit
-rw-r--r--   1 jon  jon        109768 2007-02-20 20:54 palm.blend
-rw-r--r--   1 jon  jon        110504 2007-02-20 20:00 palm.blend1
-rw-r--r--   1 jon  jon         17271 2007-02-20 19:30 palmtree.jpg
drwx------   2 jon  jon          4096 2007-01-21 14:41 .pekwm
-rw-r--r--   1 jon  jon           151 2007-01-03 18:52 .penguin-command
drwxr-xr-x   3 jon  jon          4096 2007-02-19 13:21 photos
drwxr-xr-x   4 jon  jon          4096 2007-02-19 13:57 .picasa
-rw-r--r--   1 jon  jon        294347 2007-02-01 19:18 pictures
drwxr-xr-x   4 jon  jon          4096 2007-02-19 13:33 Pictures
drwxr-x---  10 jon  jon          4096 2007-02-10 23:34 .pingus
drwxr-xr-x   2 jon  jon          4096 2007-01-17 19:24 .planets
drwxr-xr-x   2 jon  jon          4096 2007-01-29 21:46 .ppracer
drwxr-xr-x   2 jon  jon          4096 2007-02-12 20:47 .qt
drwxr-xr-x   4 jon  jon          4096 2007-02-14 23:46 .quodlibet
-rw-r--r--   1 jon  jon         29702 2007-02-20 14:43 random.jpg
-rw-------   1 jon  jon         34493 2007-01-21 21:25 .realplayerrc
-rw-------   1 jon  jon         27782 2007-02-20 21:20 .recently-used
-rw-r--r--   1 jon  jon         93812 2007-02-22 09:56 .recently-used.xbel
-rw-r--r--   1 jon  jon         16761 2007-02-20 14:18 rocket.jpg
-rw-r--r--   1 jon  jon         20380 2007-02-14 19:18 roundcube.jpg
drwxrwx---   4 jon  jon          4096 2007-01-15 19:02 .sane
drwxr-xr-x   3 jon  jon          4096 2007-01-30 17:16 .scorched3d
-rw-r--r--   1 jon  jon       1440054 2007-02-14 01:23 screenshot.bmp
drwx------   2 jon  jon          4096 2007-02-14 01:14 .SearchAndRescue
drwx------   3 jon  jon          4096 2007-01-06 21:14 .secpanel
-rw-------   1 jon  jon            51 2007-01-07 23:21 .serverauth.5072
-rw-------   1 jon  jon            51 2007-01-29 17:13 .serverauth.5235
-rw-------   1 root root           51 2007-01-07 12:53 .serverauth.5453
drwxr-xr-x   2 jon  jon          4096 2007-02-09 02:20 .sheep
-rw-r--r--   1 jon  jon         52620 2007-02-22 09:46 size.zip
drwx------   3 jon  jon          4096 2007-02-07 17:26 .Skype
-rw-r--r--   1 jon  jon          1541 2007-01-22 14:26 .slimp3.pref
-rw-r--r--   1 jon  jon           359 2007-02-21 21:45 .slune
-rw-r--r--   1 jon  jon           121 2007-01-29 18:09 .soya_editor
drwx------   2 jon  jon          4096 2007-01-06 21:35 .ssh
drwxr-xr-x   3 jon  jon          4096 2007-01-13 21:17 .streamtuner
-rw-r--r--   1 jon  jon             0 2006-12-28 12:52 .sudo_as_admin_successful
-rw-r--r--   1 jon  jon          2608 2007-01-29 18:33 .tdfsb
-rw-r--r--   1 jon  jon         43407 2007-01-25 22:38 .temp
drwxr-xr-x   3 jon  jon          4096 2007-01-02 19:42 .themes
drwxr-xr-x   5 jon  jon          4096 2007-01-20 23:22 .thumbnails
drwx------   2 jon  games        4096 2007-01-26 14:15 .tlkgames
drwxr-xr-x   5 jon  jon          4096 2007-02-02 00:42 .torcs
drwxr-x---   3 jon  jon          4096 2007-02-18 21:32 .trackballs
drwx------   5 jon  jon          4096 2007-02-22 09:09 .Trash
drwxr-xr-x   3 jon  jon          4096 2007-02-02 09:46 .tremulous
-rw-r--r--   1 jon  jon      11547360 2007-02-22 10:06 TribalTroubleSetup.sh
drwx------   2 jon  jon          4096 2007-02-01 23:33 .trigger
-rw-r--r--   1 jon  jon          5174 2007-02-22 09:28 tris0.bmp
-rw-r--r--   1 jon  jon          1964 2007-02-22 09:28 tris.md2
-rw-r--r--   1 jon  jon           388 2007-02-08 14:45 tryout.plx
-rw-r--r--   1 jon  jon           389 2007-02-08 14:44 tryout.plx~
drwxr-xr-x   3 jon  jon          4096 2007-01-17 20:01 .tuxpaint
-rw-r--r--   1 jon  jon         19069 2007-02-21 20:46 um.....jpg
-rw-r--r--   1 jon  jon         14482 2007-02-20 16:41 unfinishedie.jpg
-rw-r--r--   1 jon  jon         14423 2007-02-22 09:37 Untitled
-rw-r--r--   1 jon  jon         94892 2007-02-07 17:07 untitled.bzw.blend
drwxr-xr-x   2 jon  jon          4096 2006-12-28 14:39 .update-manager
drwx------   2 jon  jon          4096 2007-01-01 19:13 .update-notifier
drwxr-xr-x   4 jon  jon          4096 2007-02-19 20:16 .uqm
drwxr-xr-t   8 jon  jon          4096 2007-02-06 10:21 .vegastrike.4.x
drwxr-xr-x   3 jon  jon          4096 2007-01-03 15:53 .vlc
drwx------   2 jon  jon          4096 2007-01-15 21:02 .w3m
drwxr-xr-x   2 jon  jon          4096 2007-01-23 22:21 website
-rw-r--r--   1 jon  jon        105967 2007-02-16 16:44 weirdmsksksksksksksksksksksskskskskskskskskskskskskskskskskskskskksksksks.png
-rw-r--r--   1 jon  jon         27920 2007-02-22 09:46 whirlwnd.zip
drwxr-xr-x   4 jon  jon          4096 2007-02-22 09:29 .wine
drwxr-xr-x   4 jon  jon          4096 2006-12-31 01:22 .wine-xbi6kF
drwxr-xr-x   2 jon  jon          4096 2007-01-23 01:38 .wmweather
drwxr-x---   2 jon  jon          4096 2007-02-01 15:51 .wormux
-rw-------   1 root root          100 2007-01-07 12:53 .Xauthority
-rw-------   2 jon  jon             0 2007-01-29 17:13 .Xauthority-c
-rw-------   2 jon  jon             0 2007-01-29 17:13 .Xauthority-l
drwxr-xr-x  20 jon  jon          4096 2007-02-19 22:07 .xfetrash
drwxr-xr-x   2 jon  jon          4096 2006-12-28 16:09 .xine
drwxr-xr-x   4 jon  jon          4096 2007-01-08 22:41 .xmms
drwx------   5 jon  jon          4096 2007-02-22 10:28 .xmoto
-rw-r--r--   1 jon  jon         17665 2007-02-18 21:01 .xscreensaver
-rw-r--r--   1 jon  jon           676 2007-02-22 11:00 .xsession-errors
-rw-r--r--   1 jon  jon          3437 2007-01-14 00:30 .xvidcaprc


(sorry about all th junk im going to have to make a "junk" folder again...)

---

### Post by Ben Sprinkle on 2007-02-22
Try:
```

sudo dpkg configure -a

```
Or
```

sudo dpkg -a

```
I havn't used this in so long so I don't even remember the command, something with -a and dpkg though.

---

### Post by MkfIbK7a on 2007-02-22
WOAH new development!

my HD now says it is read only!!!

what could have caused that and how can i fix it?

---

### Post by taurus on 2007-02-22
How come root owns /home/jon/.Xauthority?

```
sudo chown jon:jon /home/jon/.Xauthority
ls -la /home/jon/.config
```

---

### Post by MkfIbK7a on 2007-02-22
hrm strange it didnt ask for a password and this was a new terminal but anyhow heres the output...

> jon@albert:~$ sudo chown jon:jon /home/jon/.Xauthority
chown: changing ownership of `/home/jon/.Xauthority': Read-only file system
jon@albert:~$ ls -la /home/jon/.config
total 48
drwx------  10 jon jon 4096 2007-01-21 01:35 .
drwxr-xr-x 129 jon jon 8192 2007-02-22 10:59 ..
drwx------   2 jon jon 4096 2007-02-20 21:20 gtk-2.0
drwxr-xr-x   3 jon jon 4096 2007-01-15 20:52 menus
drwx------   2 jon jon 4096 2006-12-28 13:02 mousepad
drwxr-xr-x   3 jon jon 4096 2007-01-21 12:18 rox.sourceforge.net
drwx------   2 jon jon 4096 2007-01-26 14:51 Terminal
drwx------   2 jon jon 4096 2007-01-15 20:53 Thunar
drwxr-xr-x   9 jon jon 4096 2007-01-10 00:35 xfce4
drwx------   2 jon jon 4096 2007-01-14 15:11 xfce4-session
-rw-r--r--   1 jon jon  120 2007-01-09 16:06 xfce4-taskmanager.rc
jon@albert:~$ 



agghh nothing happened to the .Xauthority root is still the owner.

---

### Post by Ben Sprinkle on 2007-02-22
```

sudo chmod 777 /

```
Lol, too bad it doesn't do subfolders.

---

### Post by MkfIbK7a on 2007-02-22
ahh the problem is that it still thinks i have a read only file system!

---

### Post by Ben Sprinkle on 2007-02-22
Strange indeed, I'll leave taurus to this one. ;)

---

### Post by MkfIbK7a on 2007-02-22
hmm how on earth could my drive reformat itself???

---

### Post by taurus on 2007-02-22
> **Ben Sprinkle said:**
> ```

sudo chmod 777 /

```
Lol, too bad it doesn't do subfolders.

Please _**[COLOR="Red"]do not[/COLOR]**_ advice any user to run that command because doing so will break your system beyond repair, okay!

---

### Post by MkfIbK7a on 2007-02-22
> **taurus said:**
> Please _**[COLOR="Red"]do not[/COLOR]**_ advice any user to run that command because doing so will break your system beyond repair, okay!

lol

---

### Post by MkfIbK7a on 2007-02-22
anyone else?? i really need help...

anymore info i could give you to make this easier?

---

### Post by MkfIbK7a on 2007-02-22
ahh ok!!!

i fixed it with an 

fsck -y

simple eh?

---

### Post by MkfIbK7a on 2007-02-22
ok thx for your help all i ended up just digging out a new 40gig HD and reinstalling turns out my old one crashed....

---

### Post by Ben Sprinkle on 2007-02-23
> **taurus said:**
> Please _**[COLOR="Red"]do not[/COLOR]**_ advice any user to run that command because doing so will break your system beyond repair, okay!

It was a little joke, sorry bout that wert. :D

---

### Post by MkfIbK7a on 2007-02-25
'sok i knew what that command did i wouldnt have used it anyway but my 
fsck ended up deleting my home directory so i just reinstalled....

---

### Post by Ben Sprinkle on 2007-02-26
> **wert613 said:**
> 'sok i knew what that command did i wouldnt have used it anyway but my 
fsck ended up deleting my home directory so i just reinstalled....

Roflcopter. /me looks around nervously.

---

### Post by bodhi.zazen on 2007-02-26
> **wert613 said:**
> ahh the problem is that it still thinks i have a read only file system!

General comment:

Changing permissions of system files, if you do not know what you are doing, is not a good idea.

chmod 777 / in particular is not so hot :(

wert613 : In terms of your read only problem, you file system may be corrupt ...

Boot to the ubuntu (desktop) live CD

Open a terminal and enter :

```
fsck -rfv /dev/hdxy
```

Where hdxy is your ubutu root partition.

If you do not know what this is, enter ```
sudo fdisk -l
```In a terminal ...

HTH :)

---

### Post by MkfIbK7a on 2007-02-26
The problem turned out to be Some burned out inodes, I have replaced the harddrive and all is well.

---

