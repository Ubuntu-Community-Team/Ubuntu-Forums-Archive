---
title: "apt-get upgrade error"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by heathguy on 2007-03-05
When I try to run apt-get upgrade I get the following messages:

# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  nautilus-sendto: Depends: libbonobo2-0 (>= * 2.15.0) but 2.16.0-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.


Of course I have tried running apt-get -f install and get the following message
 # apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  nautilus-sendto
Suggested packages:
  sylpheed-claws
Recommended packages:
  gnome-bluetooth
The following packages will be upgraded:
  nautilus-sendto
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/40.1kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 28633 package `nautilus-sendto':
 `Depends' field, reference to `libbonobo2-0': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

All i can see is that I am running a newer version of libbonobo2-0 but I cannot install any new updates because of this issue

Thanks in advance,

Heath

---

### Post by webofunni on 2007-03-05
try sudo apt-get update && sudo apt-get upgrade

---

### Post by heathguy on 2007-03-05
I tried that and It ran though the packages and then I get this message

You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  nautilus-sendto: Depends: libbonobo2-0 (>= * 2.15.0) but 2.16.0-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.

Thanks for the quick post

---

### Post by heathguy on 2007-03-05
Any other ideas?

---

### Post by webofunni on 2007-03-05
i think you remove libbonobo2-0  and then try to install older one 2.15

---

### Post by heathguy on 2007-03-05
Is this safe to do? How do i know if other programs I have are depending on the newer file.

Also how do i get the full file name of this or is it simply "apt-get remove libbonobo2-0"

---

### Post by heathguy on 2007-03-06
Anyone able to help me with this? I cannot download any new updates because of this dependancy error.

If I run this command:  sudo apt-get remove libbonobo2-0

I get the following output

$ sudo apt-get remove libbonobo2-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  abiword-gnome: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  at-spi: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  brltty-x11: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  bug-buddy: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  compiz-gnome: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  deskbar-applet: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  evince: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  evolution: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  evolution-data-server: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  evolution-exchange: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  evolution-plugins: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  evolution-webcal: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gdesklets: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-control-center: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-cups-manager: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-mag: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-panel: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-pilot: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-pilot-conduits: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-power-manager: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-session: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-spell: Depends: libbonobo2-0 (>= 2.13.0) but it is not going to be installed
  gnome-system-monitor: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-system-tools: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-terminal: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-utils: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gnome-volume-manager: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gthumb: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  gtkhtml3.8: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libatspi1.0-0: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libbonobo2-common: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libbonoboui2-0: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libebook1.2-9: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libecal1.2-7: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libedata-book1.2-2: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libedata-cal1.2-6: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libedataserver1.2-7: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libedataserverui1.2-8: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libeel2-2: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libegroupwise1.2-12: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libexchange-storage1.2-2: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libgdl-1-0: Depends: libbonobo2-0 (>= 2.13.0) but it is not going to be installed
  libgnome-desktop-2: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libgnome-speech3: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libgnome-window-settings1: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libgnome2-0: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libgnome2-perl: Depends: libbonobo2-0 (>= 2.13.0) but it is not going to be installed
  libgnome2-vfs-perl: Depends: libbonobo2-0 (>= 2.13.0) but it is not going to be installed
  libgnome2.0-cil: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libgnomebt0: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libgnomecupsui1.0-1c2a: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libgnomeui-0: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libgtkhtml3.8-15: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libgucharmap5: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  liblpint-bonobo0: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  libpanel-applet2-0: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  mail-notification: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  mail-notification-evolution: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  mdbtools-gmdb: Depends: libbonobo2-0 (>= 2.13.0) but it is not going to be installed
  mysql-query-browser: Depends: libbonobo2-0 (>= 2.13.0) but it is not going to be installed
  nautilus: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  nautilus-cd-burner: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  nautilus-sendto: Depends: libbonobo2-0 (>= * 2.15.0) but it is not going to be installed
  python-at-spi: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  python-gnome2: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  python-gnome2-desktop: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  python-gnome2-extras: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  totem-gstreamer: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  update-notifier: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
  vino: Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Please help!

---

### Post by heathguy on 2007-03-06
I am still struggling with this issue.

I opened up synaptic package manager and did a custom filter search for broken dependancies and found that nautilus-sendto was the only package with a broken dependancy

when trying to remove this (Mark for removal or complete removal -> apply) gives the following message:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 28633 package `nautilus-sendto':
 `Depends' field, reference to `libbonobo2-0': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

what does it mean **version contains `**

---

### Post by OBnascar on 2007-03-06
heathguy, try replacing your repositories [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.psychocats.net/ubuntu/sources.php")

Then try to update & upgrade again.

---

### Post by heathguy on 2007-03-06
Okay I backed up and used that sources.list and ran update just fine.

Then I tried this:

# sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have unmet dependencies:
  nautilus-sendto: Depends: libbonobo2-0 (>= * 2.15.0) but 2.16.0-0ubuntu1 is installed.
#

GAH I'm confused... why can't i just delete this nautilus-sendto program!! I tried in synaptic package manager and I cannot remove it :(

---

### Post by heathguy on 2007-03-06
Any other suggestions?

---

### Post by heathguy on 2007-03-07
Bump... I really would like this resolved..

I tried this:
```

# apt-get -f remove nautilus-sendto
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nautilus-sendto
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nautilus-sendto
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 684kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 28633 package `nautilus-sendto':
 `Depends' field, reference to `libbonobo2-0': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by heathguy on 2007-03-07
I think this may be a bug...

I checked the file /var/lib/dpkg/status and went to line 28633 and saw this:
 **libbonobo2-0 (>* 2.15.0)**

And then i changed it to

**libbonobo2-0 (>= 2.15.0)**

Could this be a bug where the * gets put in instead of an = sign?

After changing this I am able to update and upgrade my system!!

Thanks for all the replies.

---

