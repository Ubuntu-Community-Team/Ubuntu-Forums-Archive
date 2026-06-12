---
title: "Can someone explain how GNOME makes graphical links/shortcuts on the desktop?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by mr.v. on 2007-02-06
Hi all--

I have a question about graphical links on the desktop. I know I can create my own symlinks using ln -s in the home/username/Desktop folder and they show up and work but I also know there's a way using the GNOME context-menu. It just doesn't seem to work on the following situations.

Namely I wanted to make a link on the desktop to /home/<my username> So I opened up Places|Computer|Filesystem|home

Then I right clicked on the folder for my username but the "Make Link" option on the context-menu is grayed out.

Then I tried to make a link to the "Filesystem" on the desktop since there isn't one by default but there are ones to my other partitions. 

To do this, I went to Places|Computer then right-clicked and the "Make Link" option was available so I clicked it but I get an error saying "'Operation not permitted' while creating a link to 'computer:/...em.desktop'"

okay...so then I just dragged the filesystem icon onto the desktop and voilla it made link. Going into a terminal I see that it made the file Filesystem.desktop whose contents are:
```
[Desktop Entry]
Encoding=UTF-8
Name=Filesystem
Type=Link
Icon=gnome-dev-harddisk
URL=file:///
```
so to make a homefolder link I made my own file titled Home.desktop in the /home/<usrname>/Desktop folder
```
[Desktop Entry]
Encoding=UTF-8
Name=Home
Type=Link
Icon=user-home
URL=file:///home/<MY USER NAME WENT HERE>
```
and it worked just fine and made a pretty link. So my question is...why won't the right-click context menu "Make Link" work? Must I manually create symlinks and/or these "Desktop Entries" myself? I'm okay with that...I'm just wondering because there appears to be the functionality to do it graphically.

Also I have another question...I have two non-linux partitions, /dev/hda1 (NTFS) and /dev/hdb6 (FAT32). Both of which are mounted in the /media folder and in the fstab. However, hdb6 is mounted in /media/hdb6 and on my desktop there is an icon (automatically created) called hdb6 with a harddrive icon. Here's the weird part...for /dev/hda1 which is mounted in /media/hda1, instead of an icon named hda1 there is a drive icon called "Local Disk". At least according to cfdisk and fdisk that partition doesn't have a volume label...so my question is...why is /dev/hda1 named "Local Disk" and is there any way to change the name? Selecting it and pressing F2 doesn't seem to change it and I don't see ".desktop" entries for either of these icons like I do for the ones I made manually in any folder (including hidden ones) in my /home directory...

sorry for the only windowmanager I'm used to is fluxbox which doesn't have desktop icons to begin with =)

---

### Post by wildseven on 2007-02-06
heh im sorry this has no help for you whatsoever. but if you know how to do it through terminal, why does it matter to do it any other way?:lolflag:

---

### Post by NotPhil on 2007-02-06
> **mr.v. said:**
> So my question is...why won't the right-click context menu "Make Link" work? Must I manually create symlinks and/or these "Desktop Entries" myself? I'm okay with that...I'm just wondering because there appears to be the functionality to do it graphically.
I think you can do the same thing by right-clicking on the desktop and choosing "Create Launcher." The difference between a symbolic link and a desktop launcher is that one is just a link to another file, while the other launches a program and, optionally, feeds it some parameters. You open your Home folder with the program Nautilus, so you need a launcher.

---

