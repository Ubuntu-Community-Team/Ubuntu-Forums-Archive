---
title: "dpkg troubles"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by billybag on 2006-12-13
i am having some troubles upgrading, autoremoving, and --configure -a[ing]. in terminal, this is the constant error i am getting:

The following packages will be REMOVED:
  libconfuse0 libifp4 libmjpegtools0c2a libmozjs0d libnjb5 libnspr4-0d
  libnss3-0d libquicktime0 libwv-1.2-1 libxfce4mcs-client3
  libxfce4mcs-manager3
The following packages will be upgraded:
  automatix2 linux-headers-2.6.17-10 linux-headers-2.6.17-10-386
  linux-headers-2.6.17-10-generic linux-image-2.6.17-10-386 linux-libc-dev
  qobex
7 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
78 not fully installed or removed.
Need to get 0B/34.2MB of archives.
After unpacking 4157kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 223832 files and directories currently installed.)
Removing libconfuse0 ...
Bus error (core dumped)
dpkg: error processing libconfuse0 (--remove):
 subprocess post-removal script returned error exit status 135
Removing libifp4 ...
Bus error (core dumped)
dpkg: error processing libifp4 (--remove):
 subprocess post-removal script returned error exit status 135
Removing libmjpegtools0c2a ...
Bus error (core dumped)
dpkg: error processing libmjpegtools0c2a (--remove):
 subprocess post-removal script returned error exit status 135
Removing libmozjs0d ...
Bus error (core dumped)
dpkg: error processing libmozjs0d (--remove):
 subprocess post-removal script returned error exit status 135
Removing libnjb5 ...
Bus error (core dumped)
dpkg: error processing libnjb5 (--remove):
 subprocess post-removal script returned error exit status 135
Removing libnss3-0d ...
Bus error (core dumped)
dpkg: error processing libnss3-0d (--remove):
 subprocess post-removal script returned error exit status 135
Removing libnspr4-0d ...
Bus error (core dumped)
dpkg: error processing libnspr4-0d (--remove):
 subprocess post-removal script returned error exit status 135
Removing libquicktime0 ...
Bus error (core dumped)
dpkg: error processing libquicktime0 (--remove):
 subprocess post-removal script returned error exit status 135
Removing libwv-1.2-1 ...
Bus error (core dumped)
dpkg: error processing libwv-1.2-1 (--remove):
 subprocess post-removal script returned error exit status 135
Removing libxfce4mcs-client3 ...
Bus error (core dumped)
dpkg: error processing libxfce4mcs-client3 (--remove):
 subprocess post-removal script returned error exit status 135
Removing libxfce4mcs-manager3 ...
Bus error (core dumped)
dpkg: error processing libxfce4mcs-manager3 (--remove):
 subprocess post-removal script returned error exit status 135
Errors were encountered while processing:
 libconfuse0
 libifp4
 libmjpegtools0c2a
 libmozjs0d
 libnjb5
 libnss3-0d
 libnspr4-0d
 libquicktime0
 libwv-1.2-1
 libxfce4mcs-client3
 libxfce4mcs-manager3
E: Sub-process /usr/bin/dpkg returned an error code (1)

and in synaptic:

E: libgtkmm-2.4-1c2a: subprocess post-installation script returned error exit status 135
E: agave: dependency problems - leaving unconfigured
E: libtdb1: subprocess post-installation script returned error exit status 135
E: apt-index-watcher: dependency problems - leaving unconfigured
E: debtags: dependency problems - leaving unconfigured
E: libggz2: subprocess post-installation script returned error exit status 135
E: libggzcore7: dependency problems - leaving unconfigured
E: libggzmod4: dependency problems - leaving unconfigured
E: ggzcore-bin: dependency problems - leaving unconfigured
E: ggz-kde-games: dependency problems - leaving unconfigured
E: ggz-kde-games-data: dependency problems - leaving unconfigured
E: xaw3dg: subprocess post-installation script returned error exit status 135
E: gv: dependency problems - leaving unconfigured
E: libboost-thread1.33.1: subprocess post-installation script returned error exit status 135
E: libpano12-0: subprocess post-installation script returned error exit status 135
E: libwxgtk2.6-0: subprocess post-installation script returned error exit status 135
E: hugin: dependency problems - leaving unconfigured
E: libflac++5c2: subprocess post-installation script returned error exit status 135
E: liblrdf0: subprocess post-installation script returned error exit status 135
E: hydrogen: dependency problems - leaving unconfigured
E: librsync1: subprocess post-installation script returned error exit status 135
E: rdiff-backup: dependency problems - leaving unconfigured
E: keep: dependency problems - leaving unconfigured
E: koffice-libs: subprocess post-installation script returned error exit status 135
E: krita: dependency problems - leaving unconfigured
E: ladcca2: subprocess post-installation script returned error exit status 135
E: lesstif2: subprocess post-installation script returned error exit status 135
E: liballegro4.2: subprocess post-installation script returned error exit status 135
E: libgwenhywfar38: subprocess post-installation script returned error exit status 135
E: libaqbanking-plugins-libgwenhywfar38: dependency problems - leaving unconfigured
E: libktoblzcheck1c2a: subprocess post-installation script returned error exit status 135
E: libchipcard2-0c2: dependency problems - leaving unconfigured
E: libaqgeldkarte4: dependency problems - leaving unconfigured
E: libaqhbci10: dependency problems - leaving unconfigured
E: libqbanking4: dependency problems - leaving unconfigured
E: libaqbanking16: dependency problems - leaving unconfigured
E: libaqdtaus3: dependency problems - leaving unconfigured
E: libconfuse0: subprocess post-installation script returned error exit status 135
E: libfltk1.1: subprocess post-installation script returned error exit status 135
E: libfluidsynth1: dependency problems - leaving unconfigured
E: libglademm-2.4-1c2a: dependency problems - leaving unconfigured
E: libgnomecanvasmm-2.6-1c2a: dependency problems - leaving unconfigured
E: libgnomemm-2.6-1c2a: dependency problems - leaving unconfigured
E: libgnomeuimm-2.6-1c2a: dependency problems - leaving unconfigured
E: liblockdev1: subprocess post-installation script returned error exit status 135
E: libquicktime0: subprocess post-installation script returned error exit status 135
E: libmjpegtools0c2a: dependency problems - leaving unconfigured
E: libnspr4-0d: subprocess post-installation script returned error exit status 135
E: libmozjs0d: dependency problems - leaving unconfigured
E: libnjb5: subprocess post-installation script returned error exit status 135
E: libnss3-0d: dependency problems - leaving unconfigured

i have tried removing each item one at a time and that hasn't worked either. i cannot accomplish anything without recieving these errors. If anyone has any ideas let me know. is it possible to just rebuild my dpkg file?

---

### Post by ciscosurfer on 2006-12-13
You need to make sure you have only one package manager open at a time.

Then issue```
sudo dpkg --configure -a
```

---

### Post by billybag on 2006-12-13
> **ciscosurfer said:**
> You need to make sure you have only one package manager open at a time.

Then issue```
sudo dpkg --configure -a
```
root@hinklestein:/home/billow# sudo dpkg --configure -a
Setting up libboost-thread1.33.1 (1.33.1-7ubuntu1) ...
Bus error (core dumped)
dpkg: error processing libboost-thread1.33.1 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libnjb5 (2.2.5-4.1ubuntu1) ...
Bus error (core dumped)
dpkg: error processing libnjb5 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libktoblzcheck1c2a (1.10-1) ...
Bus error (core dumped)
dpkg: error processing libktoblzcheck1c2a (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libphysfs-1.0-0 (1.0.0-5) ...
Bus error (core dumped)
dpkg: error processing libphysfs-1.0-0 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libconfuse0 (2.5-2) ...
Bus error (core dumped)
dpkg: error processing libconfuse0 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of libaqbanking16:
 libaqbanking16 depends on libktoblzcheck1c2a; however:
  Package libktoblzcheck1c2a is not configured yet.
dpkg: error processing libaqbanking16 (--configure):
 dependency problems - leaving unconfigured
Setting up tcl8.3 (8.3.5-5) ...
Bus error (core dumped)
dpkg: error processing tcl8.3 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of libaqdtaus3:
 libaqdtaus3 depends on libaqbanking16; however:
  Package libaqbanking16 is not configured yet.
dpkg: error processing libaqdtaus3 (--configure):
 dependency problems - leaving unconfigured
Setting up libwxgtk2.6-0 (2.6.3.2.1.5) ...
Bus error (core dumped)
dpkg: error processing libwxgtk2.6-0 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libquicktime0 (0.9.7-0.6ubuntu1) ...
Bus error (core dumped)
dpkg: error processing libquicktime0 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libgtkmm-2.4-1c2a (2.10.2-0ubuntu1) ...
Bus error (core dumped)
dpkg: error processing libgtkmm-2.4-1c2a (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libtdb1 (1.0.6-13) ...
Bus error (core dumped)
dpkg: error processing libtdb1 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of debtags:
 debtags depends on libtdb1; however:
  Package libtdb1 is not configured yet.
dpkg: error processing debtags (--configure):
 dependency problems - leaving unconfigured
Setting up libifp4 (1.0.0.2-3) ...
Bus error (core dumped)
dpkg: error processing libifp4 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libxfce4mcs-manager3 (4.3.99.1-0ubuntu1) ...
Bus error (core dumped)
dpkg: error processing libxfce4mcs-manager3 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up librsync1 (0.9.7-1) ...
Bus error (core dumped)
dpkg: error processing librsync1 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of libgnomemm-2.6-1c2a:
 libgnomemm-2.6-1c2a depends on libgtkmm-2.4-1c2a; however:
  Package libgtkmm-2.4-1c2a is not configured yet.
dpkg: error processing libgnomemm-2.6-1c2a (--configure):
 dependency problems - leaving unconfigured
Setting up liblockdev1 (1.0.3-1) ...

WARNING
Format of device lock files have changed, you will need to restart all
programs that have locked device files using the old version of liblockdev.

Bus error (core dumped)
dpkg: error processing liblockdev1 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libxfcegui4-4 (4.3.99.1-0ubuntu1) ...
Bus error (core dumped)
dpkg: error processing libxfcegui4-4 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of libgnomecanvasmm-2.6-1c2a:
 libgnomecanvasmm-2.6-1c2a depends on libgtkmm-2.4-1c2a; however:
  Package libgtkmm-2.4-1c2a is not configured yet.
dpkg: error processing libgnomecanvasmm-2.6-1c2a (--configure):
 dependency problems - leaving unconfigured
Setting up libxml++2.6c2a (2.14.0-0ubuntu1) ...
Bus error (core dumped)
dpkg: error processing libxml++2.6c2a (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libfltk1.1 (1.1.7-2) ...
Bus error (core dumped)
dpkg: error processing libfltk1.1 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libggz2 (0.0.13-2) ...
Bus error (core dumped)
dpkg: error processing libggz2 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libpano12-0 (2.8.3-1) ...
Bus error (core dumped)
dpkg: error processing libpano12-0 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of agave:
 agave depends on libgtkmm-2.4-1c2a; however:
  Package libgtkmm-2.4-1c2a is not configured yet.
dpkg: error processing agave (--configure):
 dependency problems - leaving unconfigured
Setting up xaw3dg (1.5+E-14ubuntu1) ...
Bus error (core dumped)
dpkg: error processing xaw3dg (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of hugin:
 hugin depends on libboost-thread1.33.1; however:
  Package libboost-thread1.33.1 is not configured yet.
 hugin depends on libpano12-0; however:
  Package libpano12-0 is not configured yet.
 hugin depends on libwxgtk2.6-0 (>= 2.6.3.2.1.1ubuntu2); however:
  Package libwxgtk2.6-0 is not configured yet.
dpkg: error processing hugin (--configure):
 dependency problems - leaving unconfigured
Setting up libode0c2 (0.5-5) ...
Bus error (core dumped)
dpkg: error processing libode0c2 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libshhopt1 (1.1.7-2) ...
Bus error (core dumped)
dpkg: error processing libshhopt1 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libxfce4mcs-client3 (4.3.99.1-0ubuntu1) ...
Bus error (core dumped)
dpkg: error processing libxfce4mcs-client3 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up liblrdf0 (0.4.0-1build1) ...
Bus error (core dumped)
dpkg: error processing liblrdf0 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of libglademm-2.4-1c2a:
 libglademm-2.4-1c2a depends on libgtkmm-2.4-1c2a; however:
  Package libgtkmm-2.4-1c2a is not configured yet.
dpkg: error processing libglademm-2.4-1c2a (--configure):
 dependency problems - leaving unconfigured
Setting up libwv-1.2-1 (1.2.1-2ubuntu0.1) ...
Bus error (core dumped)
dpkg: error processing libwv-1.2-1 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of apt-index-watcher:
 apt-index-watcher depends on libtdb1; however:
  Package libtdb1 is not configured yet.
dpkg: error processing apt-index-watcher (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libaqgeldkarte4:
 libaqgeldkarte4 depends on libaqbanking16; however:
  Package libaqbanking16 is not configured yet.
dpkg: error processing libaqgeldkarte4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ggzcore-bin:
 ggzcore-bin depends on libggz2 (>= 0.0.13); however:
  Package libggz2 is not configured yet.
dpkg: error processing ggzcore-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libggzcore7:
 libggzcore7 depends on libggz2 (>= 0.0.13); however:
  Package libggz2 is not configured yet.
dpkg: error processing libggzcore7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of monster-masher:
 monster-masher depends on libglademm-2.4-1c2a; however:
  Package libglademm-2.4-1c2a is not configured yet.
 monster-masher depends on libgnomecanvasmm-2.6-1c2a; however:
  Package libgnomecanvasmm-2.6-1c2a is not configured yet.
 monster-masher depends on libgnomemm-2.6-1c2a (>= 2.16.0); however:
  Package libgnomemm-2.6-1c2a is not configured yet.
 monster-masher depends on libgtkmm-2.4-1c2a; however:
  Package libgtkmm-2.4-1c2a is not configured yet.
dpkg: error processing monster-masher (--configure):
 dependency problems - leaving unconfigured
Setting up libgwenhywfar38 (2.2.0-1) ...
Bus error (core dumped)
dpkg: error processing libgwenhywfar38 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up lesstif2 (0.94.4-2) ...
Bus error (core dumped)
dpkg: error processing lesstif2 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up liballegro4.2 (4.2.0-5) ...
Bus error (core dumped)
dpkg: error processing liballegro4.2 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of gv:
 gv depends on xaw3dg (>= 1.5+E-1); however:
  Package xaw3dg is not configured yet.
dpkg: error processing gv (--configure):
 dependency problems - leaving unconfigured
Setting up qobex (0.99+1.0beta2-2+3v1ubuntu0) ...
Bus error (core dumped)
dpkg: error processing qobex (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of libaqhbci10:
 libaqhbci10 depends on libaqbanking16; however:
  Package libaqbanking16 is not configured yet.
 libaqhbci10 depends on libgwenhywfar38 (>= 2.1.1); however:
  Package libgwenhywfar38 is not configured yet.
dpkg: error processing libaqhbci10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libggzmod4:
 libggzmod4 depends on libggz2 (>= 0.0.13); however:
  Package libggz2 is not configured yet.
 libggzmod4 depends on libggzcore7 (>= 0.0.13); however:
  Package libggzcore7 is not configured yet.
dpkg: error processing libggzmod4 (--configure):
 dependency problems - leaving unconfigured
Setting up koffice-libs (1.5.2-0ubuntu2) ...
Bus error (core dumped)
dpkg: error processing koffice-libs (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of rdiff-backup:
 rdiff-backup depends on librsync1 (>= 0.9.6); however:
  Package librsync1 is not configured yet.
dpkg: error processing rdiff-backup (--configure):
 dependency problems - leaving unconfigured
Setting up libshhmsg1 (1.4.1-4) ...
Bus error (core dumped)
dpkg: error processing libshhmsg1 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of xconq:
 xconq depends on tcl8.3 (>= 8.3.5); however:
  Package tcl8.3 is not configured yet.
dpkg: error processing xconq (--configure):
 dependency problems - leaving unconfigured
Setting up libnspr4-0d (1.8.0.5-4.2) ...
Bus error (core dumped)
dpkg: error processing libnspr4-0d (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of liquidwar:
 liquidwar depends on liballegro4.2; however:
  Package liballegro4.2 is not configured yet.
dpkg: error processing liquidwar (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 libboost-thread1.33.1
 libnjb5
 libktoblzcheck1c2a
 libphysfs-1.0-0
 libconfuse0
 libaqbanking16
 tcl8.3
 libaqdtaus3
 libwxgtk2.6-0
 libquicktime0
 libgtkmm-2.4-1c2a
 libtdb1
 debtags
 libifp4
 libxfce4mcs-manager3
 librsync1
 libgnomemm-2.6-1c2a
 liblockdev1
 libxfcegui4-4
 libgnomecanvasmm-2.6-1c2a
 libxml++2.6c2a
 libfltk1.1
 libggz2
 libpano12-0
 agave
 xaw3dg
 hugin
 libode0c2
 libshhopt1
 libxfce4mcs-client3
 liblrdf0
 libglademm-2.4-1c2a
 libwv-1.2-1
 apt-index-watcher
 libaqgeldkarte4
 ggzcore-bin
 libggzcore7
 monster-masher
 libgwenhywfar38
 lesstif2
 liballegro4.2
 gv
 qobex
 libaqhbci10
 libggzmod4
 koffice-libs
 rdiff-backup
 libshhmsg1
 xconq
 libnspr4-0d
 liquidwar
Processing was halted because there were too many errors.
root@hinklestein:/home/billow#

---

### Post by ciscosurfer on 2006-12-13
Looks like you're already root.  There's no need to login to a root shell to issue the commands.  Simply use **sudo** as your normal user.

Or, if you want to stay as root, then just enter [B]dpkg --configure -a

[/B]Next, try this puppy```
sudo apt-get -f install
```

---

### Post by billybag on 2006-12-13
> **ciscosurfer said:**
> Looks like you're already root.  There's no need to login to a root shell to issue the commands.  Simply use **sudo** as your normal user.

Or, if you want to stay as root, then just enter [B]dpkg --configure -a

[/B]Next, try this puppy```
sudo apt-get -f install
```
root@hinklestein:/home/billow# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxfce4mcs-client3 libnspr4-0d libfltk1.1 libwv-1.2-1 libmjpegtools0c2a
  libifp4 libmozjs0d libconfuse0 libxfce4mcs-manager3 libquicktime0 libnss3-0d
  libnjb5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
80 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libgtkmm-2.4-1c2a (2.10.2-0ubuntu1) ...

---

