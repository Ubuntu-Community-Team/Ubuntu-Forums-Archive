---
title: "[SOLVED] cd command not working in Terminal"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by kujaabi on 2008-02-15
This is what I get when I type in the change directory command even though the directory exists and I can see it and open it with the mouse. Other commands seem to be working fine:

ggero@rscott-desktop:~$ cd directory
bash: cd: directory: No such file or directory
ggero@rscott-desktop:~$ 

:confused:

---

### Post by Dr Small on 2008-02-15
Post the output of:
```
ls -la
```

---

### Post by kujaabi on 2008-02-15
ggero@rscott-desktop:~$ ls -la
total 23072
drwxr-xr-x 48 ggero ggero     4096 2008-02-15 12:07 .
drwxr-xr-x  4 root  root      4096 2008-02-07 08:17 ..
-rw-r--r--  1 root  root         0 2008-02-15 08:46 1
drwxr-xr-x  2 ggero root      4096 2008-02-15 08:49 .automatix
-rw-------  1 ggero ggero      128 2008-02-15 12:33 .bash_history
-rw-r--r--  1 ggero ggero      220 2008-01-07 08:13 .bash_logout
-rw-r--r--  1 ggero ggero     2298 2008-01-07 08:13 .bashrc
drwxr-xr-x  8 ggero ggero     4096 2008-02-07 08:40 .bibledit
drwxr-xr-x  4 ggero ggero     4096 2008-02-15 08:03 .bibledit_temp
drwxr-xr-x  3 ggero ggero     4096 2008-01-07 08:50 .cache
drwxr-xr-x  5 ggero ggero     4096 2008-02-07 08:25 .config
drwx------  3 ggero ggero     4096 2008-02-07 08:26 .dbus
drwxr-xr-x  7 ggero ggero     4096 2008-02-15 12:34 Desktop
-rw-------  1 ggero ggero       28 2008-02-15 12:07 .dmrc
drwxr-xr-x  2 ggero ggero     4096 2008-01-07 08:50 Documents
-rw-------  1 ggero ggero       16 2008-01-07 08:51 .esd_auth
drwxr-xr-x  8 ggero ggero     4096 2008-02-15 12:02 .evolution
lrwxrwxrwx  1 ggero ggero       26 2008-01-07 08:13 Examples -> /usr/share/example-content
drwx------  2 ggero ggero     4096 2008-01-23 11:18 .filezilla
drwxr-xr-x  2 ggero ggero     4096 2008-02-13 11:04 .fontconfig
drwx------  5 ggero ggero     4096 2008-02-15 12:07 .gconf
drwx------  2 ggero ggero     4096 2008-02-15 12:34 .gconfd
drwxr-xr-x 22 ggero ggero     4096 2008-02-14 08:46 .gimp-2.4
-rw-r-----  1 ggero ggero        0 2008-02-15 11:28 .gksu.lock
drwxr-xr-x  4 ggero ggero     4096 2008-02-15 08:47 .gnome
drwx------ 13 ggero ggero     4096 2008-02-15 12:02 .gnome2
drwx------  2 ggero ggero     4096 2008-02-04 11:20 .gnome2_private
lrwxrwxrwx  1 ggero ggero       37 2008-02-15 08:46 googleearth -> /home/ggero/google-earth//googleearth
drwxr-xr-x  9 ggero ggero     4096 2008-02-15 08:47 google-earth
-rwxr-xr-x  1 ggero ggero 23048189 2008-02-12 23:35 GoogleEarthLinux.bin
drwxr-xr-x  2 ggero ggero     4096 2008-01-23 11:09 .gstreamer-0.10
-rw-r--r--  1 ggero ggero      261 2008-02-15 12:07 .gtk-bookmarks
-rw-r--r--  1 ggero ggero    25509 2008-02-12 09:39 .gtk_qt_engine_rc
-rw-r--r--  1 ggero ggero      136 2008-02-13 11:11 .gtkrc-1.2-gnome2
-rw-r--r--  1 ggero ggero      285 2008-02-07 08:25 .gtkrc-2.0-kde
drwxr-----  2 ggero ggero     4096 2008-02-04 10:59 .hplip
-rw-------  1 ggero ggero      382 2008-02-15 12:07 .ICEauthority
drwxr-xr-x  8 ggero ggero     4096 2008-02-13 11:08 .icons
drwxr-xr-x  3 ggero ggero     4096 2008-02-11 11:14 .java
drwx------  5 ggero ggero     4096 2008-02-07 08:25 .kde
drwxr-xr-x  3 ggero ggero     4096 2008-01-07 08:50 .local
drwx------  3 ggero ggero     4096 2008-02-15 08:47 .loki
drwxr-xr-x  3 ggero ggero     4096 2008-02-07 08:25 .mcop
-rw-------  1 ggero ggero       31 2008-02-15 11:34 .mcoprc
drwx------  3 ggero ggero     4096 2008-01-07 08:50 .metacity
drwx------  3 ggero ggero     4096 2008-01-09 10:37 .mozilla
drwxr-xr-x  2 ggero ggero     4096 2008-01-07 08:50 Music
drwxr-xr-x  3 ggero ggero     4096 2008-02-15 12:02 .nautilus
-rw-r--r--  1 ggero ggero   241664 2008-02-15 12:02 nautilus-debug-log.txt
drwx------  3 ggero ggero     4096 2008-02-12 09:43 .openoffice.org2
drwxr-xr-x  2 ggero ggero     4096 2008-01-07 08:50 Pictures
-rw-r--r--  1 ggero ggero      566 2008-01-07 08:13 .profile
drwxr-xr-x  2 ggero ggero     4096 2008-01-07 08:50 Public
drwxr-xr-x  2 ggero ggero     4096 2008-02-14 09:02 .qt
-rw-------  1 ggero ggero     1046 2008-01-28 10:28 .recently-used
-rw-r--r--  1 ggero ggero    15327 2008-02-15 12:02 .recently-used.xbel
drwx------  4 ggero ggero     4096 2008-01-28 10:29 .screem
drwx------  2 ggero ggero     4096 2008-01-28 10:41 .sitecopy
-rw-r--r--  1 ggero ggero        0 2008-01-09 11:04 .sudo_as_admin_successful
drwxr-xr-x  2 ggero ggero     4096 2008-01-07 08:50 Templates
drwxr-xr-x  4 ggero ggero     4096 2008-02-13 11:09 .themes
drwx------  4 ggero ggero     4096 2008-01-28 10:37 .thumbnails
drwx------  9 ggero ggero     4096 2008-02-15 11:36 .Trash
drwxr-xr-x  2 ggero ggero     4096 2008-01-09 10:53 .update-manager-core
drwx------  2 ggero ggero     4096 2008-01-09 11:00 .update-notifier
drwxr-xr-x  2 ggero ggero     4096 2008-01-07 08:50 Videos
drwx------  2 ggero ggero     4096 2008-01-25 08:32 .w3m
drwxr-xr-x  2 ggero ggero     4096 2008-01-28 08:39 .wapi
drwxr-xr-x  4 ggero ggero     4096 2008-02-15 11:32 .wine
-rw-------  1 ggero ggero      125 2008-02-15 12:07 .Xauthority
-rw-r--r--  1 ggero ggero     4553 2008-02-15 12:07 .xsession-errors
ggero@rscott-desktop:~$

---

### Post by Dr Small on 2008-02-15
Ok. Just as I thought. "directory" doesn't exist.
Where is "directory" at? Perhaps on your desktop?

Dr Small

---

### Post by kujaabi on 2008-02-15
yes on desktop

---

### Post by taurus on 2008-02-15
Try something like

```
cd ~/Desktop
cd directory
```
Otherwise, post

```
ls -la ~/Desktop
```

---

### Post by HermanAB on 2008-02-15
cd ~/Desktop/directory

The '~' means your home directory - a general Unix shortcut.

If your home directory is /home/joesoap then you can also write it out in full:
cd /home/joesoap/Desktop/directory

Cheers,

Herman

---

### Post by kujaabi on 2008-02-15
ggero@rscott-desktop:~$ cd ~/Desktop
ggero@rscott-desktop:~/Desktop$ cd directory
bash: cd: directory: No such file or directory
ggero@rscott-desktop:~/Desktop$ 
ggero@rscott-desktop:~/Desktop$ ls -la ~/Desktop
total 3184
drwxr-xr-x  7 ggero ggero    4096 2008-02-15 13:19 .
drwxr-xr-x 48 ggero ggero    4096 2008-02-15 13:19 ..
drwxr-xr-x  2 ggero ggero    4096 2008-02-14 08:54 Appearance
-rw-r--r--  1 ggero ggero    1883 2008-02-07 08:25 .directory
drwxr-xr-x  2 ggero ggero    4096 2008-02-15 11:48 Directory
drwxr-xr-x  2 ggero ggero    4096 2007-11-20 18:24 flashplayer-installer
drwxr-xr-x  3 ggero ggero    4096 2008-02-15 09:19 Glenn Gero on Levi
-rw-------  1 ggero ggero     430 2008-02-15 08:47 Google-googleearth.desktop
drwxr-xr-x  2 ggero ggero    4096 2007-11-20 18:24 install_flash_player_9_linux
-rw-r--r--  1 ggero ggero 3036127 2008-02-15 11:27 install_flash_player_9_linux.tar.gz
-rw-r--r--  1 ggero ggero  174066 2008-02-08 08:42 Windows-Linux program comparisions
ggero@rscott-desktop:~/Desktop$

---

### Post by taurus on 2008-02-15
Unix/Linux is CaSe SenSiTive so directory is _not_ the same as Directory.

```
cd Directory
```

---

### Post by Usta_AsH on 2008-02-15
> **kujaabi said:**
> ggero@rscott-desktop:~$ cd ~/Desktop
ggero@rscott-desktop:~/Desktop$ cd directory
bash: cd: directory: No such file or directory
ggero@rscott-desktop:~/Desktop$ 
ggero@rscott-desktop:~/Desktop$ ls -la ~/Desktop
total 3184
drwxr-xr-x  7 ggero ggero    4096 2008-02-15 13:19 .
drwxr-xr-x 48 ggero ggero    4096 2008-02-15 13:19 ..
drwxr-xr-x  2 ggero ggero    4096 2008-02-14 08:54 Appearance
-rw-r--r--  1 ggero ggero    1883 2008-02-07 08:25 .directory
drwxr-xr-x  2 ggero ggero    4096 2008-02-15 11:48 Directory
drwxr-xr-x  2 ggero ggero    4096 2007-11-20 18:24 flashplayer-installer
drwxr-xr-x  3 ggero ggero    4096 2008-02-15 09:19 Glenn Gero on Levi
-rw-------  1 ggero ggero     430 2008-02-15 08:47 Google-googleearth.desktop
drwxr-xr-x  2 ggero ggero    4096 2007-11-20 18:24 install_flash_player_9_linux
-rw-r--r--  1 ggero ggero 3036127 2008-02-15 11:27 install_flash_player_9_linux.tar.gz
-rw-r--r--  1 ggero ggero  174066 2008-02-08 08:42 Windows-Linux program comparisions
ggero@rscott-desktop:~/Desktop$

when you are in desktop

cd Directory

"d" letter should be big.

---

### Post by kujaabi on 2008-02-15
That's it. Sorry :oops:  Thanks very much

---

### Post by kujaabi on 2008-02-15
What does the ~/Desktop mean?

---

### Post by taurus on 2008-02-15
> **kujaabi said:**
> What does the ~/Desktop mean?

~ means your $HOME directory, /home/ggero.  So, ~/Desktop means Desktop directory under your $HOME, /home/ggero/Desktop.

But if you are in your $HOME, then you don't have to put ~ in front.  You can also do

```
cd Desktop
```

---

### Post by oldos2er on 2008-02-15
> **kujaabi said:**
> What does the ~/Desktop mean?

 It's showing you that the current directory is Desktop. The ~ is shorthand for "/home/username".

---

