---
title: "[SOLVED] Another Synaptic error message"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by ozzyprv on 2008-02-29
Every time I use Synaptic I get this error at the end of the installation:

> E: kdelibs-data: subprocess post-installation script returned error exit status 139
E: kdelibs4c2a: dependency problems - leaving unconfigured
E: libkonq4: dependency problems - leaving unconfigured
E: kdebase-bin: dependency problems - leaving unconfigured
E: kdesktop: dependency problems - leaving unconfigured
E: kdebase-kio-plugins: dependency problems - leaving unconfigured
E: amarok: dependency problems - leaving unconfigured
E: amarok-xine: dependency problems - leaving unconfigured
E: desktop-effects: subprocess post-installation script returned error exit status 139
E: kamera: dependency problems - leaving unconfigured
E: libkcddb1: dependency problems - leaving unconfigured
E: kdemultimedia-kio-plugins: dependency problems - leaving unconfigured
E: gtkpod: subprocess post-installation script returned error exit status 139




It is unrelated to whatever I am installing.

Thanks.

---

### Post by northern lights on 2008-02-29
You seem to have dependency issues / broken packages.

Have you run ```
sudo dpkg --configure -a
```already? Alternatively, have you open Synaptic and under "Edit" tried to fix broken packages?

If nothing helps, you could try to move your current gtkpod & kdelibs-data as a backup: ```
sudo mv /var/lib/dpkg/info/kdelibs-data.* /tmp/
sudo mv /var/lib/dpkg/info/gtkpod.* /tmp/
```
and thereupon running an update, purging those two packages & reinstalling: ```
sudo apt-get update
sudo apt-get --purge remove kdelibs-data gtkpod
sudo apt-get install kdelibs-data gtkpod
```

---

### Post by ozzyprv on 2008-02-29
hmmm, did not work

This is the detail of the error I keep getting.

> 
me@MyUbuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-cups-manager
Use 'apt-get autoremove' to remove them.
Suggested packages:
  msttcorefonts
The following packages will be REMOVED:
  kamera kdebase-bin kdebase-kio-plugins kdemultimedia-kio-plugins libkcddb1
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 5 to remove and 3 not upgraded.
17 not fully installed or removed.
Need to get 0B/9951kB of archives.
After unpacking, 40.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 108671 files and directories currently installed.)
Removing kamera ...

(update-desktop-database:12652): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kamera (--remove):
 subprocess post-removal script returned error exit status 139
Removing kdebase-bin ...

(update-desktop-database:12669): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kdebase-bin (--remove):
 subprocess post-removal script returned error exit status 139
Removing kdebase-kio-plugins ...

(update-desktop-database:12683): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kdebase-kio-plugins (--remove):
 subprocess post-removal script returned error exit status 139
Removing kdemultimedia-kio-plugins ...

(update-desktop-database:12688): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kdemultimedia-kio-plugins (--remove):
 subprocess post-removal script returned error exit status 139
Removing libkcddb1 ...

(update-desktop-database:12693): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing libkcddb1 (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 kamera
 kdebase-bin
 kdebase-kio-plugins
 kdemultimedia-kio-plugins
 libkcddb1
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by ozzyprv on 2008-02-29
Anybody? Please.
I have spent hours searching for a fix...nothing.

Now I am unable to install/uninstall anything.

Thanks.

---

### Post by ozzyprv on 2008-03-02
Keep getting the errors but got around few new installs by renaming some scripts (post-removal) that are failing.

Synaptic error
> E: pidgin: subprocess post-removal script returned error exit status 139

W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_feisty-updates_main_binary-amd64_Packages)

Error from console
> me@My:~$ sudo apt-get install minicom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  lrzsz
The following packages will be REMOVED:
  pidgin
The following NEW packages will be installed:
  minicom
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
11 not fully installed or removed.
Need to get 0B/179kB of archives.
After unpacking, 624kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 109145 files and directories currently installed.)
Removing pidgin ...

(update-desktop-database:6538): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing pidgin (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 pidgin
E: Sub-process /usr/bin/dpkg returned an error code (1)


Not sure why the these scripts keep failing.

Please help.

---

### Post by Partyboi2 on 2008-03-03
have a look at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/desktop-file-utils/+bug/59392")

---

### Post by ozzyprv on 2008-03-04
> **Partyboi2 said:**
> have a look at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/desktop-file-utils/+bug/59392")

Thank you Partyboi2, I carefully read the bug post and I solved the problem

Cause: An empty place holder created to have the nvidia setting launcher (that never worked).
The empty file was NVIDIA-Settings.desktop
I removed the file and the problem is gone.

According to the bug  post the issue was fixed for Hardy.

Oz.

---

