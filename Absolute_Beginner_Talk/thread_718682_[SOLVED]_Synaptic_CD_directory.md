---
title: "[SOLVED] Synaptic CD directory"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by GregMB on 2008-03-08
Hello. I am trying to install a package (ndisgtk, if it matters) with Synaptic Package Manager, so I can get my wireless internet adapter to work. When I tell it to install it, it asks for the Ubuntu CD to be put in directory /cdrom. When I put the CD in, it by default mounts in /media/cdrom1. The problem is that Synaptic doesn't recognize this drive as the one to use. Is there any way to fix this? I am a complete newbie to Ubuntu and Linux in general, so step-by-step instructions are very helpful. Thank you in advance!

---

### Post by happyhamster on 2008-03-08
Hi. Do you have a working internet connection at the moment? If so, you can de-select the cdrom from System-->Administration-->Software Sources.

---

### Post by GregMB on 2008-03-08
> **happyhamster said:**
> Hi. Do you have a working internet connection at the moment? If so, you can de-select the cdrom from System-->Administration-->Software Sources.

Unfortunately not, that's what I'm trying to get to work.

---

### Post by happyhamster on 2008-03-08
Ok, could you show the output of the following command:

cat /etc/fstab

(Just type or copy&paste it into a terminal. Applications-->Accessories-->Terminal)
(copy = highlight text using the left mouse button)
(paste = press middle mouse button)

---

### Post by GregMB on 2008-03-08
> **happyhamster said:**
> Ok, could you show the output of the following command:

cat /etc/fstab

(Just type or copy&paste it into a terminal. Applications-->Accessories-->Terminal)
(copy = highlight text using the left mouse button)
(paste = press middle mouse button)

Okay. It says 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=c7b7dd96-f3fc-49f1-aece-7b8512b3984c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=93a24384-a84a-478d-87c2-5523270df2c8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by happyhamster on 2008-03-08
> 
dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec 0       0
Hmm, that's really strange: /dev/scd0 is listed twice. It's both a cdrom drive and a floppy drive. :confused:

Do you really have 2 cdrom drives and 1 floppy?

---

### Post by GregMB on 2008-03-08
> **happyhamster said:**
> Hmm, that's really strange: /dev/scd0 is listed twice. It's both a cdrom drive and a floppy drive. :confused:

Do you really have 2 cdrom drives and 1 floppy?

No, but if it makes a difference, I have an "Expansion bay" which I don't use, but could theoretically hold a cd drive. Also, I have about ten different miscellaneous drives, Sd, SmartMedia, CompactFlash, etc. that I rarely if ever use. I've never heard of half of them. xP

---

### Post by happyhamster on 2008-03-08
- Alright, let's assume that's all correct then :). Try the following: put the cd in the drive (make sure it is clean). Go to System --> Administration --> Software Sources and untick the cdrom. Exit that menu.

- In a terminal:

sudo apt-cdrom -m -d /media/cdrom1 add

sudo apt-get update

- It should output some stuff about adding the cdrom to the sources list. Go to System --> Administration --> Software Sources again and check if there's a second cdrom section now. It should already be ticked. If so, close the menu and try to install your app. Good luck.

---

### Post by GregMB on 2008-03-08
> **happyhamster said:**
> - Alright, let's assume that's all correct then :). Try the following: put the cd in the drive (make sure it is clean). Go to System --> Administration --> Software Sources and untick the cdrom. Exit that menu.

- In a terminal:

sudo apt-cdrom -m -d /media/cdrom1 add

sudo apt-get update

- It should output some stuff about adding the cdrom to the sources list. Go to System --> Administration --> Software Sources again and check if there's a second cdrom section now. It should already be ticked. If so, close the menu and try to install your app. Good luck.

It didn't seem to work. :( The first command worked fine, and the second cdrom section was there, and ticked. But the second one, the sudo apt-get update one didn't work, it said something about getting something from security.ubuntu.com and stopped, probably because my internet wasn't working.

---

### Post by GregMB on 2008-03-08
Well, I got the thing installed by manually going to the file on the Cd, and that worked. :P Unfortunately it didn't solve my problem of not connecting to the internet. :( Oh well. Thanks for helping!

---

