---
title: "admin password"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-08-29
Am trying to use an XP CD to fdisk or is it FDISK
/MBR or whatever (so I can boot into the XP partition at the start of the
disk in order to make it larger with Partition Magic).
It seems the Administrator password is not accepted. I assumed the
administrator password in XP would be my password !?
Does anyone know how I can bypass this obstacle?
Cheers all

---

### Post by FuriousLettuce on 2006-08-29
The Administrator password was set when windows was installed. If you got your computer from a company (rather than building / installing windows yourself) then your best bet is to ring them up and ask about it.

---

### Post by benfindlay on 2006-08-29
Bypassing passwords isn't easy at all.

XP passwords can be cracked using a combination of programs called Saminside and L0phtcrack. It does take quite a bit of time, depending on how powerful your pc is.

You need to boot into linux and mount a removable drive like a USB pen drive. Then you need to mount you hard-drive and go to /windows/system32/config. In this directory you need to copy the files called SYSTEM and SAM onto your USB pen drive. then if you boot into a windows pc with Saminside and L0phtcrack installed you can crack the passwords using those 2 programs.

However it is often less hassle to remove the drive, put it into another pc, get the files you wnt to keep and then reformat

Just as a sidenote, you can get a bootable version of linux called ntpasswd which allows you to blank passwords ina windows install, however, if this goes wrong you have effectively trashed the entire OS and a reformat will have to be done!

---

### Post by carverj on 2006-08-29
Oh, ok. Thanks for the prompt reply.
I'll just have to do it the old fashioned way and install everything from scratch... anyone know how I can run a free Windows Office ? star office or cross office or whatever it is?
I don't have the CD here to re-install Office. The only reason I wiped this disk is to be able to fit the huge Visual Studio 2005.
Does anyone have any experience with and recommend the mono project for C sharp?

---

### Post by clint1010 on 2006-08-29
try openoffice.org is available on win and linux platforms, is open source and free. Comes as a standard package with Ubuntu

---

