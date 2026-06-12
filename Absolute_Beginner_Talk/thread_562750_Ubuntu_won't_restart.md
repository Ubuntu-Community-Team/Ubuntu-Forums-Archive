---
title: "Ubuntu won't restart"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by nolane on 2007-09-29
Hi all

I've been running Ubuntu 7.04 for a few days now; I am a _complete_ beginner with it. Earlier I ran Package Manager and got all the latest updates.  Now, when I'm in GNOME and click "restart", it locks up.  I get the Ubuntu logo and the status bar goes DOWN to 0 like it used to, however that's where it stops.  The computer never gets that extra command telling it to finish restarting.  I can physically turn the computer off and restart it, that seems to work fine.

My guess is one of the updates from Package Manager hosed something.  However...

1. How do i find out *what* caused this problem?
2. How do i undo that change?

Thanks for your time.

--nolan

PS. I'm not a _total_ computer novice; I've used Windows for a number of years. Is there a book/url you'd recommend for those of us making the transition?

---

### Post by Bothered on 2007-09-29
Did you update using synaptic? If you did, you can check the log to see what was updated, which might give you a clue to the problem:

1. Press Alt F2
2. Type "gksudo gnome-terminal" and click "Run"
3. Enter "cd /root/.synaptic/log"
4. Enter "cat *" and look towards the end of the log for the last updates. Copy those here.
5. Make sure you exit the terminal, as the terminal has been run with root privileges (type "exit")

---

### Post by nolane on 2007-09-29
Thanks for the reply.  Here are the last few entries in that log file:

Installed the following packages:
flashplugin-nonfree (9.0.48.0.0ubuntu1~7.04.1)
Commit Log for Fri Sep 28 00:27:33 2007


Upgraded the following packages:
app-install-data (0.3.30) to 0.3.31
app-install-data-commercial (7) to 7.3
apport (0.76) to 0.76.1
apport-gtk (0.76) to 0.76.1
bind9-host (1:9.3.4-2ubuntu2) to 1:9.3.4-2ubuntu2.1
capplets-data (1:2.18.1-0ubuntu2) to 1:2.18.1-0ubuntu2.1
dbus (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
dbus-1-utils (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
dnsutils (1:9.3.4-2ubuntu2) to 1:9.3.4-2ubuntu2.1
evolution-data-server (1.10.1-0ubuntu1) to 1.10.1-0ubuntu1.1
evolution-data-server-common (1.10.1-0ubuntu1) to 1.10.1-0ubuntu1.1
file (4.19-1ubuntu2) to 4.19-1ubuntu2.1
firefox (2.0.0.3+1-0ubuntu2) to 2.0.0.6+1-0ubuntu1
firefox-gnome-support (2.0.0.3+1-0ubuntu2) to 2.0.0.6+1-0ubuntu1
gimp (2.2.13-1ubuntu4) to 2.2.13-1ubuntu4.3
gimp-data (2.2.13-1ubuntu4) to 2.2.13-1ubuntu4.3
gimp-python (2.2.13-1ubuntu4) to 2.2.13-1ubuntu4.3
gnome-app-install (0.3.30) to 0.3.31
gnome-btdownload (0.0.25-1ubuntu1) to 0.0.28-1~feisty1
gnome-control-center (1:2.18.1-0ubuntu2) to 1:2.18.1-0ubuntu2.1
gnome-panel (1:2.18.1-0ubuntu3) to 1:2.18.1-0ubuntu3.1
gnome-panel-data (1:2.18.1-0ubuntu3) to 1:2.18.1-0ubuntu3.1
gnupg (1.4.6-1ubuntu2) to 1.4.6-2ubuntu3~feisty1
gpgv (1.4.6-1ubuntu2) to 1.4.6-2ubuntu3~feisty1
hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hwdb-client-common (0.6.10) to 0.6.10.1
hwdb-client-gnome (0.6.10) to 0.6.10.1
iptables (1.3.6.0debian1-5ubuntu2) to 1.3.6.0debian1-5ubuntu2.1
language-pack-ar (1:7.04+20070412) to 1:7.04+20070601
language-pack-cs (1:7.04+20070412) to 1:7.04+20070601
language-pack-de (1:7.04+20070412) to 1:7.04+20070601
language-pack-el (1:7.04+20070412) to 1:7.04+20070601
language-pack-en (1:7.04+20070412) to 1:7.04+20070601
language-pack-es (1:7.04+20070412) to 1:7.04+20070601
language-pack-fi (1:7.04+20070412) to 1:7.04+20070601
language-pack-fr (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-ar (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-cs (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-de (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-el (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-en (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-es (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-fi (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-fr (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-he (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-hu (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-it (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-ja (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-ko (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-nb (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-nl (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-nn (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-no (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-pl (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-pt (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-ru (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-sv (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-tr (1:7.04+20070412) to 1:7.04+20070601
language-pack-gnome-zh (1:7.04+20070412) to 1:7.04+20070601
language-pack-he (1:7.04+20070412) to 1:7.04+20070601
language-pack-hu (1:7.04+20070412) to 1:7.04+20070601
language-pack-it (1:7.04+20070412) to 1:7.04+20070601
language-pack-ja (1:7.04+20070412) to 1:7.04+20070601
language-pack-ko (1:7.04+20070412) to 1:7.04+20070601
language-pack-nb (1:7.04+20070412) to 1:7.04+20070601
language-pack-nl (1:7.04+20070412) to 1:7.04+20070601
language-pack-nn (1:7.04+20070412) to 1:7.04+20070601
language-pack-no (1:7.04+20070412) to 1:7.04+20070601
language-pack-pl (1:7.04+20070412) to 1:7.04+20070601
language-pack-pt (1:7.04+20070412) to 1:7.04+20070601
language-pack-ru (1:7.04+20070412) to 1:7.04+20070601
language-pack-sv (1:7.04+20070412) to 1:7.04+20070601
language-pack-tr (1:7.04+20070412) to 1:7.04+20070601
language-pack-zh (1:7.04+20070412) to 1:7.04+20070601
lftp (3.5.6-1build1) to 3.5.11-1~feisty1
libbind9-0 (1:9.3.4-2ubuntu2) to 1:9.3.4-2ubuntu2.1
libcamel1.2-10 (1.10.1-0ubuntu1) to 1.10.1-0ubuntu1.1
libcurl3 (7.15.5-1ubuntu2) to 7.15.5-1ubuntu2.1
libdbus-1-3 (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libdns22 (1:9.3.4-2ubuntu2) to 1:9.3.4-2ubuntu2.1
libebook1.2-9 (1.10.1-0ubuntu1) to 1.10.1-0ubuntu1.1
libecal1.2-7 (1.10.1-0ubuntu1) to 1.10.1-0ubuntu1.1
libedata-book1.2-2 (1.10.1-0ubuntu1) to 1.10.1-0ubuntu1.1
libedata-cal1.2-6 (1.10.1-0ubuntu1) to 1.10.1-0ubuntu1.1
libedataserver1.2-9 (1.10.1-0ubuntu1) to 1.10.1-0ubuntu1.1
libedataserverui1.2-8 (1.10.1-0ubuntu1) to 1.10.1-0ubuntu1.1
libegroupwise1.2-13 (1.10.1-0ubuntu1) to 1.10.1-0ubuntu1.1
libexchange-storage1.2-3 (1.10.1-0ubuntu1) to 1.10.1-0ubuntu1.1
libexif12 (0.6.13-5build1) to 0.6.13-5ubuntu0.2
libfreetype6 (2.2.1-5ubuntu1) to 2.2.1-5ubuntu1.1
libgimp2.0 (2.2.13-1ubuntu4) to 2.2.13-1ubuntu4.3
libgl1-mesa-dri (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libgl1-mesa-glx (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libglu1-mesa (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libgnome-window-settings1 (1:2.18.1-0ubuntu2) to 1:2.18.1-0ubuntu2.1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libisc11 (1:9.3.4-2ubuntu2) to 1:9.3.4-2ubuntu2.1
libisccc0 (1:9.3.4-2ubuntu2) to 1:9.3.4-2ubuntu2.1
libisccfg1 (1:9.3.4-2ubuntu2) to 1:9.3.4-2ubuntu2.1
libjasper-1.701-1 (1.701.0-2) to 1.701.0-2ubuntu0.7.04
libkrb53 (1.4.4-5ubuntu3) to 1.4.4-5ubuntu3.3
liblwres9 (1:9.3.4-2ubuntu2) to 1:9.3.4-2ubuntu2.1
libmagic1 (4.19-1ubuntu2) to 4.19-1ubuntu2.1
libmagick9 (7:6.2.4.5.dfsg1-0.14) to 7:6.2.4.5.dfsg1-0.14ubuntu0.1
libmetacity0 (1:2.18.2-0ubuntu1) to 1:2.18.2-0ubuntu1.1
libnspr4 (2:1.firefox2.0.0.3+1-0ubuntu2) to 2:1.firefox2.0.0.6+1-0ubuntu1
libnss3 (2:1.firefox2.0.0.3+1-0ubuntu2) to 2:1.firefox2.0.0.6+1-0ubuntu1
libpanel-applet2-0 (1:2.18.1-0ubuntu3) to 1:2.18.1-0ubuntu3.1
libpng12-0 (1.2.15~beta5-1) to 1.2.15~beta5-1ubuntu1
libpoppler1 (0.5.4-0ubuntu8) to 0.5.4-0ubuntu8.1
libpoppler1-glib (0.5.4-0ubuntu8) to 0.5.4-0ubuntu8.1
libslab0 (1:2.18.1-0ubuntu2) to 1:2.18.1-0ubuntu2.1
libsmbclient (3.0.24-2ubuntu1) to 3.0.24-2ubuntu1.2
libvorbis0a (1.1.2.dfsg-1.2) to 1.1.2.dfsg-1.2ubuntu2
libvorbisenc2 (1.1.2.dfsg-1.2) to 1.1.2.dfsg-1.2ubuntu2
libvorbisfile3 (1.1.2.dfsg-1.2) to 1.1.2.dfsg-1.2ubuntu2
libwrap0 (7.6.dbs-11build1) to 7.6.dbs-11ubuntu0.1
linux-generic (2.6.20.15.14) to 2.6.20.16.28.1
linux-headers-2.6.20-16 (2.6.20-16.29) to 2.6.20-16.32
linux-headers-2.6.20-16-generic (2.6.20-16.29) to 2.6.20-16.32
linux-headers-generic (2.6.20.15.14) to 2.6.20.16.28.1
linux-image-2.6.20-16-generic (2.6.20-16.29) to 2.6.20-16.32
linux-restricted-modules-2.6.20-16-generic (2.6.20.5-16.28) to 2.6.20.5-16.29
linux-restricted-modules-common (2.6.20.5-15.20) to 2.6.20.5-16.29
mesa-utils (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
metacity (1:2.18.2-0ubuntu1) to 1:2.18.2-0ubuntu1.1
metacity-common (1:2.18.2-0ubuntu1) to 1:2.18.2-0ubuntu1.1
openoffice.org (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-base (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-calc (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-common (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-core (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-draw (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-evolution (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-filter-mobiledev (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-gnome (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-gtk (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-impress (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-java-common (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-math (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-style-human (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
openoffice.org-writer (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
poppler-utils (0.5.4-0ubuntu8) to 0.5.4-0ubuntu8.1
python (2.5.1~rc1-0ubuntu3) to 2.5.1-0ubuntu3
python-apport (0.76) to 0.76.1
python-gdbm (2.5-0ubuntu1) to 2.5.1-0ubuntu1
python-launchpad-bugs (0.1.13) to 0.1.13.2
python-minimal (2.5.1~rc1-0ubuntu3) to 2.5.1-0ubuntu3
python-problem-report (0.76) to 0.76.1
python-uno (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
python2.5 (2.5.1~rc1-0ubuntu3) to 2.5.1-0ubuntu1
python2.5-minimal (2.5.1~rc1-0ubuntu3) to 2.5.1-0ubuntu1
rdesktop (1.5.0-1build1) to 1.5.0-1ubuntu1
rsync (2.6.9-3ubuntu1) to 2.6.9-3ubuntu1.1
samba-common (3.0.24-2ubuntu1) to 3.0.24-2ubuntu1.2
smbclient (3.0.24-2ubuntu1) to 3.0.24-2ubuntu1.2
tar (1.16-2) to 1.16-2ubuntu0.1
tcpdump (3.9.5-2) to 3.9.5-2ubuntu1
ttf-opensymbol (2.2.0-1ubuntu3) to 2.2.0-1ubuntu4
tzdata (2007b-0ubuntu1) to 2007f-0ubuntu0.7.4
unattended-upgrades (0.22ubuntu2) to 0.23ubuntu3
update-manager (1:0.59.19) to 1:0.59.25
update-manager-core (1:0.59.19) to 1:0.59.25
vim-common (1:7.0-164+1ubuntu7) to 1:7.0-164+1ubuntu7.2
vim-tiny (1:7.0-164+1ubuntu7) to 1:7.0-164+1ubuntu7.2
xscreensaver-data (4.24-5ubuntu2) to 4.24-5ubuntu2.1
xscreensaver-gl (4.24-5ubuntu2) to 4.24-5ubuntu2.1

Installed the following packages:
hal-info (20070402-1ubuntu1~feisty1)

Does anything pop out as a possible culprit?

Thanks again for your time.

-nolan

---

### Post by Bothered on 2007-09-30
It could be the kernel update. You could try booting using an older kernel version (should still be on your grub menu unless you removed it) and see if it shuts down cleanly.

---

### Post by nowshining on 2007-09-30
for the transition thing - depends on how u used windows - if u tweaked it to death or tweak it some then your transition with / to ubuntu will be minimal and nothing will be out of place and all will be peaceful - other words - a peaceful transition will occur - if you just kept the windows defaults and only installed here and there - then well u'll have a tougher time  :)

---

