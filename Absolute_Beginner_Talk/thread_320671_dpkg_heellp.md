---
title: "dpkg heellp"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by billybag on 2006-12-17
whenever i do anything involving dpkg or aptitude, i get this:

The following packages were automatically installed and are no longer required:
  libgnomecupsui1.0-1c2a libxfcegui4-4 evolution-webcal ekiga libzzip-0-12
  libgsf-gnome-1-114 openoffice.org-gnome python-gst0.10 libxfce4mcs-client3
  gcalctool gthumb sharutils gnome-nettool libdc1394-13 kwin
  linux-headers-generic python-at-spi tangerine-icon-theme ttf-thai-tlwg
  libgnome-mag2 kcontrol gucharmap brltty-x11 libbtctl2 zenity
  hwdb-client-gnome xscreensaver-gl gdebi evolution-exchange
  openoffice.org-gtk rhythmbox gedit libmp4v2-0 brltty ubuntu-artwork refblas3
  libapr0 gnome-themes python-virtkey libnspr4-0d libglade-gnome0 kicker
  scim-modules-socket libmysqlclient15-dev alsa-oss libmysql++2c2a libclamav1
  libgpod0 libscim8c2a ttf-lao lapack3 libavformat0d libcdio3 libxfce4util4
  fontforge scim-gtk2-immodule libffi4 human-theme gnome-btdownload
  libatspi1.0-0 libakode2 gnome-volume-manager openoffice.org-evolution
  gtk2-engines libgmp3c2 libkonq4 eog gdm screensaver-default-images
  libfltk1.1 libwv-1.2-1 gtk2-engines-ubuntulooks gnome-spell bug-buddy
  kdebase-bin libbrlapi1 language-selector libxcomposite1 libkpimidentities1
  at-spi tsclient libtse3-0.3.1c2a libdirectfb-0.9-22 vino libmjpegtools0c2a
  firefox-gnome-support libtunepimp3 libifp4 libdbus-qt-1-1c2 wine konqueror
  totem-gstreamer contact-lookup-applet human-gtk-theme libgnome-speech3
  libmozjs0d libconfuse0 hal-device-manager libavcodec0d onboard libnetpbm10
  linux-headers-2.6.17-10 gconf-editor gnome-system-tools libgnomebt0
  libxfce4mcs-manager3 libg2c0 libquicktime0 libgraphicsmagick1 totem
  libglade0 libestools1.2 libnss3-0d xscreensaver-data gauche totem-mozilla
  libnjb5 bluez-pin example-content gimp-python file-roller serpentine
  nautilus-sendto gnome-cups-manager libgwrap-runtime0 ssh-askpass-gnome
  linux-headers-2.6.17-10-generic sound-juicer
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  alsa-oss fontforge gauche kcontrol kdebase-bin kicker konqueror kwin lapack3
  libakode2 libapr0 libbtctl2 libcdio3 libclamav1 libconfuse0 libdbus-qt-1-1c2
  libdirectfb-0.9-22 libestools1.2 libffi4 libfltk1.1 libg2c0 libglade-gnome0
  libglade0 libgmp3c2 libgnome-mag2 libgnome-speech3 libgraphicsmagick1
  libgwrap-runtime0 libifp4 libkonq4 libkpimidentities1 libmjpegtools0c2a
  libmozjs0d libmp4v2-0 libmysql++2c2a libmysqlclient15-dev libnetpbm10
  libnjb5 libnspr4-0d libnss3-0d libquicktime0 libtunepimp3 libwv-1.2-1
  libxcomposite1 libxfce4mcs-client3 libxfce4mcs-manager3 libxfcegui4-4
  libzzip-0-12 refblas3 scim-gtk2-immodule wine

and then i get error messages for each of the files
i.e:
Removing alsa-oss ...
Bus error (core dumped)
dpkg: error processing alsa-oss (--remove):
 subprocess post-removal script returned error exit status 135

i have tried everything i can think of. . dpkg --configure -a. apt-get autoremove. i have tried removingeach file in synaptic. i tried uninstalling recentally installed apps. i am out of ideas and this is wicked annoying.](*,) :confused:

---

### Post by DirtDawg on 2006-12-17
What exactly are you trying to do?

---

### Post by louieb on 2006-12-17
Yes it is annoying. Must be some new feature or bug. I was installing some system stats software the other day and got the message about packages no longer being required. I just let it do it thing and it uninstall the   KDE desktop from my machine. 
Don't know why or how to fix it but I guess I just have to look at the messages closer from now on.

---

### Post by billybag on 2006-12-17
> **DirtDawg said:**
> What exactly are you trying to do?
i get the message everytime i do anything involving dpkg or aptitude.
i-e. apt-get autoremoved, apt-get update, apt-get upgrade...

---

### Post by DirtDawg on 2006-12-17
Wow, sorry man. I dug around for a bit here but I cant find anything even resembling your problem.

Can you think of something you may have installed recently that would cause a problem somewhere? Or if you just installed Edgy, maybe you would have better luck with Dapper? 

Sorry I'm not more help. That's rough.

---

### Post by billybag on 2006-12-17
yeah i have no idea. it happened recently and i have had edgy for a few months

---

### Post by ciscosurfer on 2006-12-17
I realize this should be a last-ditch effort, but maybe a fresh reinstall will fix this issue.  I mention this as an option so that you can possibly see if this problem is recreated again after a clean install.  If it is, then perhaps you have a hardware incompatibility.  If it does not get reproduced after installing clean, then you'll have a fresh OS without this occurrence (more than likely).

---

### Post by billybag on 2006-12-17
> **ciscosurfer said:**
> I realize this should be a last-ditch effort, but maybe a fresh reinstall will fix this issue.  I mention this as an option so that you can possibly see if this problem is recreated again after a clean install.  If it is, then perhaps you have a hardware incompatibility.  If it does not get reproduced after installing clean, then you'll have a fresh OS without this occurrence (more than likely).
do you know how to go about reinstalling without a disk?

---

### Post by Littleweseth on 2006-12-17
Package cache?

Or you could find/download a disc :)

---

