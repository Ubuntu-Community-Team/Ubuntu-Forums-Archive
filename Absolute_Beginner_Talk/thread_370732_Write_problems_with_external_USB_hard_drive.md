---
title: "Write problems with external USB hard drive"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by michaelc.nash on 2007-02-26
Hi all.

I have a Western Digital MyBook external hard drive (USB) that works fine in Windows, but I can only read from it in Kubuntu. 

I've read that it should be mounted as a hard drive, but instead it appears in the /media directory (it also has the icon of a USB stick).

Does anyone have a clue what is happening? I need to be able to write to the disk, as there are files I need to work on in both Windows and Linux. I can't format the disk, as it contains a lot of stuff already.

Thanks!

---

### Post by timetunnel on 2007-02-26
I have a Western Digital Passport, and it appears as "/media/WD Passport". USB-sticks and USB-harddisks usually appear in the "/media" folder, so that should be ok. What kind of file system does your USB disk use? It should be FAT32 if you want to have write access with Windows **and** Linux.

---

### Post by michaelc.nash on 2007-02-26
Blast! It's NTFS.

I don't have another hard drive with enough spare room to keep the contents of the external hard drive, so I can't reformat it. Is there no way at all that I can get Linux to write to it anyway?

---

### Post by george29 on 2007-02-26
yes - you can use the ntfs-3g driver...

do a google search and forum search to find out how to obtain and install the driver.

---

### Post by timetunnel on 2007-02-26
...or just ask the ubuntu wiki:

[https://wiki.ubuntu.com/ntfs-3g](https://wiki.ubuntu.com/ntfs-3g)

---

### Post by timetunnel on 2007-02-26
just a few days ago the first stable version has been released:

[http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)

---

### Post by michaelc.nash on 2007-02-26
Thanks for these; I'm having a few problems installing ntfs-config though.

I put one of the package URL things into source.list, then do:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ntfs-config

...but it says that it cannot find the package ntfs-config. Is there something I am really not getting here?

(sorry for trying your patience, I'm rather new to all this).

---

