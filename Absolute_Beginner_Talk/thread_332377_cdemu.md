---
title: "cdemu"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by parradux on 2007-01-05
I'am having problems mounting .bin and .cue files. I have this .cue so I execute: 

cdemu 0 /pathtofile/image.cue 

then once this is done, I should be able to do: 

mount /media/cdemu0

to get it to cdrom0

however i get this warning when i try to mount it:

mount: wrong fs type, bad option, bad superblock on /dev/cdemu/0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


How can I mount this cue file?

---

### Post by ajmorris on 2007-01-05
try this
[http://www.mail-archive.com/forensics@securityfocus.com/msg00286.html](http://www.mail-archive.com/forensics@securityfocus.com/msg00286.html)

---

### Post by ajmorris on 2007-01-05
also this application for linux mounts bin and cue files

[http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml)

---

### Post by parradux on 2007-01-06
Even conversion to ISO format wont work.

---

