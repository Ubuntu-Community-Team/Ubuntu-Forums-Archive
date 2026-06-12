---
title: "iPhone + Ubuntu"
date: 2013-06-26
forum: Apple Hardware Users
---

### Post by staim on 2013-06-26
Guys, is anybody using iPhone with Ubuntu desktop? I need your experience.


I'm using iPhone5(iOS6) + Ubuntu 12.04: device is detected out of the box using libimobiledevice(i think so) and mounts two gvfs-drives: "iPhone Documents" and "iPhone". First one contains installed application data (in a normal human-readable format), second one -  internal iTunes data: photos and pictures, that can be downloaded, but not uploaded, music and ringtones renamed in a strange way, and also settings files and databases of itunes itself. 


There are following troubles: 


1) *Uploading files to non-Apple Applications* -  there is "iPhone Documents" mount, that allows accessing data in a proper way. But the problem appears when I copy big files (or a pack of small files) to devices using Nautilus i'm getting error: "Wrong data recievd from Apple File Control"  and after this iPhone is not acessible anymore until reconnected. While I'm using Midnight Commander and access gvfs directly (using ~/.gvfs/...) there is no such problem.


2) *Music Uploading* - libgpod-based solutions do not work with >=iOS5. I've tried to investigate this by hand: there is a file /iTunes_control/iTunes/MediaLibrary.sqlitedb, that is actually an SQLite 3 database and accessible by any SQLite 3 client. I was able to add my music file by hand, and iPhone sees it, but do not play. I cannot understand what I'm doing wrong. 


3) *Ringtones* - The same **** as Music: I have uploaded file(Audacity converted to m4r) and added it to Ringtones.plist(which is converted by plutil to plaintext XML), iPhone sees the file, even allows play it while selecting, but when I try to assign it to contact it is reverted back to default Marimba ringtone (this does not happen with iTunes-uploaded Ringtones).

4) *Images and Videos Upload* - there is DCIM folder in iPhone, but when I add pictures and video to it, iPhone does not see it in Gallery.

---

