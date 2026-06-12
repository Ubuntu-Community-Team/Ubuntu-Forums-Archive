---
title: "External FAT32 Hard Drive"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by barrack on 2006-08-24
Hey all,

I just set up my computer to dual boot w/ XP and Ubuntu. (I really wanted a full Ubuntu install, but I need Windows to run a special program for this project I'm working on. But I digress...)

I backed up my personal files that were on XP onto an external HD that I bought jsut for this purpose. I also formatted the drive as FAT32 because of the compatibility with Windows, Linux and OS X. So I finally got both fresh installs of Ubuntu and XP up to date and I'm all ready to test access my files in Linux.... the only problem now is that all files and folders are listed as read-only.

Is there any way that I can fix this? I would like to be able to change files as needed. As always, any help is appreciated.

---

### Post by frrobert on 2006-08-24
A detailed set of instructions are at

[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28mountingwindows%29](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28mountingwindows%29)

Look under Mount a FAT32 partition

---

### Post by eternalsword on 2006-08-24
well it depends on if it's mounted with write capability or if you need to change the permissions on all the files.  if it's just a permissions thing, go to the root of the drive in the terminal and do: chmod -R 0775 *
as for the mounting I'm not sure off the top of my head and don't have time to look it up right now

---

### Post by mssever on 2006-08-24
> **eternalsword said:**
> well it depends on if it's mounted with write capability or if you need to change the permissions on all the files.  if it's just a permissions thing, go to the root of the drive in the terminal and do: chmod -R 0775 *
as for the mounting I'm not sure off the top of my head and don't have time to look it up right now
The link provided by frrobert above has good info. Note that for any windows filesystem type, changing permissions by any means other than through mount options will have no effect whatsoever.

---

### Post by barrack on 2006-08-24
Frrobert, thanks for the info. Mine is a USB connected, drive, I should have mentioned that. Will these instructions still work? I spose I can reboot the system w/ the harddrive plugged into the USB.

I won't be able to test this until tomorrow though.

Thanks again!

---

### Post by barrack on 2006-08-24
> **eternalsword said:**
> well it depends on if it's mounted with write capability or if you need to change the permissions on all the files.  if it's just a permissions thing, go to the root of the drive in the terminal and do: chmod -R 0775 *
as for the mounting I'm not sure off the top of my head and don't have time to look it up right now

I did this... and it did indeed allow me some access to this and that... but it created a LOT of files with unreadiable characters. I'm not sure what they are... and nwo I can't remember what items wheren't in a folder!  Eep!

---

### Post by barrack on 2006-08-25
> **barrack said:**
> I did this... and it did indeed allow me some access to this and that... but it created a LOT of files with unreadiable characters. I'm not sure what they are... and nwo I can't remember what items wheren't in a folder!  Eep!

Just as a follow up... is there a way to undo this chmod thing? The files that now appear (with filenames using characters that don't show up) are actually pretty large. Some of them are on the order of 3 or 4 GB. If not, I will just have to back up my files somewhere else and try this again.

---

### Post by eternalsword on 2006-08-25
> **barrack said:**
> I did this... and it did indeed allow me some access to this and that... but it created a LOT of files with unreadiable characters. I'm not sure what they are... and nwo I can't remember what items wheren't in a folder!  Eep!

chmod never creates files, so I'm not sure what you did.

---

