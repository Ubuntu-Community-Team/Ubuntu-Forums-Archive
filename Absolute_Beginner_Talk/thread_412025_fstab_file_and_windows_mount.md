---
title: "fstab file and windows mount"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by HeyItsMatt on 2007-04-17
Hey folks!

I am on a computer that dual boots Windows XP and Ubuntu 6.10.  I want to make Ubuntu recognize my Windows partition on startup so that I can read from it (which means taking files from it, correct?).  I have a couple resources here that are confusing me slightly.  One is in the Community Ubuntu Documentation, the other is the Psychocats windows mounting page:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I have looked at the output of the command "sudo fdisk -l" and it shows my Windows XP partition (/dev/hda1, HPFS/NTFS).  I have created the new directory /media/windows to mount to, and backed up the /etc/fstab file.  What confuses me is exactly what to add at the end of the /etc/fstab file in order for the windows partition to show up.  In the Community Ubuntu Documentation resource, under the heading "Editing Ubuntu's filesystem table", there is an options table that lists for a NTFS partition (accessible by one user):
"ro,user,auto,fmask=0177,dmask=0077,uid=1000".  
However, when it gives an example of how I would mount a vfat partition, it says this: 
"/dev/hda1   /media/windows   vfat   user,fmask=0111,dmask=0000   0   0"

Should I be following the latter example and just replacing "vfat" with "ntfs" and then adding "ro" to the beginning of the options section and "uid=1000" to the end of it?  Also, why does it leave out "auto" from the vfat example when it has "auto" in all the examples in the options table (FAT32, NTFS, and Apple alike)?

The Psychocats resource also lists something totally different to add to the end of the fstab file (or modify an existing listing to look like): 
"/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0"
The mount directory is just a different preference, but I'm wondering why the options are so different?  The example leaves out any mention of "ro", "uid=1000", "auto", "fmask=0111", or "dmask=0077".

I guess I'm just confused because I keep reading that I have to be careful modifying fstab, but exactly what to write for "options" is kind of vague and confusing, so I'm reluctant to try this and end up roasting Ubuntu. Thank you for reading.

---

### Post by annda on 2007-04-17
just to make it short, aysiu's options at psychocats are simpler and they work. fmask and dmask are not necessary, since umask covers all that for a non-writeable partition. also, "ro" is not needed, because linux knows that a NTFS partition is by default read-only - unless you want to use a special driver,

if you want the details, read here:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

UPDATE:
if you need it, here is the NTFS driver:
[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

search the forums for ntfs-3g on how to handle it - i don't use it so i can't help you, sorry.

---

### Post by HeyItsMatt on 2007-04-17
> **annda said:**
> just to make it short, aysiu's options at psychocats are simpler and they work. fmask and dmask are not necessary, since umask covers all that for a non-writeable partition. also, "ro" is not needed, because linux knows that a NTFS partition is by default read-only - unless you want to use a special driver,

if you want the details, read here:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

UPDATE:
if you need it, here is the NTFS driver:
[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

search the forums for ntfs-3g on how to handle it - i don't use it so i can't help you, sorry.

Thanks for the reply annda!  The link definitely cleared up what the "mask" stuff meant.  Just to make sure, would be it fine if I added this line to the fstab file?

/dev/hda1 /media/windows ntfs nls=utf8,umask=0222,uid=1000 0 0

Basically it's the line on the Psychocats page but I'm just adding "uid=1000" to the options section of the line, so that access is restricted to my administrator (and only) Ubuntu account.  I don't really *need* this but I don't foresee ever having to make another user on this computer or needing that user to access the windows mount, so I figure it can't hurt for security.

---

### Post by annda on 2007-04-17
if you are sure your user id is 1000, i guess it won't hurt.

check system > admnistration > users ans groups to make sure.

---

