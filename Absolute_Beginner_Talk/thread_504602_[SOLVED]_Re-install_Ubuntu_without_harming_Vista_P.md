---
title: "[SOLVED] Re-install Ubuntu without harming Vista Partition"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by holdinout on 2007-07-19
How do I remove and re-install ubuntu without touching my Vista partition? I'm having some trouble finding an answer on the forums. The only reason I'm re-installing is because my session crashes before 10 seconds. I also can't get into "Sessions", or "Desktop Effects". I would just re-install both of them but getting all my drivers for Windows is a pain. 
Any help is appreciated guys. 

Oh, heres the output of my xsessions-errors file:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "administrator"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Desktop:/tmp/.ICE-unix/6126
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Initializing gnome-mount extension
Starting gdesklets-daemon...

Connecting to daemon [###          ]
(update-notifier:6209): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.


Seems like gDesklets is the problem, but why would it suddenly stop working? As I said, I can't open sessions to remove gDesklets from startup.

---

### Post by LaRoza on 2007-07-19
If you have already a dual boot setup it will be easy, you just install Ubuntu to those partitions that Ubuntu used before. You can choice "manual" or something during the installation and you will be given an overview of your hardrive(s). You select where you want to install Ubuntu, since Ubuntu was there before, you needn't worry about formatting, just make sure the new Ubuntu knows where swap is, it should automatically.

---

### Post by holdinout on 2007-07-19
Awesome, thanks much. Do you know the command to see all partitions and info? ls something?

---

### Post by Malibu Illusion on 2007-07-19
Try:

```
sudo fdisk -l
```

---

### Post by holdinout on 2007-07-19
Thats the one. Where is there a good page with all the useful Ubuntu commands? Guessing it doesn't exist yet? It would be nice to have one place to refer to when you forget commands.

---

### Post by ReaderRat on 2007-07-19
> **holdinout said:**
> Thats the one. Where is there a good page with all the useful Ubuntu commands? Guessing it doesn't exist yet? It would be nice to have one place to refer to when you forget commands.

[Terminal *_[color=red]Basics[/color]_*](http://users.bigpond.net.au/hermanzone/p8.html)

[All You Want To Know About Terminal](http://ubuntuforums.org/showthread.php?t=171507)

[Terminal: *Basic _Tutorials_*](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by LaRoza on 2007-07-19
They are mostly Linux commands and common to all distros. Some are programs, that not all distros have, like "tree".

When you install, you will get a graphical view of the disk, like GParted. Just don't touch anything with an NTFS partition!

---

### Post by cobrn1 on 2007-07-19
So does GRUB work with vista then (think so, but not sure, hence asking you...)

Maybe planning triple boot: ubuntu, XP, vista/ubuntustudio/anyother OS i might like to try...

As we're all here (sorry to hijack your thread, but I think your q's been answered) if you're using 1 harddrive you'r limited to a certain amount of primary partitions (3 or 4, can't remember...). If you use 2 harddrives, can you have another 3 or 4 on that harddrive too?

---

