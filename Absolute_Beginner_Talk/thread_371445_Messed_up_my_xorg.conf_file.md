---
title: "Messed up my xorg.conf file"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by BurgesS on 2007-02-26
Luckily I saved a backup but am having trouble deleting the messed up file so I can rename the backup to xorg.conf.  Ubuntu can't launch the GUI so it starts at a command prompt.  When I try to delete the file I get an access denied message because it is a root file I guess.  How do I log in as root so I can remove this file and rename my backup.

Sorry guys...don't you hate newbs?

---

### Post by Adramelech on 2007-02-26
sudo cp backup dest

---

### Post by scrooge_74 on 2007-02-26
Nobody hate newbs, at one time every body was.

to delete the file you can do sudo rm xorg.conf

or just copy over it sudo cp your_backup_file_name xorg.conf

---

### Post by STREETURCHINE on 2007-02-26
try 

```
sudo cp /etc/X11/xorg.conf.backup etc/X11/xorg.conf
```

 restart x

```
ctrl+alt+backspace
```

---

### Post by BurgesS on 2007-02-26
So...putting sudo before the command makes you root?

---

### Post by sloggerkhan on 2007-02-26
try 
sudo mv /etc/X11/backup.xorg.conf /etc/X11/xorg.conf
or
sudo cp /etc/X11/backup.xorg.conf /etc/X11/xorg.conf

---

### Post by sloggerkhan on 2007-02-26
adding sudo executes the command as though you were root.

---

### Post by BurgesS on 2007-02-26
awesome...that fixed it....thanks!!!!!

---

