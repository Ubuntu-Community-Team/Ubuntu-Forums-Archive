---
title: "Ubuntu Beginner Can't mount cdrom or floppy drive"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Rock518 on 2006-09-26
I am a new kubuntu user and I am unable to mount my cdrom0 or my floppy drive 
although I have Kier Thomas's book Beginning Ubuntu Linux From Novice to Professional. Could some kind person help a 70 year old silver surfer

---

### Post by JAwuku on 2006-09-26
Hello, and welcome to Ubuntuforums!

Normally CD's and floppies should mount automatically when inserted.

there's a good site out there for setting up Ubuntu and Kubuntu, click on

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

especially the bit for CD-ROM mounting:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders)

Although I don't have a floppy drive, I believe you can mount a floppy disk with ```
mount /media/floppy
```

and unmount it with ```
umount /media/floppy
```

sorry if that does not address why they are not coming up automatically, but it should enable you to access your disks.

Hope this helps.

---

### Post by Kateikyoushi on 2006-09-26
Can mount it by right clicking on the icon in Places > Computer.

Or you can find the cdrom device in:

```
/var/log/syslog
```

Then type 

```
sudo mount /media/CDROM/
```

change the CDROM to whatever your cdrom drive is.

---

### Post by tatimmer on 2006-09-26
I wrote a small program called mrm MountRemovableMedia which is available from my website and may help you.

---

