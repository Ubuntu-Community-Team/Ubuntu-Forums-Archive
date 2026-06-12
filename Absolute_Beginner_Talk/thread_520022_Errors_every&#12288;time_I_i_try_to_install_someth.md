---
title: "Errors every&#12288;time I i try to install something"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by saxonthebeach908 on 2007-08-07
Every time I try to install something I get these errors:
```
E: desktop-effects: subprocess post-installation script returned error exit status 139
E: kate: subprocess post-installation script returned error exit status 139
E: kicker: subprocess post-installation script returned error exit status 139
E: kcontrol: dependency problems - leaving unconfigured
E: kdeprint: subprocess post-installation script returned error exit status 139
E: kfind: subprocess post-installation script returned error exit status 139
E: khelpcenter: subprocess post-installation script returned error exit status 139
E: klipper: subprocess post-installation script returned error exit status 139
E: kmenuedit: subprocess post-installation script returned error exit status 139
E: konqueror: dependency problems - leaving unconfigured
E: konqueror-nsplugins: subprocess post-installation script returned error exit status 139
E: konsole: subprocess post-installation script returned error exit status 139
E: ksplash: subprocess post-installation script returned error exit status 139
E: ksysguard: subprocess post-installation script returned error exit status 139
E: kwin: subprocess post-installation script returned error exit status 139
E: rhythmbox: subprocess post-installation script returned error exit status 139

```

And I get something similar when I try it in the terminal. I don't know why all the kde packages are there, but I do know I tried to uninstall rhythmbox and it didn't complete. I'm sure there's something simple I'm missing, but I need help- this is making it so I can't install some packages!

---

### Post by FakeOutdoorsman on 2007-08-07
This may be of help:
[HOWTO fix problems regarding broken dependencies]("http://ubuntuforums.org/showthread.php?t=186672")

---

### Post by saxonthebeach908 on 2007-08-08
Tried everything in that guide- thought I had all those packages removed, but they keep coming back...this is really frustrating

---

### Post by saxonthebeach908 on 2007-08-08
For reference, this is exactly what my terminal looks like after I do anything like sudo apt-get install or dpkg --configure -a, etc:
```
Setting up desktop-effects (0.7.1-0ubuntu4) ...

(update-desktop-database:10993): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing desktop-effects (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-btdownload (0.0.28-1~feisty1) ...

(update-desktop-database:11004): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-btdownload (--configure):
 subprocess post-installation script returned error exit status 139
Setting up hal-device-manager (0.5.9-1ubuntu2~feisty1) ...

(update-desktop-database:11009): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing hal-device-manager (--configure):
 subprocess post-installation script returned error exit status 139
Setting up kate (3.5.6-0ubuntu20.1) ...

(update-desktop-database:11026): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kate (--configure):
 subprocess post-installation script returned error exit status 139
Setting up kicker (3.5.6-0ubuntu20.1) ...

(update-desktop-database:11053): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kicker (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of kcontrol:
 kcontrol depends on kicker (>= 4:3.5.5-1); however:
  Package kicker is not configured yet.
dpkg: error processing kcontrol (--configure):
 dependency problems - leaving unconfigured
Setting up kdeprint (3.5.6-0ubuntu20.1) ...

(update-desktop-database:11068): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
dSegmentation fault (core dumped)
dpkg: error processing kdeprint (--configure):
 subprocess post-installation script returned error exit status 139
Setting up kfind (3.5.6-0ubuntu20.1) ...

(update-desktop-database:11083): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kfind (--configure):
 subprocess post-installation script returned error exit status 139
Setting up khelpcenter (3.5.6-0ubuntu20.1) ...

(update-desktop-database:11100): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing khelpcenter (--configure):
 subprocess post-installation script returned error exit status 139
Setting up klipper (3.5.6-0ubuntu20.1) ...

(update-desktop-database:11115): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing klipper (--configure):
 subprocess post-installation script returned error exit status 139
Setting up kmenuedit (3.5.6-0ubuntu20.1) ...

(update-desktop-database:11130): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kmenuedit (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of konqueror:
 konqueror depends on kcontrol (= 4:3.5.6-0ubuntu20.1); however:
  Package kcontrol is not configured yet.
 konqueror depends on kfind (= 4:3.5.6-0ubuntu20.1); however:
  Package kfind is not configured yet.
dpkg: error processing konqueror (--configure):
 dependency problems - leaving unconfigured
Setting up konqueror-nsplugins (3.5.6-0ubuntu20.1) ...

(update-desktop-database:11135): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing konqueror-nsplugins (--configure):
 subprocess post-installation script returned error exit status 139
Setting up konsole (3.5.6-0ubuntu20.1) ...

(update-desktop-database:11152): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing konsole (--configure):
 subprocess post-installation script returned error exit status 139
Setting up ksplash (3.5.6-0ubuntu20.1) ...

(update-desktop-database:11166): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing ksplash (--configure):
 subprocess post-installation script returned error exit status 139
Setting up ksysguard (3.5.6-0ubuntu20.1) ...

(update-desktop-database:11195): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing ksysguard (--configure):
 subprocess post-installation script returned error exit status 139
Setting up kwin (3.5.6-0ubuntu20.1) ...

(update-desktop-database:11225): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kwin (--configure):
 subprocess post-installation script returned error exit status 139
Setting up rhythmbox (0.10.0-0ubuntu2) ...

(update-desktop-database:11247): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing rhythmbox (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 desktop-effects
 gnome-btdownload
 hal-device-manager
 kate
 kicker
 kcontrol
 kdeprint
 kfind
 khelpcenter
 klipper
 kmenuedit
 konqueror
 konqueror-nsplugins
 konsole
 ksplash
 ksysguard
 kwin
 rhythmbox
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

