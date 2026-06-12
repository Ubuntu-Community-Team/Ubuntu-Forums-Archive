---
title: "somethings wrong with aptitude!"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-10-05
It happened again the last time was when I used Synaptic to automatically uninstall LAMP with the automatic taskcel something something.  This time I just used 
aptitude 
and searched for emacs to install I selected it by doing
+
g
g

Then it started to uninstall a bunch of unrelated things I saw some MySQL packages flash by so I 
Ctrl+C
before any more damage would occur.

I don't know how to dig up the relevant error messages for you.  You want them?
I'm starting to be afraid of using programs like
**taskcel and aptitude on Ubuntu Feisty nowadays**.  Aptitude seems so simple and easy on Debian but it's unpredictable on Ubuntu. :(

---

### Post by Dr Small on 2007-10-05
Just use apt-get... :|

---

### Post by jingo811 on 2007-10-06
Guess you're right about not going near taskcel and aptitude interfaces ever again.  But I'm kind of married to aptitude :)  We use that a lot at school on our Debian systems.  So I kind of like to be able to test it at home on my Ubuntu also sometimes.

Anyways I think I found the evidence I need to show you what happened in aptitude last night.
I just wanted to install what seemed to be emacs but it said emacs-extra or something and then it just automatically started uninstalling stuff that I didn't choose previously.
Maybe I'm using the aptitude interface wrong, maybe I accidentally pressed some unknown key that automatically de-selects packages.....:confused:
Maybe I've got some sort of viruses in my taskcel and aptitude interface programs?

[SIZE="2"]-rw-r--r-- 1 root  root     449 2007-10-06 00:31 aptitude.1.gz[/SIZE]
[SIZE="4"]**/var/log/aptitude.1.gz**[/SIZE]

> 
Aptitude 0.4.4: log report
Sat, Oct  6 2007 00:31:24 +0200

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 6 packages, and remove 18 packages.
27.7MB of disk space will be freed
===============================================================================
[INSTALL, DEPENDENCIES] emacs21
[INSTALL, DEPENDENCIES] emacs21-bin-common
[INSTALL, DEPENDENCIES] emacs21-common
[INSTALL, DEPENDENCIES] emacsen-common
[INSTALL, DEPENDENCIES] xaw3dg
[HOLD] moblock-nfq
[INSTALL] emacs-extra
[REMOVE] kdelibs4c2a
[REMOVE] ktorrent
[REMOVE] libarts1c2a
[REMOVE] libavahi-qt3-1
[REMOVE] libcairomm-1.0-1
[REMOVE] libglibmm-2.4-1c2a
[REMOVE] libgmp3c2
[REMOVE] libgtkhtml3.8-15
[REMOVE] libgtkmm-2.4-1c2a
[REMOVE] liblua50
[REMOVE] liblualib50
[REMOVE] libopenexr2c2a
[REMOVE] mysql-admin
[REMOVE] mysql-admin-common
[REMOVE] mysql-query-browser
[REMOVE] mysql-query-browser-common
[REMOVE] php-pear
[REMOVE] php5-cli
===============================================================================

Log complete.

---

