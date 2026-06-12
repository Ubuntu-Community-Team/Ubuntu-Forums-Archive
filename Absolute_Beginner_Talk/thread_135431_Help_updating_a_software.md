---
title: "Help updating a software"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by ubuntu27 on 2006-02-23
Good Morning/afternoon/evening.
I would like to know how to update an existing software that was not installed using apt.

Well, the software that I want update is the official BitTorrent.

I installed BitTorrent using  sudo dpkg -i filename.deb

But, I cannot install the new version, this is what I get:

```
Ubuntu27@heaven:~$ sudo dpkg -i bittorrent-4.4.0.linux_i686-2_all_python2.4.deb
Password:
(Reading database ... 94540 files and directories currently installed.)
Unpacking bittorrent-4.4.0.linux (from bittorrent-4.4.0.linux_i686-2_all_python2.4.deb) ...
dpkg: error processing bittorrent-4.4.0.linux_i686-2_all_python2.4.deb (--install):
 trying to overwrite `/usr/share/locale/af/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 bittorrent-4.4.0.linux_i686-2_all_python2.4.deb
Ubuntu27@heaven:~$
```

Gotta learn more about Linux :D

---

### Post by shams2 on 2006-02-23
first remove the old bittorrent with:
aptitude purge bittorrent
then install the new when with dpkg.

---

### Post by ubuntu27 on 2006-02-23
[QUOTE=shams2]first remove the old bittorrent with:
aptitude purge bittorrent
then install the new when with dpkg.[/QUOTE]

Thanks for the reply :)  SHAMAN.

Well, I've removed BiTorrent, and then tried to install Bittorrent, but there were some error:

```
Ubuntu27@heaven:~$ aptitude purge bittorrent
E: /home/ghost/.aptitude/config - Unable to open %s for writing (13 Permission d enied)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

```
Ubuntu27@heaven:~$ sudo aptitute purge bittorrent
Password:
sudo: aptitute: command not found
ghost@heaven:~$ sudo aptitude purge bittorrent
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
The following packages have been kept back:
  gaim linux-image-2.6.12-10-386
The following packages will be REMOVED:
  bittorrent
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 94539 files and directories currently installed.)
Removing bittorrent ...
Purging configuration files for bittorrent ...
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
ghost@heaven:~$ sudo dpkg -i bittorrent-4.4.0.linux_i686-2_all_python2.4.deb
(Reading database ... 94540 files and directories currently installed.)
Unpacking bittorrent-4.4.0.linux (from bittorrent-4.4.0.linux_i686-2_all_python2 .4.deb) ...
dpkg: error processing bittorrent-4.4.0.linux_i686-2_all_python2.4.deb (--instal l):
 trying to overwrite `/usr/share/locale/af/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 bittorrent-4.4.0.linux_i686-2_all_python2.4.deb
```

What should I do? :-?

---

### Post by ubuntu27 on 2006-02-24
***Bump!!***  [WHo invented this word?]

Anyway, update:   Even though I did aptitude purge bittorrent, Bittorrent is still there, I can still run it from the launcher :(

---

### Post by shams2 on 2006-02-24
try the force command for installation:
dpkg -i --force-overwrite bittorrent-4.4.0.linux_i686-2_all_python2.4.deb
if that failed then try:
dpkg -i --force-all bittorrent-4.4.0.linux_i686-2_all_python2.4.deb

---

### Post by Madpilot on 2006-02-24
try "sudo aptitude <whatever>" - just like apt-get & dpkg, aptitude must be run with admin privs.

If you look at one of the error messages you posted, it actually asks "Are you root?" at the end of the error msg - which in Ubuntu terms means "Did you use sudo?"

EDIT: nevermind, I see you tried that, and got another error message that makes much less sense. Never mind...

You do know that gnome-bitttorrent is included in Ubuntu by default, though? Go **Applications-->Internet-->BitTorrent** or just click on a .torrent file in Firefox.

---

### Post by ubuntu27 on 2006-02-24
> **Madpilot]try "sudo aptitude <whatever>" - just like apt-get & dpkg, aptitude must be run with admin privs.

If you look at one of the error messages you posted, it actually asks "Are you root?" at the end of the error msg - which in Ubuntu terms means "Did you use sudo?"

EDIT: nevermind, I see you tried that, and got another error message that makes much less sense. Never mind...

You do know that gnome-bitttorrent is included in Ubuntu by default, though? Go **Applications-->Internet-->BitTorrent** or just click on a .torrent file in Firefox.[/QUOTE]

Well, I replaced GnomeTorrent with the Official bittorrent  said:**
> try the force command for installation:
dpkg -i --force-overwrite bittorrent-4.4.0.linux_i686-2_all_python2.4.deb
if that failed then try:
dpkg -i --force-all bittorrent-4.4.0.linux_i686-2_all_python2.4.deb

Alright! Thanks! It seems to work since when I launch BitTorrent and click on Help/About, it shows the updated 4.4.0 version.


I got a werid message though:


```
also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/it/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/ja/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/ko/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/nb_NO/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/nl/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/pl/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/pt/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/pt_BR/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/ro/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/ru/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/sk/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/sl/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/sv/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/tr/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/vi/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/zh_CN/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale/zh_TW/LC_MESSAGES/bittorrent.mo', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Choker.py', wh ich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/ClientIdentifi er.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Connecter.py',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/ConvertedMetai nfo.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/CurrentRateMea sure.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Desktop.py', w hich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Downloader.py' , which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/DownloaderFeed back.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Encoder.py', w hich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/GUI.py', which  is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/GetTorrent.py' , which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/HTTPHandler.py ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/LaunchPath.py' , which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/NatCheck.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/NewVersion.py' , which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/PiecePicker.py ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/RateLimiter.py ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/RateMeasure.py ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/RawServer.py',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/RawServer_magi c.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/RawServer_twis ted.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Rerequester.py ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Storage.py', w hich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/StorageWrapper .py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/TorrentQueue.p y', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Uploader.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/__init__.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/bencode.py', w hich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/bitfield.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/btformats.py',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/configfile.py' , which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/defaultargs.py ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/defer.py', whi ch is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/download.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/launchmanycore .py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/makemetafile.p y', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/obsoletepython support.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/parseargs.py',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/parsedir.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/platform.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/prefs.py', whi ch is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/selectpoll.py' , which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/track.py', whi ch is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/zurllib.py', w hich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Choker.pyc', w hich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/ClientIdentifi er.pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Connecter.pyc' , which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/ConvertedMetai nfo.pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/CurrentRateMea sure.pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Desktop.pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Downloader.pyc ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/DownloaderFeed back.pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Encoder.pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/GUI.pyc', whic h is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/GetTorrent.pyc ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/HTTPHandler.py c', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/LaunchPath.pyc ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/NatCheck.pyc',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/NewVersion.pyc ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/PiecePicker.py c', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/RateLimiter.py c', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/RateMeasure.py c', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/RawServer.pyc' , which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/RawServer_magi c.pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/RawServer_twis ted.pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Rerequester.py c', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Storage.pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/StorageWrapper .pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/TorrentQueue.p yc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Uploader.pyc',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/__init__.pyc',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/bencode.pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/bitfield.pyc',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/btformats.pyc' , which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/configfile.pyc ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/defaultargs.py c', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/defer.pyc', wh ich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/download.pyc',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/launchmanycore .pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/makemetafile.p yc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/obsoletepython support.pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/parseargs.pyc' , which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/parsedir.pyc',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/platform.pyc',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/prefs.pyc', wh ich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/selectpoll.pyc ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/track.pyc', wh ich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/zurllib.pyc', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/KRateLimiter.py' , which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/__init__.py', wh ich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/actions.py', whi ch is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/cache.py', which  is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/const.py', which  is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/hammerlock.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/inserter.py', wh ich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/khash.py', which  is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/khashmir.py', wh ich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/knet.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/knode.py', which  is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/krpc.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/kstore.py', whic h is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/ktable.py', whic h is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/node.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/setup.py', which  is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/test.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/test_khashmir.py ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/test_krpc.py', w hich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/test_kstore.py',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/unet.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/util.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/utkhashmir.py', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/KRateLimiter.pyc ', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/__init__.pyc', w hich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/actions.pyc', wh ich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/cache.pyc', whic h is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/const.pyc', whic h is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/hammerlock.pyc',  which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/inserter.pyc', w hich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/khash.pyc', whic h is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/khashmir.pyc', w hich is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/knet.pyc', which  is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/knode.pyc', whic h is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/krpc.pyc', which  is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/kstore.pyc', whi ch is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/ktable.pyc', whi ch is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/python2.4/site-packages/khashmir/node.pyc', which  is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/bin/bittorrent-console', which is also in package bit torrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/bin/maketorrent', which is also in package bittorrent -4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/bin/maketorrent-console', which is also in package bi ttorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/bin/launchmany-curses', which is also in package bitt orrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/bin/launchmany-console', which is also in package bit torrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/bin/changetracker-console', which is also in package bittorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/bin/torrentinfo-console', which is also in package bi ttorrent-4.2.2.linux
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/bin/bittorrent-tracker', which is also in package bit torrent-4.2.2.linux
Setting up bittorrent-4.4.0.linux (i686-2) ...
Ubuntu27@heaven:~$ 
```

I guess it is normal... :D

Thank you guys for you help!!

---

### Post by ericsp on 2006-10-20
> **ubuntu27 said:**
> Well, I replaced GnomeTorrent with the Official bittorrent ;)


Is there a .deb available for easy installation of GnomeTorrent? The tar.gz that I downloaded did not include instructions how to install.

Eric

---

### Post by ubuntu27 on 2006-10-22
> **ericsp said:**
> Is there a .deb available for easy installation of GnomeTorrent? The tar.gz that I downloaded did not include instructions how to install.

Eric

The GnomeTorrent comes with Ubuntu by default. You just don't see it under the Application menu in Dapper (you can see it in Breezy).

If you open  a *.torrent file it will download the file with Gnome-torrent.

---

