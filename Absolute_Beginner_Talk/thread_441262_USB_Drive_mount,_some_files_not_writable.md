---
title: "USB Drive mount, some files not writable?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by guice on 2007-05-12
I've setup my USB drive to mount under /media/iomega with the following options from fstab:

```
/dev/usbdevices/iomega     /media/iomega        vfat    rw,gid=33,uid=1000,utf8,umask=0027      0       0
```

However, for some reason, I have files that are not writable:
```

drwxr-x---  4 guice www-data    32768 2007-04-13 01:49 backup
-rwxr-x---  1 guice www-data    97347 2007-04-13 01:49 before.jpg
-rwxr-x---  1 guice www-data  3270262 2007-04-13 01:49 before.psd
-r-xr-x---  1 guice www-data   167418 2007-04-13 01:49 bookmarks1.html
-r-xr-x---  1 guice www-data    82672 2007-04-13 01:49 bookmarks.html
-rwxr-x---  1 guice www-data  6582857 2007-04-13 01:49 BoulevardofBrokenSongs-2.mp3
-rwxr-x---  1 guice www-data  3841225 2007-04-13 01:49 boulevardofbrokensongs.mp3
-r-xr-x---  1 guice www-data    22708 2007-04-13 01:49 burnedwoods.html
-rwxr-x---  1 guice www-data 48371458 2007-04-13 01:50 chronology.sql
drwxr-x---  2 guice www-data    32768 2007-04-13 01:50 Desktop

```
(just a subset of the oddities)
And it's not just limited to .html files. I do have writable .html files as well as unwritable .xml files.

Why is this? How can I fix it? It's pretty important that I have every file on this drive writable.

---

### Post by [S|G] on 2007-05-12
If you do this:
```
sudo chmod 750 -R /media/iomega
```
Are the .html files still unwritable?

---

### Post by guice on 2007-05-12
Well fark, I did that earlier and it didn't work. No clue why ... /shrug, all well. Feel free to mark this as resolved as a simple +w did work on the files. I feel stupid now....

---

