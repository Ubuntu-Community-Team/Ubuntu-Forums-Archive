---
title: "Router/flash drive file problem"
date: 2015-07-06
forum: Any Other OS
---

### Post by kurt18947 on 2015-07-06
I hope this is the correct place for this. If not, please feel free to move.  I had something 'interesting' occur and I'm hoping someone can make an educated guess as to what happened. I have a Linksys E2500 router running a current version of DD-WRT. This router has a USB port and DD-WRT recognizes it. I plug a 16 GB. PNY Attache drive into the router to function as a data backup. I"m pretty sure the drive is formatted with an ext* file system. Windows tells me the drive needs to be formatted and permissions are present on intact folders so not FAT32. 

The problem is that one folder appears to no longer exist. Here is a screen shot of a folder that is readable.

[ATTACH=CONFIG]263054[/ATTACH]

Here is the corrupted folder

[ATTACH=CONFIG]263055[/ATTACH]

It appears as a binary file rather than a folder. If I right-click the 'file' in Nautilus it shows up as 2 GB. which seems about right. If the drive is plugged into a PC USB port the corrupted file/folder may or may not show up. If it does show, it shows as a file rather than a folder.  I'm not concerned about recovering data from the corrupted folder - backups are GOOD things but I'm curious about what happened. Two other folders and two text files are intact. It's just the one Folder that went bonkers. The contents were a bunch of .jpg pics and .pdfs and perhaps an .odt file or two. No script files or binaries. I may try testdisk/photorec on it just to see what happens. I'm thinking hardware failure but if so, why only one folder and not the entire drive? Thanks for any insights or suggestions preventing a recurrence.

---

