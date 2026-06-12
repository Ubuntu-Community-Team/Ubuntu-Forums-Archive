---
title: "autosync files to thumb drive or memory card"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by mistergq on 2007-07-16
Is there a program that I can autosync files to a thumb drive or memory card every time the device is plugged into the computer?

---

### Post by Al3xK3aton on 2007-07-16
If you have changed both the version on your hard disk and the version on the thumb drive, you have to choose which way to sync, thus losing the changes in one of the copies of the file.

---

### Post by gsb521 on 2007-12-19
Bump.

Are there any programs out there that can do the type of thing that briefcase does in Windows (better, if possible)?

---

### Post by Inxsible on 2007-12-19
rsync should do the job. You might have to create an alias command which will mount the drive and sync it. For more information enter ```
man rsync
``` in a terminal

---

### Post by Blutack on 2007-12-19
Conduit/Unison have GUI's.

---

### Post by borobudur on 2008-03-21
[http://linuxappfinder.com/backupandrecovery/filesynchronizing](http://linuxappfinder.com/backupandrecovery/filesynchronizing)

---

### Post by herbster on 2008-03-21
Rsync is certainly the way to go, but having it execute whenever the device is mounted is another story. One very real possibility is the System > Preferences > Removable Drives and Media, going to the tab for a USB stick being attached and changing the command for when it's mounted to the rsync command, which is as simple as

```
rsync -avz --delete /source /destination
```

---

### Post by herbster on 2008-03-22
RSync is definitely the way to go. You can most likely go to System > Preferences > Removable Drives and Media and change the command for USB stick in one of the tabs to

```
rsync -avz --delete /source /destination
```

---

