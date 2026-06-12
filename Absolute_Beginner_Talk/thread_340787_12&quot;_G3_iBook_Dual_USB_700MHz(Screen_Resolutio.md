---
title: "12&quot; G3 iBook Dual USB 700MHz(Screen Resolution)"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by rogue6 on 2007-01-17
Hi

      Ok i'm very new to linux but not completely helpless.My problem is my screen resolution I'm on a 12" G3 iBook Dual USB 700MHz.Install went Perfect got my airport working and everything
I just can't deal with the 800x600 screen resolution It"s way too BIG. I've tried to fix it searchin on my own with no Luck.The closest i could find a fix was at this link 

[http://www.ubuntuforums.org/showthread.php?t=231279&highlight=ibook+screen+resolution](http://www.ubuntuforums.org/showthread.php?t=231279&highlight=ibook+screen+resolution)

But text entry i tried on those posts Either had no effect or i got a xserver error and was lost and had to reinstall 5times so far.So I've read to back up your xorg.conf file.But when i screw it up and get stuck.I have no idea how to restore the backup file.

Help Please

---

### Post by linear on 2007-01-17
To backup or restore the file, work from a shell prompt (ctrl-option-F1).

Get to the correct directory:

**cd /etc/X11**

Backup the file:

[B]sudo cp xorg.conf xorg.old
[/B]
Restore:

[B]sudo cp xorg.old xorg.conf
[/B]
You might want to try just regenerating the xorg.conf file:

**sudo dpkg-reconfigure xserver-xorg**

Finally, to restart Gnome:

**sudo killall -HUP gdm**

---

### Post by rogue6 on 2007-01-17
Thanx got it to work regenerating the xorg.conf file:
:)


Now to customize the appearance

---

