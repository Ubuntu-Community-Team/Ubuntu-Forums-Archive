---
title: "desktop copy"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by theRightNee on 2008-02-23
whenever i move something on the desktop (organizing icons, lining them up, making smiley faces, etc.) the file gets copied. I just want to move the file, not copy it. I recently had an issue with permissions with the desktop, so I went in to root and changed the desktop to give me full control. Is this the reason? If so, how do i go about fixing this?

---

### Post by taurus on 2008-02-23
You should be the owner of your $HOME and that would include Desktop directory too.  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~
```

---

### Post by theRightNee on 2008-02-23
```

total 4324
drwxrwxr-x  57 james james    4096 2008-02-23 10:44 .
drwxr-xr-x   6 root  root     4096 2008-02-22 19:41 ..
drwx------   3 james james    4096 2008-02-12 21:14 .adobe
-rw-------   1 root  root     3352 2008-02-22 19:36 .bash_history
-rw-r--r--   1 james james     220 2008-02-11 20:19 .bash_logout
-rw-r--r--   1 james james    2298 2008-02-11 20:19 .bashrc
drwxr-xr-x   3 james james    4096 2008-02-11 20:52 .cache
drwx------   2 james james    4096 2008-02-12 06:30 .chewing
drwxr-xr-x   7 james james    4096 2008-02-14 22:24 .config
[COLOR="Red"]drwxrwxr-x   2 root  james    4096 2008-02-23 10:27 Desktop[/COLOR]
-rw-------   1 james james      28 2008-02-22 22:43 .dmrc
drwxr-xr-x   8 james james    4096 2008-02-14 22:13 Documents
drwxr-xr-x   2 james james    4096 2008-02-12 05:10 dwhelper
drwxr-xr-x   4 james james    4096 2008-02-16 18:43 .emerald
-rw-------   1 james james      16 2008-02-11 20:52 .esd_auth
drwxr-xr-x   3 james james    4096 2008-02-12 21:03 .evolution
lrwxrwxrwx   1 james james      26 2008-02-11 20:19 Examples -> /usr/share/example-content
drwxr-xr-x  11 root  root     4096 2008-02-12 22:37 ffmpeg-0.cvs20070307
-rw-r--r--   1 root  root    37885 2007-06-03 13:03 ffmpeg_0.cvs20070307-5ubuntu4.diff.gz
-rw-r--r--   1 root  root     1233 2007-06-03 13:03 ffmpeg_0.cvs20070307-5ubuntu4.dsc
-rw-r--r--   1 root  root  2593100 2007-04-29 14:03 ffmpeg_0.cvs20070307.orig.tar.gz
-rw-r--r--   1 james james 1232683 2008-02-13 04:06 Firefox_wallpaper.png
drwxr-xr-x   2 james james    4096 2008-02-16 21:26 .fontconfig
drwxr-xr-x   3 james james    4096 2008-02-14 22:31 .fullcircle
drwx------   5 james james    4096 2008-02-22 22:44 .gconf
drwx------   2 james james    4096 2008-02-23 10:27 .gconfd
drwx------   2 james james    4096 2008-02-17 23:27 .ggz
drwxr-xr-x  22 james james    4096 2008-02-19 20:20 .gimp-2.4
-rw-r-----   1 james james       0 2008-02-23 10:22 .gksu.lock
drwxr-xr-x   5 james james    4096 2008-02-12 21:32 .gnome
drwx------  14 james james    4096 2008-02-22 21:34 .gnome2
drwx------   2 james james    4096 2008-02-11 20:52 .gnome2_private
drwx------   3 james james    4096 2008-02-19 19:21 .gnome-color-chooser
drwx------   2 james james    4096 2008-02-12 21:32 .gnome_private
drwx------   2 root  root     4096 2008-02-11 22:18 .gnupg
drwxr-xr-x   2 james james    4096 2008-02-12 19:06 .gstreamer-0.10
-rw-r--r--   1 james james     108 2008-02-22 22:43 .gtk-bookmarks
-rw-r--r--   1 james james     156 2008-02-18 20:41 .gtkrc-1.2-gnome2
-rw-r--r--   1 james james       1 2008-02-19 19:34 .gtkrc-2.0
-rw-r--r--   1 james james      42 2008-02-19 19:33 .gtkrc-2.0~
-rw-------   1 james james    1388 2008-02-22 22:43 .ICEauthority
drwxr-xr-x   3 james james    4096 2008-02-12 21:09 .icons
drwx------   3 james james    4096 2008-02-12 22:15 .kde
drwx------   2 james james    4096 2008-02-17 16:00 .kino-history
-rw-r--r--   1 james james    2968 2008-02-17 23:11 .kinorc
drwxr-xr-x   3 james james    4096 2008-02-11 20:52 .local
drwx------   3 james james    4096 2008-02-12 21:14 .macromedia
drwx------   3 james james    4096 2008-02-11 20:52 .metacity
drwx------   4 james james    4096 2008-02-12 21:14 .mozilla
drwx------   3 root  root     4096 2008-02-11 22:16 .mozilla_backup_2008-02-11T22:16:17-0800
drwx------   2 james james    4096 2008-02-12 20:07 .mplayer
drwxr-xr-x 144 james james    4096 2008-02-21 20:47 Music
drwxr-xr-x   3 james james    4096 2008-02-22 21:34 .nautilus
-rw-r--r--   1 james james  192512 2008-02-18 23:06 nautilus-debug-log.txt
drwx------   3 james james    4096 2008-02-17 17:16 .openoffice.org2
drwxr-xr-x   2 james james    4096 2008-02-19 19:30 Pictures
-rw-r--r--   1 james james     566 2008-02-11 20:19 .profile
drwxr-xr-x   2 james james    4096 2008-02-11 20:52 Public
-rw-------   1 james james     256 2008-02-18 18:40 .pulse-cookie
drwx------   5 james james    4096 2008-02-12 21:02 .purple
drwxr-xr-x   2 james james    4096 2008-02-12 22:15 .qt
-rw-------   1 james james     575 2008-02-17 17:16 .recently-used
-rw-r--r--   1 james james   34278 2008-02-23 10:44 .recently-used.xbel
-rw-------   1 root  root     1024 2008-02-18 14:06 .rnd
drwx------   4 james james    4096 2008-02-12 06:30 .scim
-rw-r--r--   1 james james       0 2008-02-11 20:55 .sudo_as_admin_successful
drwxr-xr-x   2 james james    4096 2008-02-12 22:43 Templates
drwxr-xr-x  13 james james    4096 2008-02-18 20:34 .themes
drwx------   4 james james    4096 2008-02-11 21:18 .thumbnails
drwxr-xr-x   5 james james    4096 2008-02-22 20:23 .transmission
drwx------   4 james james    4096 2008-02-23 10:27 .Trash
drwxr-xr-x   2 james james    4096 2008-02-11 21:50 .update-manager-core
drwx------   2 james james    4096 2008-02-11 22:16 .update-notifier
drwxr-xr-x   2 james james    4096 2008-02-22 20:07 Videos
drwxr-xr-x   3 james james    4096 2008-02-12 22:12 .vlc
drwxr-xr-x   2 james james    4096 2008-02-18 20:14 vmware
drwxr-xr-x   2 james james    4096 2008-02-18 20:17 .vmware
drwx------   2 root  root     4096 2008-02-11 22:14 .w3m
drwxr-xr-x   2 james james    4096 2008-02-18 19:57 Windows 2000 Professional
drwxr-xr-x   4 james james    4096 2008-02-22 06:39 .wine
drwxr-xr-x   2 james james    4096 2008-02-12 22:42 .winff
-rw-------   1 james james     124 2008-02-22 22:43 .Xauthority
-rw-r--r--   1 james james    9611 2008-02-23 10:44 .xsession-errors

```
[COLOR="Black"]looks like its ok[/COLOR]

---

### Post by taurus on 2008-02-23
I don't know why root owns some of the files/directories in your $HOME!  Try not to use sudo/gksudo if you don't have to.

Now, reset the ownership again with

```
sudo chown -R james:james /home/james
ls -la ~
```

---

### Post by theRightNee on 2008-02-23
thank you so much!!! ( i believe it is the result of some nasty experimentation with Time Vault)

---

