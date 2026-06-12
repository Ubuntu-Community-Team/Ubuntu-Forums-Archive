---
title: "[SOLVED] Too many dependencies?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by virx on 2007-10-30
I want to install pidgin to my Openbox gnome-free Gutsy.
aptitude install pidgin
```
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
The following packages are unused and will be REMOVED:
  libast2 libimlib2 libungif4g 
The following NEW packages will be automatically installed:
  gamin gnome-keyring gnome-mime-data gnome-mount gstreamer0.10-alsa 
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x 
  launchpad-integration libavahi-glib1 libbonobo2-0 libbonobo2-common 
  libcdparanoia0 libdv4 libgadu3 libgamin0 libgnome-keyring0 libgnome2-0 
  libgnome2-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra 
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtkspell0 
  libhesiod0 libiec61883-0 liblaunchpad-integration0 libmeanwhile1 
  libnm-glib0 liboil0.3 libperl5.8 libpurple0 libshout3 libtag1c2a 
  libvisual-0.4-0 libvisual-0.4-plugins libwavpack1 libzephyr3 oss-compat 
  pidgin-data shared-mime-info 
```

gnome-mount - why would I need that for pidgin?
I have experienced the same problem with other programs too.

Is it possible to skip some dependencie packages?
Is only chance later apt-get remove unwanted_dependency?

---

### Post by haldean on 2007-10-30
It wants all those dependencies because pidgin is a Gnome program with Gnome integration, so it expects all of those packages to be there. If you want to use it, those need to stay installed.


You could try Kopete - it's the KDE version that does pretty much the same thing. You might have the same problem, though - both Kopete and Pidgin are designed to be pretty well integrated with the desktop :S

---

### Post by dca on 2007-10-30
Indeed, Kopete requires kdelibs and a bunch of other programs...  If you're interested in just AIM usage, see if this still works:
 
[http://www.aim.com/get_aim/linux/latest_linux.adp](http://www.aim.com/get_aim/linux/latest_linux.adp)

---

### Post by EXCiD3 on 2007-10-30
I dont think mine ever needed *that* many dependencies just for pidgin. Are you sure its not including dependencies for another application you had/are going to install?

You can always compile from source:
The following command installs all the dependencies needed to compile from source...Theoretically they should be the same as the ones you should be seeing.
```
sudo apt-get install libgtk2.0-dev libxml2-dev gettext libnss-dev libnspr-dev
```
extract the source and execute these commands in terminal in the source directory:
```
./configure
make
sudo make install
```

---

### Post by kerry_s on 2007-10-30
have you tried ayttm? it's very small very simple, no tray icon though, just a simple im.

---

### Post by haldean on 2007-10-30
@excid3: You don't notice all of those dependencies cuz they're already installed when you install Gnome or KDE... Openbox is way slimmer and doesn't come with a lot of libraries that Gnome / KDE apps need.

---

### Post by EXCiD3 on 2007-10-30
Oops, wasn't thinking...Sorry about that.

---

### Post by virx on 2007-10-31
OK gnome libraries got explained - didn't know, that pidgin was meant for gnome (forgot Gaim part ;))

---

### Post by urukrama on 2007-10-31
You might also want to try apt-get instead of aptitude, or prevent aptitude from installing recommended (but not essential) packages. See "man aptitude" for details.

---

### Post by erginemr on 2007-10-31
I would suggest the same. I have discovered that feature not long ago, which causes installation of recommended (but sometimes redundant) packages along with the ones we deliberately demand. 

I have noticed its effect when I tried to install tvtime with "sudo aptitude install tvtime" and the system tried to install a myriad of packages summing up to ~44 MB. On the other hand, when I disable the automated installation of recommended packages, the same command above installs only one or two packages with ~1.8 MB.

To disable this feature, type "aptitude" from the console and nothing else, you end up with a text-mode but graphical menu of "aptitude" that lists all installed and available programs, allows you to install / remove them and what not.

From "Ctrl+T" -> Main Menu -> Options -> Dependency Handling (the mouse also works), disable the line that says: "Install Recommended Packages automatically". Leave aptitude with "q", then type "sudo aptitude update" from the console. 

It may or may not help your issue with Pidgin, but is still worth a try.

---

### Post by virx on 2007-10-31
> **urukrama]You might also want to try apt-get instead of aptitude, or prevent aptitude from installing recommended (but not essential) packages. See "man aptitude" for details.
[/quote]

apt-get install pidgin
```
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  launchpad-integration libavahi-glib1 libgadu3 libgstreamer0.10-0
  libgtkspell0 libhesiod0 liblaunchpad-integration0 libmeanwhile1 libnm-glib0
  libperl5.8 libpurple0 libzephyr3 pidgin-data
Suggested packages:
  gstreamer0.10-tools gstreamer0.10-plugins tcl8.4 tk8.4 gnome-panel kicker
  docker evolution-data-server
Recommended packages:
  libgnome2-0 gstreamer0.10-plugins-base gstreamer0.10-plugins-good
The following NEW packages will be installed:
  launchpad-integration libavahi-glib1 libgadu3 libgstreamer0.10-0
  libgtkspell0 libhesiod0 liblaunchpad-integration0 libmeanwhile1 libnm-glib0
  libperl5.8 libpurple0 libzephyr3 pidgin pidgin-data
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 5054kB of archives.
After unpacking 29.5MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

A lot better.


[QUOTE=erginemr said:**
> 
From "Ctrl+T" -> Main Menu -> Options -> Dependency Handling (the mouse also works), disable the line that says: "Install Recommended Packages automatically". Leave aptitude with "q", then type "sudo aptitude update" from the console. 
It may or may not help your issue with Pidgin, but is still worth a try.

aptitude install pidgin
```
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
The following NEW packages will be automatically installed:
  launchpad-integration libavahi-glib1 libgadu3 libgstreamer0.10-0 
  libgtkspell0 libhesiod0 liblaunchpad-integration0 libmeanwhile1 
  libnm-glib0 libperl5.8 libpurple0 libzephyr3 pidgin-data 
The following NEW packages will be installed:
  launchpad-integration libavahi-glib1 libgadu3 libgstreamer0.10-0 
  libgtkspell0 libhesiod0 liblaunchpad-integration0 libmeanwhile1 
  libnm-glib0 libperl5.8 libpurple0 libzephyr3 pidgin pidgin-data 
0 packages upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 5054kB of archives. After unpacking 29.5MB will be used.
Do you want to continue? [Y/n/?] 
```

Does the same as apt-get, but when i remove pidgin, dependencies will be removed also.

It solved my problem, thanks for help.

---

### Post by erginemr on 2007-11-01
Good to hear that virx. To let the others know, you may consider marking your thread as "solved".

Take Care...

---

### Post by virx on 2007-11-03
Done ;)

---

