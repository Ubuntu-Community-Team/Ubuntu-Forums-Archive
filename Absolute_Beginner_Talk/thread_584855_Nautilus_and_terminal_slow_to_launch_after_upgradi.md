---
title: "Nautilus and terminal slow to launch after upgrading to Gusty"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by moairmoair on 2007-10-21
Hi,

I got some strange problems after upgrading to 7.10. 

Double clicking on folders on the Desktop loads Nautilus immediately and fast. But choosing Places/Home or clicking on the Trash icon takes a long time to launch Nautilus. 

Launching a terminal window also takes a long time. 

This problem did not happen right after the online upgrade to Gusty. Seems it only happened after a failed connection (through Samba) to a Windows box in the home lan. 

Any idea what's going wrong? (Wondering if I should have did a clean live-CD install of Gusty instead of the upgrade.)

Thanks,
Moair

Update: its not only Nautilus and Terminal. Some other programs are slow to load as well. Please refer below.

---

### Post by mikeyphi on 2007-10-21
Have you had a look using System monitor to see if an unexpected process is running?

---

### Post by moairmoair on 2007-10-21
> **mikeyphi said:**
> Have you had a look using System monitor to see if an unexpected process is running?

CPU consumption is very low. It seems the slowed programs are just waiting for a while (without hard disk accessing) for something before they show up. 

Fast as normal:
Calculator,  Folders on the Desktop  (Nautilus), Geany editor, MySQL Query Browser, flpsed, Gimp. 

Noticeably slower than before update  to 7.10:
Home Folder, Accessories/Dictionary, Default Terminal, Google Earth, Evolution, Opera,  Tomboy, OpenOffice Word, gedit ...

---

### Post by moairmoair on 2007-10-21
The following packages are removed at the end of the update. Does it have something to do with the slowing down?

binfmt-support
feisty-session-splashes
gcj-4.1-base
gij-4.1
gnome-cups-manager
libgda2-3
libgda2-common
libgnomecupsui1.0-1c2a
liblzo1
libportaudio0
libslab0
libstlport5.1
openoffice.org-filter-mobiledev
ttf-baekmuk
vnc-common
xvncviewer

---

### Post by neillo on 2007-10-24
I just did an internet upgrade to 7.10 as well, and I am now having a slow opening of Nautilus the first time I try to access a mounted FAT32 partition, but my programs run fine.  Probably not related, but I'm throwing it out there just in case...

---

### Post by handaxe on 2007-11-01
[http://ubuntuforums.org/showpost.php?p=3682583&postcount=9](http://ubuntuforums.org/showpost.php?p=3682583&postcount=9)

Help?

HA

---

### Post by wild_oscar on 2007-11-30
I have the same problem.

Especially the Trash icon, it is SLOW as hell to open. I can even see the window expanding. It takes 3 seconds to open the window!

---

