---
title: "the upgrade aborts here!"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by giuseppe20 on 2007-04-22
Hi

i did dist-upgrade two days back. after forcing -f a infinite number of times the problems were circumscribed to only this. But here i got stuck. to move on the only thing i can do is ctrl C (i left it overnight to think about what to do about evms but when i woke up it was still thinking). 

I'm scared at the prospect to have to restart my computer because the error message in the update manager said "your system might be unusable". Please HELP!!!

Ciao
Giu

PS: this is the terminal output...

giuseppemeraya@ubuntumaqroll:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  gnome-menus: Depends: python-gmenu (= 2.18.0-0ubuntu3) but 2.16.1-0ubuntu1 is installed
  kubuntu-desktop: Depends: slocate but it is not installed
  ubuntu-desktop: Depends: slocate but it is not installed
E: Unmet dependencies. Try using -f.
giuseppemeraya@ubuntumaqroll:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  alacarte evms python-gadfly python-gmenu slocate
Suggested packages:
  linux-patch-evms evms-ha python-gmenu-dbg
Recommended packages:
  evms-cli
The following NEW packages will be installed
  slocate
The following packages will be upgraded:
  alacarte evms python-gadfly python-gmenu
4 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
30 not fully installed or removed.
Need to get 408kB of archives.
After unpacking 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) feisty/main python-gmenu 2.18.0-0ubuntu3 [40.3kB]
Get: 2 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) feisty/main alacarte 0.11.3-0ubuntu2 [70.7kB]                                              
Get: 3 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) feisty/main evms 2.5.5-18ubuntu4 [88.0kB]                                                  
Get: 4 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) feisty/main slocate 3.1-1ubuntu1 [31.2kB]                                                  
Get: 5 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) feisty/universe python-gadfly 1.0.0-11 [177kB]                                             
Fetched 408kB in 1m30s (4527B/s)                                                                                           
(Reading database ... 
dpkg: serious warning: files list file for package `xmodmap' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `sane-utils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libart-2.0-2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `skype' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libsane' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `sudo' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libexif10' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgpod0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgdk-pixbuf2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-osd' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgal2.4-0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `sgml-base' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libecal1.2-2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-pexpect' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `fping' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xman' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gstreamer0.8-tools' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxtrap6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gmenu' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `festlex-cmu' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `alacarte' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libjasper-1.701-1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libglut3' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `patch' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libhtml-tree-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xconsole' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libegroupwise1.2-5' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxosd2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libopenobex-1.0-0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libijs-0.35' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python2.4-id3lib' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gadfly' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `outdoors-theme' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libsoup2.2-7' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `lesstif1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `legacyhuman-theme' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnujaxp-java' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwnck16' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libart-2.0-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `festlex-poslex' missing, assuming package has no files currently installed.
171566 files and directories currently installed.)
Preparing to replace python-gmenu 2.16.1-0ubuntu1 (using .../python-gmenu_2.18.0-0ubuntu3_i386.deb) ...
pycentral: pycentral pkgremove: package python-gmenu is not installed
pycentral pkgremove: package python-gmenu is not installed
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package python-gmenu is not installed
pycentral pkgremove: package python-gmenu is not installed
dpkg: error processing /var/cache/apt/archives/python-gmenu_2.18.0-0ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package python-gmenu is not installed
pycentral pkginstall: package python-gmenu is not installed
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace alacarte 0.10.1-0ubuntu1 (using .../alacarte_0.11.3-0ubuntu2_all.deb) ...
pycentral: pycentral pkgremove: package alacarte is not installed
pycentral pkgremove: package alacarte is not installed
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package alacarte is not installed
pycentral pkgremove: package alacarte is not installed
dpkg: error processing /var/cache/apt/archives/alacarte_0.11.3-0ubuntu2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package alacarte is not installed
pycentral pkginstall: package alacarte is not installed
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace evms 2.5.5-15 (using .../evms_2.5.5-18ubuntu4_i386.deb) ...
Unpacking replacement evms ...

---

### Post by TomGla on 2007-04-22
Looks like your CD was corrupted to me.

---

### Post by giuseppe20 on 2007-04-22
it actually was an online upgrade. I had the feeling too thought that the packages were corrupted that's why i downloaded them again after cleaning the apt archive... but even the new versions did not work ad i haven't found anyone who had the same issues with the same packages so... what to do?

ciao
giu

---

### Post by dannyboy79 on 2007-04-25
sudo mv /usr/bin/pycentral /tmp

sudo apt-get -f update

sudo apt-get -f upgrade

then move it back if something else complains.

---

