---
title: "Shell Script"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-02-01
I was wondering how one would go about makeing a script to run a command at start up.  I know I have to put it in /home/<user_name>/.kde/Autostart.

The command I want to run is
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Thank you in advance for any help.

---

### Post by xtacocorex on 2006-02-01
I don't know why you wouldn't add this to /etc/fstab to do it automatically on boot.

As for the shell script:
```

#!/bin/sh

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

```

That might work, but you'd have to enter a password somewhere, so you might have to change sudo to kdesu or gksudo (I don't have Gnome, so I can't be totally sure on that one).

I also can't test this because I don't have my computer set up to dual boot.

---

### Post by tseliot on 2006-02-01
[QUOTE=JNowka]I was wondering how one would go about makeing a script to run a command at start up.  I know I have to put it in /home/<user_name>/.kde/Autostart.

The command I want to run is
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Thank you in advance for any help.[/QUOTE]
Just edit your fstab:
sudo cp /etc/fstab /etc/fstab_backup 
sudo gedit /etc/fstab

Append the following line at the end of file:
/dev/hda1 /media/windows ntfs umask=0222 0 0

Then:
sudo mount -a

---

### Post by JNowka on 2006-02-01
Thank you all for your help.

---

