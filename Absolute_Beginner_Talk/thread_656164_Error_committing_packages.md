---
title: "Error committing packages"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by martyn314 on 2008-01-02
In common with some other people on the forums I've had big problems with Gutsy and when I update using Adept Updater I get a message saying 'There was an error committing packages'.

---

### Post by bapoumba on 2008-01-02
Could you please post your sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by martyn314 on 2008-01-02
Sorry - hadn't quite finished on the above!!

It mostly affects open office which won't update, and when I try to reinstall I get messages like:

(Reading database ... 137408 files and directories currently installed.)
Unpacking openoffice.org-style-human (from .../openoffice.org-style-human_1%3a2.
3.0-1ubuntu5.3_all.deb) ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-style-human_1%3a2.
3.0-1ubuntu5.3_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)

I've tried doing 

sudo apt-get update -f
sudo apt-get upgrade

I'm running Kubuntu on and AMD64.

---

### Post by martyn314 on 2008-01-02
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

---

### Post by bapoumba on 2008-01-02
Please try to clear the cache:
```
sudo apt-get clean
```

Then run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Do you still have errors?

---

### Post by martyn314 on 2008-01-02
Still much the same, I'm afraid:

The following packages have unmet dependencies.
  openoffice.org: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not installed
                  Depends: openoffice.org-writer but it is not installed
                  Depends: openoffice.org-calc but it is not installed
                  Depends: openoffice.org-draw but it is not installed
                  Depends: openoffice.org-java-common (> 2.2.0-4) but it is not installed
  openoffice.org-base: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not installed
                       Depends: openoffice.org-java-common (> 2.2.0-4) but it is not installed
  openoffice.org-filter-mobiledev: Depends: openoffice.org-java-common (> 2.2.0-4) but it is not installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not installed
                          Depends: openoffice.org-draw (= 1:2.3.0-1ubuntu5.3) but it is not installed
  openoffice.org-math: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not installed
  openoffice.org-officebean: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not installed
                             Depends: openoffice.org-java-common (> 2.2.0-4) but it is not installed
  python-uno: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by bapoumba on 2008-01-02
Okay, but the funky cache error is gone ;)

```
sudo apt-get -f install
```

---

### Post by martyn314 on 2008-01-02
That helped - it downloaded something, but still had:

Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-common_1%3a2.3.0-1ubuntu5.3_all.deb
 /var/cache/apt/archives/openoffice.org-core_1%3a2.3.0-1ubuntu5.3_amd64.deb
 /var/cache/apt/archives/openoffice.org-writer_1%3a2.3.0-1ubuntu5.3_amd64.deb
 /var/cache/apt/archives/openoffice.org-calc_1%3a2.3.0-1ubuntu5.3_amd64.deb
 /var/cache/apt/archives/openoffice.org-draw_1%3a2.3.0-1ubuntu5.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bapoumba on 2008-01-02
Do you have ubuntu-desktop and openoffice.org installed?

```
aptitude show ubuntu-desktop
aptitude show openoffice.org
```

---

### Post by martyn314 on 2008-01-02
They weren't installed.  I've tried installing (using sudo apt-get install ubuntu-desktop), but it still comes up with errors.  Currently the output for aptitude show ubuntu-desktop is:

Package: ubuntu-desktop
State: unpacked
Automatically installed: yes
Version: 1.79
Priority: optional
Section: metapackages
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Uncompressed Size: 49.2k
Depends: acpi, acpi-support, acpid, alacarte, anacron, avahi-daemon, bc,
         cdparanoia, consolekit, cupsys, cupsys-bsd, cupsys-client,
         cupsys-driver-gutenprint, dc, dcraw, desktop-file-utils, doc-base,
         dvd+rw-tools, eog, evince, evolution-webcal, fast-user-switch-applet,
         file-roller, foomatic-db, foomatic-db-engine, foomatic-db-hpijs,
         foomatic-filters, fortune-mod, gcalctool, gconf-editor, gdebi, gdm,
         gedit, genisoimage, ghostscript-x, gimp-python, gnome-about,
         gnome-app-install, gnome-applets, gnome-btdownload,
         gnome-control-center, gnome-icon-theme, gnome-keyring-manager,
         gnome-media, gnome-menus, gnome-netstatus-applet, gnome-nettool,
         gnome-panel, gnome-pilot-conduits, gnome-power-manager, gnome-session,
         gnome-spell, gnome-system-monitor, gnome-system-tools, gnome-terminal,
         gnome-themes, gnome-utils, gnome-volume-manager, gstreamer0.10-alsa,
         gstreamer0.10-esd, gstreamer0.10-plugins-base-apps, gthumb,
         gtk2-engines, gtk2-engines-pixbuf, gucharmap, hal, hal-device-manager,
         hotkey-setup, hwdb-client-gnome, language-selector, lftp,
         libgl1-mesa-glx, libglut3, libgnome2-perl, libgnomevfs2-bin,
         libgnomevfs2-extra, libpam-foreground, libpt-plugins-v4l,
         libpt-plugins-v4l2, libsasl2-modules, libxp6, metacity, nautilus,
         nautilus-cd-burner, nautilus-sendto, notification-daemon,
         openprinting-ppds, pnm2ppa, powermanagement-interface, readahead,
         rss-glx, screen, screensaver-default-images, scrollkeeper, serpentine,
         slocate, smbclient, sound-juicer, ssh-askpass-gnome, synaptic,
         system-config-printer, tangerine-icon-theme, tsclient,
         ttf-bitstream-vera, ttf-dejavu-core, ttf-freefont, ubuntu-artwork,
         ubuntu-sounds, unzip, update-notifier, usplash, usplash-theme-ubuntu,
         vino, wodim, x-ttcidfont-conf, xdg-user-dirs, xdg-user-dirs-gtk,
         xkb-data, xorg, xscreensaver-data, xscreensaver-gl, xterm, xvnc4viewer,
         yelp, zenity, zip
Recommends: app-install-data-commercial, apport-gtk, avahi-autoipd, bluez-cups,
            bluez-gnome, bluez-utils, bogofilter, brltty, brltty-x11, bug-buddy,
            compiz, contact-lookup-applet, cups-pdf, deskbar-applet, discover1,
            displayconfig-gtk, diveintopython, ekiga, espeak, evolution,
            evolution-exchange, evolution-plugins, example-content, f-spot,
            firefox, firefox-gnome-support, foo2zjs, gcc, gimp, gimp-print,
            gnome-accessibility-themes, gnome-games, gnome-mag, gnome-orca,
            gnome-screensaver, gnome-user-guide, hal-cups-utils, hplip,
            landscape-client, laptop-detect, libdeskbar-tracker,
            libgl1-mesa-dri, libnss-mdns, libpam-gnome-keyring,
            linux-headers-generic, make, min12xxw, network-manager-gnome,
            onboard, openoffice.org, openoffice.org-evolution,
            openoffice.org-gnome, pidgin, powernowd, pxljr, restricted-manager,
            rhythmbox, scim, scim-gtk2-immodule, splix, tomboy, totem,
            totem-mozilla, tracker, tracker-search-tool, ttf-arabeyes,
            ttf-arphic-uming, ttf-gentium, ttf-indic-fonts-core,
            ttf-kochi-gothic, ttf-kochi-mincho, ttf-lao, ttf-malayalam-fonts,
            ttf-mgopen, ttf-thai-tlwg, ttf-unfonts-core, ubufox, ubuntu-docs,
            wvdial, xcursor-themes, xdg-utils, xresprobe, xsane





and for openoffice.org:

Package: openoffice.org
State: not installed
Version: 1:2.3.0-1ubuntu5.3
Priority: optional
Section: editors
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 45.1k
Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3), openoffice.org-writer,
         openoffice.org-calc, openoffice.org-impress, openoffice.org-draw,
         openoffice.org-math, openoffice.org-base, openoffice.org-java-common (>
         2.2.0-4)
Recommends: openoffice.org-filter-mobiledev, openoffice.org-officebean,
            openoffice.org-filter-binfilter
Suggests: hunspell-dictionary, myspell-dictionary, openoffice.org-help-2.3,
          openoffice.org-l10n-2.3, menu, unixodbc, cupsys-bsd, libsane,
          ttf-dejavu | ttf-bitstream-vera, openoffice.org-hyphenation,
          openoffice.org2-thesaurus, libxrender1, libgl1, msttcorefonts,
          openoffice.org-gnome | openoffice.org-kde, iceweasel | firefox |
          icedove | thunderbird | iceape-browser | mozilla-browser, gij |
          java-gcj-compat | libgcj8-1-awt | sun-java5-jre | sun-java6-jre |
          icedtea-java7-jre | java2-runtime, openclipart-openoffice.org,
          pstoedit, imagemagick, libpaper-utils, gstreamer0.10-plugins-base,
          gstreamer0.10-plugins-good, gstreamer0.10-plugins-ugly,
          gstreamer0.10-plugins-bad, gstreamer0.10-ffmpeg
Conflicts: openoffice.org2 (< 1:2.3.0-1ubuntu5.3)
Replaces: openoffice.org2 (< 1:2.3.0-1ubuntu5.3), openoffice.org-debian-files
Provides: openoffice.org2
Description: OpenOffice.org Office suite
 OpenOffice.org is a full-featured office productivity suite that provides a
 near drop-in replacement for Microsoft(R) Office.

 This metapackage installs all components of openoffice.org:
 * openoffice.org-writer: Word processor
 * openoffice.org-calc: Spreadsheet
 * openoffice.org-impress: Presentation
 * openoffice.org-draw: Drawing
 * openoffice.org-base: Database
 * openoffice.org-math: Equation editor
 * openoffice.org-filter-mobiledev: Mobile Devices filters
 * openoffice.org-filter-binfilter: legacy filters (e.g. StarOffice 5.2)

 You can extend the functionality of OpenOffice.org by installing these
 packages:
 * hunspell-dictionary-*/myspell-dictionary-*: Hunspell/Myspell dictionaries for
   use with OpenOffice.org
 * openoffice.org-l10n-*: UI interface translation
 * openoffice.org-help-*: User help
 * openoffice.org-thesaurus-*: Thesauri for the use with OpenOffice.org
 * openoffice.org-hyphenation-*: Hyphenation patterns for OpenOffice.org
 * openoffice.org-gtk: Gtk UI Plugin, GNOME File Picker support, QuickStarter
   for GNOMEs notification are
 * openoffice.org-gnome: GNOME VFS, GConf backend
 * openoffice.org-kde: KDE UI Plugin and KDE File Picker support
 * openoffice.org-headless: Headless (svp) UI Plugin
 * menu: Will add openoffice.org menu entries for every Debian window manager.
 * unixodbc: ODBC database support
 * cupsys-bsd: Allows OpenOffice.org to detect your CUPS printer queues
   automatically
 * libsane: Use your sane-supported scanner with OpenOffice.org
 * libxrender1: Speed up display by using Xrender library
 * libgl1: OpenGL support
 * openclipart-openoffice.org: Open Clip Art Gallery with OOo index files
 * iceweasel | firefox | icedove | thunderbird | iceape-browser |
   mozilla-browser: Mozilla profile with Certificates needed for XML Security...
 * msttcorefonts: Installs standard MS truetype fonts (contrib)
 * java-gcj-compat/gij-4.1 | j2re1.4 (non-free) | java2-runtime Java Runtime
   Environment for use with OpenOffice.org
 * pstoedit / imagemagick: helper tools for EPS thumbnails
 * gstreamer0.10-plugins-*: GStreamer plugins for use with OOos media backend
 * libpaper-utils: papersize detection support via paperconf

---

### Post by bapoumba on 2008-01-02
Okay, so what is the error to:
```
sudo apt-get install openoffice.org
```

I see ubuntu-desktop is installed. openoffice.org package may be the origin of your problems.

---

### Post by martyn314 on 2008-01-02
Done that, and then sudo apt-get -f install and get the following output:

Errors were encountered while processing:
 /var/cache/apt/archives/gnome-applets-data_2.20.0-0ubuntu1_all.deb
 /var/cache/apt/archives/libestools1.2_1%3a1.2.3-10_amd64.deb
 /var/cache/apt/archives/system-config-printer_0.7.75+svn1653-0ubuntu2_all.deb
 /var/cache/apt/archives/linux-headers-2.6.22-14_2.6.22-14.47_all.deb
 /var/cache/apt/archives/openoffice.org-common_1%3a2.3.0-1ubuntu5.3_all.deb
 /var/cache/apt/archives/openoffice.org-core_1%3a2.3.0-1ubuntu5.3_amd64.deb
 /var/cache/apt/archives/openoffice.org-draw_1%3a2.3.0-1ubuntu5.3_amd64.deb
 /var/cache/apt/archives/eog_2.20.1-0ubuntu1_amd64.deb
 /var/cache/apt/archives/gucharmap_1%3a1.10.1-0ubuntu1_amd64.deb
 /var/cache/apt/archives/xscreensaver-gl_4.24-5ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by martyn314 on 2008-01-02
The original error is:

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  festival: Depends: libestools1.2 but it is not going to be installed
  gnome-applets: Depends: gnome-applets-data (>= 2.20) but it is not going to be installed
                 Depends: gnome-applets-data (< 2.21) but it is not going to be installed
  hal-cups-utils: Depends: system-config-printer but it is not going to be installed
  linux-headers-2.6.22-14-generic: Depends: linux-headers-2.6.22-14 but it is not going to be installed
  openoffice.org: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not going to be installed
                  Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
  openoffice.org-base: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not going to be installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not going to be installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not going to be installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not going to be installed
                          Depends: openoffice.org-draw (= 1:2.3.0-1ubuntu5.3) but it is not going to be installed
  openoffice.org-java-common: Depends: openoffice.org-common but it is not going to be installed
  openoffice.org-math: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not going to be installed
  openoffice.org-officebean: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but it is not going to be installed
  openoffice.org-style-human: Depends: openoffice.org-common (= 1:2.3.0-1ubuntu5.3) but it is not going to be installed
  ubuntu-desktop: Depends: eog but it is not going to be installed
                  Depends: gucharmap but it is not going to be installed
                  Depends: system-config-printer but it is not going to be installed
                  Depends: xscreensaver-gl but it is not going to be installed
                  Recommends: example-content but it is not going to be installed
                  Recommends: f-spot but it is not going to be installed
                  Recommends: gnome-user-guide but it is not going to be installed
                  Recommends: openoffice.org-evolution but it is not going to be installed
                  Recommends: ubuntu-docs but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).

---

### Post by bapoumba on 2008-01-04
Sorry, I got a little carried away and did not answer. Do you still have the error ?

---

### Post by martyn314 on 2008-01-04
No worries. I do still have the error, although I went fishing elsewhere on the forums and tried something that seemed to make it worse.  I gave in and decided to reinstall kubuntu.  Having done this and tried 'sudo apt-get dist-upgrade' it comes up with the error:

The following packages have unmet dependencies.
  gnome-applets: Depends: gnome-applets-data (>= 2.20) but it is not installed
                 Depends: gnome-applets-data (< 2.21) but it is not installed
  yelp: Depends: firefox (>= 1.5) but it is not installed
E: Unmet dependencies. Try using -f.

If I try using adept to upgrade it runs the version upgrade wizard, but won't install it, saying that I don't have the necessary prerequisites.

---

### Post by martyn314 on 2008-01-04
...sorry, should add that at least open office is working now!

---

### Post by PmDematagoda on 2008-01-04
Not sure about this, but did you check the installation CD for defects by any chance?

---

### Post by martyn314 on 2008-01-04
No, but the errors look very similar to what I was getting before which was an upgrade from Feisty, which worked fine.  How would I go about checking it - everything seems to run fine from it.

---

### Post by PmDematagoda on 2008-01-04
When you boot the Live CD, you can see an option on the Live CD menu to check the CD for defects, that is what you will need to do. If you get any errors from the CD check, that means the CD is corrupted and may be causing the problems you are having right now with Kubuntu.

---

### Post by bapoumba on 2008-01-05
Okay, if it is a fresh install, please post your sources.list:
```
cat /etc/apt/sources.list
```

If you had some network problems at the moment Ubuntu installed and was fetching packages, chances are good that some repositories are missing (this is the normal procedure during the install. If a repo is unreachable, for whatever reason, it gets commented in the sources.list and the install goes on without it).

---

### Post by martyn314 on 2008-01-05
The CD doesn't have any errors on it.  Sources.list is:

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security multiverse

---

