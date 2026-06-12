---
title: "Cannot connect to repositories"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by mavuashire on 2007-03-02
Can some one help me please. 

I have installed ubuntu 6.10 and when I try to download the packages my computer would not connect to the repositories. It times out while trying to connect. I can browse internet and everything seems to be working fine. I have tried to edit the source files but still there is no improvement. I have tried to use both the terminal and the synaptics.

I have tried almost all the help related to my problem but it did not help.

You can email me at [email]keolus@hotmail.com[/email]

---

### Post by taurus on 2007-03-02
What are the outputs of these two commands from a terminal then.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Iesu on 2007-03-03
I posted earlier today on a similar problem. This problem seems to be so common that I can't believe there isn't a heap of extremely clear solutions. I don't know the permanent fix for the problem but pinging your repos first allows aptitude to connect to them. I have no idea why. I made a basic script to ping all my repos so I could update.
```
#!/bin/bash

ping archive.ubuntu.com -c 1
ping security.ubuntu.com -c 1
ping kubuntu.org -c 1
ping archive.canonical.com -c 1
ping seveas.imbrandon.com -c 1
ping ubuntu.beryl-project.org -c 1
ping wine.budgetdedicated.com -c 1
ping 3v1n0.tuxfamily.org -c 1
ping home.eng.iastate.edu -c 1
```
Updating as I write this so I'm not even certain it will work still when it gets to the latter repos but it does fix it for a little bit.
PS. If any experts see this post could you please tell us why ping connects but wget, apt-get, and aptitude doesn't? And why ping allows them to connect?

---

### Post by konungursvia on 2007-03-03
I haven't been able to connect to archive.ubuntu.com for days... it seems to be down?

---

### Post by Kateikyoushi on 2007-03-03
No it is not down, I saw 2 solutions to this, might be different reason why they actually couldn't connect but does not happen to me so can't figure it out myself.

One way was to change the server to a local one, for example .ca , .au whatever is close to you.

The other is to change the http to ftp in the /etc/apt/sources.list.

---

### Post by konungursvia on 2007-03-03
Thanks kateikyoushi-san, I changed the problematic addresses to ftp and they work now (edit: some of them connect, others still do not...)

---

### Post by mavuashire on 2007-03-04
I've changed the http to ftp in sources.list. Some of the things com thru yet it fails to download others. The synapic still doesn't work

here are some of the results I get after I ping the repositories: 

temo@temo:~$ sudo apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
30% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubu

it times out here or will go down at times and say some packages were not downloaded

then

temo@temo:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
  app-install-data-commercial avahi-daemon bind9-host capplets-data dbus
  dbus-1-utils dnsutils ekiga evince firefox firefox-gnome-support gdm gimp
  gimp-data gimp-python gnome-applets gnome-applets-data gnome-control-center
  gnome-games gnome-games-data gnome-netstatus-applet gnome-panel
  gnome-panel-data gnome-system-tools gnupg info language-pack-en
  language-pack-gnome-en libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-core4 libavahi-glib1 libbind9-0 libc6 libc6-dev
  libc6-i686 libdbus-1-3 libdns21 libgimp2.0 libgnome-window-settings1
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgsf-1-114
  libgsf-1-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop2-7
  libgtop2-common libisc11 libisccc0 libisccfg1 libkrb53 liblwres9 libmagick9
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil
  libmono-system-data1.0-cil libmono-system-web1.0-cil libmono-system1.0-cil
  libmono0 libmono1.0-cil libnspr4 libnss3 libpanel-applet2-0 libpng12-0
  libpoppler1 libpoppler1-glib libsmbclient libsoup2.2-8 libtotem-plparser1
  libvolumeid0 linux-generic linux-headers-2.6.17-10
  linux-headers-2.6.17-10-generic linux-image-2.6.17-10-386
  linux-image-2.6.17-10-generic linux-libc-dev
  linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-common
  mono-common mono-gac mono-jit mono-runtime openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-math openoffice.org-style-default
  openoffice.org-style-industrial openoffice.org-writer poppler-utils
  python-uno samba-common screen slocate smbclient system-tools-backends tar
  totem totem-gstreamer totem-mozilla ttf-opensymbol tzdata ubuntu-docs udev
  vino volumeid w3m x11-common xbase-clients xorg xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-video-all xutils
134 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 226MB of archives.
After unpacking 5677kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tar linux-libc-dev libc6-dev libc6 libc6-i686 x11-common language-pack-en
  language-pack-gnome-en openoffice.org-style-industrial
  openoffice.org-style-default openoffice.org-calc python-uno
  openoffice.org-writer openoffice.org-impress openoffice.org-draw
  openoffice.org-java-common openoffice.org-base libdbus-1-3 libgtk2.0-common
  libpng12-0 libgtk2.0-bin libgtk2.0-0 openoffice.org-gtk libavahi-common-data
  libavahi-common3 libavahi-client3 libavahi-glib1 libkrb53 dbus libsmbclient
  libgnomevfs2-extra libgnomevfs2-0 libgnomevfs2-common openoffice.org-gnome
  openoffice.org-evolution openoffice.org-math openoffice.org ttf-opensymbol
  openoffice.org-core openoffice.org-common screen xserver-xorg-video-all
  xserver-xorg-input-all xserver-xorg-core xutils xbase-clients xserver-xorg
  gnupg libvolumeid0 udev volumeid tzdata libisc11 libdns21 libisccc0
  libisccfg1 libbind9-0 liblwres9 bind9-host dnsutils info w3m
  app-install-data-commercial libavahi-core4 avahi-daemon gnome-control-center
  libgnome-window-settings1 capplets-data dbus-1-utils ekiga libpoppler1-glib
  libpoppler1 evince firefox-gnome-support libnspr4 libnss3 firefox gdm gimp
  gimp-data libgimp2.0 gimp-python libgtop2-common libgtop2-7
  libpanel-applet2-0 gnome-applets gnome-applets-data gnome-panel
  gnome-panel-data gnome-games gnome-games-data gnome-netstatus-applet
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomevfs2-bin
  libgsf-1-common libgsf-1-114 libmagick9 mono-runtime mono-gac mono-jit
  mono-common libmono0 libmono-corlib1.0-cil libmono-cairo1.0-cil
  libmono-system1.0-cil libmono-security1.0-cil libmono-data-tds1.0-cil
  libmono-sharpzip0.84-cil libmono-system-data1.0-cil libmono-sqlite1.0-cil
  libmono-system-web1.0-cil libmono1.0-cil libsoup2.2-8 libtotem-plparser1
  linux-generic linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic
  linux-image-2.6.17-10-386 linux-image-2.6.17-10-generic
  linux-restricted-modules-common linux-restricted-modules-2.6.17-10-generic
  poppler-utils smbclient samba-common gnome-system-tools
  system-tools-backends totem-gstreamer totem totem-mozilla ubuntu-docs vino
  xorg slocate
Install these packages without verification [y/N]? y
0% [Connecting to security.ubuntu.com (1.0.0.0)] [Connecting to au.archive.ubun

AND THEN IT FAILS AGAIN

---

### Post by sauravbhaumik on 2007-03-04
try this:
```
sudo apt-get install axel
```

axel is a very small program. See if you can get this small size out of the repository.

or else, try this:
```
sudo apt-get install xcdroast
```

---

### Post by mavuashire on 2007-03-04
I have tried sudo apt-get install axel

it worked but I had to ping the site first for it to work

results:
temo@temo:~$ sudo apt-get install axel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mesa-common-dev libglu1-mesa-dev libgl1-mesa-dev
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  axel
0 upgraded, 1 newly installed, 0 to remove and 137 not upgraded.
Need to get 34.7kB of archives.
After unpacking 172kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  axel
Install these packages without verification [y/N]? y
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe axel 1.0b-1.1 [34.7kB]
Fetched 34.7kB in 0s (35.6kB/s)
Selecting previously deselected package axel.
(Reading database ... 91899 files and directories currently installed.)
Unpacking axel (from .../axel_1.0b-1.1_i386.deb) ...
Setting up axel (1.0b-1.1) ...

---

### Post by mrmonday on 2007-03-04
I had this problem a while back. I have posted the solution a few times. Have a look at the 8th post [here]("http://www.ubuntuforums.org/showthread.php?t=358749").

Does this help? It has worked for everyone I know.

---

### Post by mavuashire on 2007-03-05
Thanks very much I can now download and update some stuff.

I used the openDNS and it worked.

Thanks for your help everyone.

---

