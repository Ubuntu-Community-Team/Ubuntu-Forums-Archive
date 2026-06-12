---
title: "Software Index is Broken"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by cumanzor on 2007-12-09
I get an error message saying that the software index is broken whenever I try to run an update from the Synaptic Update Manager. It tells me to run sudo apt-get install -f but this the error I get:

```
manuel@home:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libtext-glob-perl clamav-base libcarp-clan-perl libclamav2 cmake libgmp3c2 libnumber-compare-perl libbit-vector-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kde-icons-oxygen kdebase-runtime-bin kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
Suggested packages:
  kdebase-kde4
The following NEW packages will be installed:
  kde-icons-oxygen kdebase-runtime-bin kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
0 upgraded, 5 newly installed, 0 to remove and 63 not upgraded.
9 not fully installed or removed.
Need to get 0B/58.6MB of archives.
After unpacking 87.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 132365 files and directories currently installed.)
Unpacking kde-icons-oxygen (from .../kde-icons-oxygen_4%3a3.96.0-1ubuntu1~gutsy1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kde-icons-oxygen_4%3a3.96.0-1ubuntu1~gutsy1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/icons/oxygen/128x128/apps/phonon-xine.png', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-runtime-data-common (from .../kdebase-runtime-data-common_4%3a3.96.0-1ubuntu1~gutsy1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data-common_4%3a3.96.0-1ubuntu1~gutsy1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/icons/crystalsvg/scalable/apps/hwinfo.svgz', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-runtime-data (from .../kdebase-runtime-data_4%3a3.96.0-1ubuntu1~gutsy1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data_4%3a3.96.0-1ubuntu1~gutsy1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/applications/kde4/knetattach.desktop', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-runtime-bin-kde4 (from .../kdebase-runtime-bin-kde4_4%3a3.96.0-1ubuntu1~gutsy1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-bin-kde4_4%3a3.96.0-1ubuntu1~gutsy1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/kdebugdialog', which is also in package kde4base
Unpacking kdebase-runtime-bin (from .../kdebase-runtime-bin_4%3a3.96.0-1ubuntu1~gutsy1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-bin_4%3a3.96.0-1ubuntu1~gutsy1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/kde4-menu', which is also in package kde4base
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-icons-oxygen_4%3a3.96.0-1ubuntu1~gutsy1_all.deb
 /var/cache/apt/archives/kdebase-runtime-data-common_4%3a3.96.0-1ubuntu1~gutsy1_all.deb
 /var/cache/apt/archives/kdebase-runtime-data_4%3a3.96.0-1ubuntu1~gutsy1_all.deb
 /var/cache/apt/archives/kdebase-runtime-bin-kde4_4%3a3.96.0-1ubuntu1~gutsy1_all.deb
 /var/cache/apt/archives/kdebase-runtime-bin_4%3a3.96.0-1ubuntu1~gutsy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
manuel@home:~$ 

```

Apparently, the problem appeared when I tried to install KDE 4 (don't really remember if it was in alpha or beta). Anyways, now I can't update, remove or install any applications, and I really don't want to reinstall up to this point, what can I do about it??

Thanks!

---

### Post by Kingsley on 2007-12-09
Try this.
```
sudo apt-get autoremove && sudo apt-get clean && sudo apt-get install -f
```

---

### Post by ptn107 on 2007-12-09
Open up *Synaptic.*  Click* Custom Filters* on the bottom left, and then *Broken* in the left column.  What packages (if any) are listed on the right?

**You can try the only known workaround[1] which is to remove any of the offending packages and reinstall them, but lets see if we can avoid doing that.

[1][http://ubuntuforums.org/showthread.php?t=528131](http://ubuntuforums.org/showthread.php?t=528131)

---

### Post by Toadmund on 2008-02-29
> **ptn107 said:**
> Open up *Synaptic.*  Click* Custom Filters* on the bottom left, and then *Broken* in the left column.  What packages (if any) are listed on the right?
**You can try the only known workaround[1] which is to remove any of the offending packages and reinstall them, but lets see if we can avoid doing that.


Thanks, this worked for my update manager problem:)

---

