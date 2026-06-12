---
title: "Damn!! I'm a noob. i broke my system"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by astrolabio on 2007-03-09
i needed to install glimpse (a search utility thing). 

Since it wasn't in edgy repositories i maually downloaded it from [http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/).
But it was bitching about libc6 version (2.4 in edgy, it wanted the 2.5 of feisty) so i downloaded also libc6 e libc6-i686 from said site and i installed them.

At the beginning everything seemed to work ok and i was very proud of my 2c hack. 

But now if i try to use apt-get again it ask me if i want to fix the unmet dependency. Apparently the rest of the packages still bitch about the old version of libc6. Unfortunately the fix seems to be f@#@#g remove everything!!

Now this is exacly what happens:

# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.4-1ubuntu12.3) but 2.5-0ubuntu11 is installed
E: Unmet dependencies. Try using -f.

so let's try it
# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpopt-dev libsm-dev kppp libattr1-dev libice-dev libaspell-dev libtasn1-3-dev
  libatk1.0-dev libaudiofile-dev libaudio-dev libglib2.0-dev libgpg-error-dev
  x11proto-gl-dev x11proto-xinerama-dev libpango1.0-dev g++-4.1 libpcre3-dev
  libopencdk8-dev x11proto-render-dev libglade2-dev libgcrypt11-dev liblualib50-dev
  libxi-dev libxmu-headers libxrender-dev libcairo2-dev mesa-common-dev
  libmysqlclient15-dev libsasl2-dev libavahi-client-dev libogg-dev libjasper-1.701-dev
  qt4-designer-kdecopy libqt3-compat-headers libstartup-notification0-dev libpng12-dev
  libsqlite0-dev libstdc++6-4.1-dev libfontconfig1-dev libpcrecpp0 x11proto-composite-dev
  intltool foomatic-db-hpijs libtool libltdl3-dev liblua50-dev libxcursor-dev libexif-dev
  libusb-dev libgphoto2-2-dev lua50 libavahi-qt3-dev libacl1-dev libglu1-mesa-dev
  libgnutls-dev libqt3-mt-dev x11proto-randr-dev hspell x11proto-damage-dev digikam
  libdbus-1-dev libxslt1-dev libssl-dev libxt-dev libgtk2.0-dev libxmu-dev libjpeg62-dev
  libqt4-core-kdecopy libxdamage-dev bogofilter zlib1g-dev libxml2-dev libtiff4-dev
  libfreetype6-dev libart-2.0-dev libesd0-dev x11proto-fixes-dev libqt4-sql-kdecopy
  liblzo-dev libqt3-headers libxcomposite-dev libasound2-dev libtiffxx0c2 libgl1-mesa-dev
  liblcms1-dev libqt4-dev-kdecopy libxrandr-dev libkadm55 libexpat1-dev libc6-dev libpq5
  libxft-dev libqt4-gui-kdecopy libartsc0-dev libopenexr-dev libqt4-qt3support-kdecopy
  libxfixes-dev libmng-dev libavahi-common-dev libxinerama-dev kdesdk-scripts
  libcupsys2-dev libvorbis-dev gettext-kde libidn11-dev libberylsettings-dev kdepim-wizards
  libbz2-dev libarts1-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  digikam g++-4.1 libacl1-dev libart-2.0-dev libarts1-dev libartsc0-dev libasound2-dev
  libatk1.0-dev libattr1-dev libaudiofile-dev libavahi-qt3-dev libbz2-dev libc6-dev
  libcairo2-dev libcupsys2-dev libesd0-dev libexif-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev libglade2-dev libglib2.0-dev
  libglu1-mesa-dev libgnutls-dev libgpg-error-dev libgphoto2-2-dev libgtk2.0-dev
  libjpeg62-dev liblua50-dev liblualib50-dev liblzo-dev libmng-dev libmysqlclient15-dev
  libogg-dev libopencdk8-dev libopenexr-dev libpango1.0-dev libpcre3-dev libpng12-dev
  libpopt-dev libqt3-mt-dev libqt4-dev-kdecopy libsasl2-dev libsqlite0-dev libssl-dev
  libstdc++6-4.1-dev libtiff4-dev libtool libusb-dev libvorbis-dev libxft-dev libxml2-dev
  libxslt1-dev qt4-designer-kdecopy zlib1g-dev
0 upgraded, 0 newly installed, 57 to remove and 6 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 147MB disk space will be freed.
Do you want to continue [Y/n]? HELL NO!!

Any apt-get guru around??

---

### Post by Crooksey on 2007-03-09
```
sudo dpkg -r unwanted_package_you_installed
```

Then update

---

### Post by louieb on 2007-03-09
>  The following packages were automatically installed and are no longer required:
Its a bug in apt-get. Some problem syncing it with aptitude. Saw a bug report on the Debian site the other day. It removed my kUbuntu-desktop once. I've learned to read the stuff before pressing ok.

---

### Post by astrolabio on 2007-03-09
> **Crooksey said:**
> ```
sudo dpkg -r unwanted_package_you_installed
```

Then update

Thanks for the reply, but it doesn't seem to work.

as i try 
sudo dpkg -r libc6 libc6-i686
i get a LOOOOOOOOOOONG list of errors. It seems that basically all the packages on my system are on a strike.

I post just the end of it:

...
...
...
 gnome-terminal depends on libc6 (>= 2.4-1).
 ico depends on libc6 (>= 2.3.4-1).
 byacc depends on libc6 (>= 2.3.4-1).
 libxmuu1 depends on libc6 (>= 2.4-1).
 libxml-parser-perl depends on libc6 (>= 2.3.2.ds1-4); however:
  Package libc6 is to be removed.
 finger depends on libc6 (>= 2.4-1).
 samba depends on libc6 (>= 2.4-1).
 libphysfs-1.0-0 depends on libc6 (>= 2.3.4-1).
 xset depends on libc6 (>= 2.4-1).
 libsysfs2 depends on libc6 (>= 2.4-1).
 debianutils depends on libc6 (>= 2.4-1).
 libfreetype6 depends on libc6 (>= 2.4-1).
 sudo depends on libc6 (>= 2.4-1).
 adept-notifier depends on libc6 (>= 2.4-1); however:
  Package libc6 is to be removed.
 libsane depends on libc6 (>= 2.4-1).
 gij-4.1 depends on libc6 (>= 2.4-1).
 coreutils depends on libc6 (>= 2.4-1).
 rtorrent depends on libc6 (>= 2.4-1).
 libisccc0 depends on libc6 (>= 2.4-1).
 libxdmcp6 depends on libc6 (>= 2.4-1).
 libpq4 depends on libc6 (>= 2.4-1).
 libpq5 depends on libc6 (>= 2.4-1).
 shared-mime-info depends on libc6 (>= 2.4-1).
 pdl depends on libc6 (>= 2.4-1); however:
  Package libc6 is to be removed.
 mktemp depends on libc6 (>= 2.4-1).
 kipi-plugins depends on libc6 (>= 2.4-1).
 libart-2.0-2 depends on libc6 (>= 2.3.2.ds1-4).
 cdrecord depends on libc6 (>= 2.4-1).
 gimp depends on libc6 (>= 2.4-1).
 dash depends on libc6 (>= 2.4-1).
 kdepasswd depends on libc6 (>= 2.4-1).
 libnjb5 depends on libc6 (>= 2.4-1).
 kaudiocreator depends on libc6 (>= 2.4-1).
 librecode0 depends on libc6 (>= 2.3.4-1).
 libdjvulibre15 depends on libc6 (>= 2.4-1).
 libboost-thread1.33.1 depends on libc6 (>= 2.4-1).
 wlassistant depends on libc6 (>= 2.4-1).
 libbonoboui2-0 depends on libc6 (>= 2.4-1).
 libgsf0.0-cil depends on libc6 (>= 2.4-1).
 tcpd depends on libc6 (>= 2.4-1).
 libgtkspell0 depends on libc6 (>= 2.3.4-1).
 libostyle1c2 depends on libc6 (>= 2.4-1).
 xmodmap depends on libc6 (>= 2.4-1).
dpkg: error processing libc6 (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of libc6-i686:
 ubuntu-minimal depends on libc6-i686.
dpkg: error processing libc6-i686 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libc6
 libc6-i686
 
:confused:

---

### Post by astrolabio on 2007-03-09
It seems that i fixed it. 

Basically i reversed the 2c hack. I went to the same site as before ([http://packages.ubuntu.com](http://packages.ubuntu.com)) and i downloaded libc6 and libc6-i686 back from edgy list.

I installed them as before (right click on Konqueror and then Kubuntu Package menu/Install Package).

Then 
apt-get install -f
apt-get upgrade
And i'm back on track again.:guitar:

---

### Post by Crooksey on 2007-03-09
Now is this not evidence to mix release files?

---

### Post by easyease on 2007-03-09
> **Crooksey said:**
> Now is this not evidence to mix release files?
hell yeah!

---

