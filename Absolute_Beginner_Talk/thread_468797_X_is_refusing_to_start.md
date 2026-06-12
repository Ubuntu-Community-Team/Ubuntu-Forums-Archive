---
title: "X is refusing to start"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by gene74 on 2007-06-09
anyway i was trying to get my MX1000 to work following this guide - [https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)

when i rebooted, it wont boot to ubuntu. how can i get back to restore the back up copy
"If X refuses to start, it means you probably made a typo. To fix this, just restore the backup copy of xorg.conf: sudo rm /etc/X11/xorg.conf; sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf. Then start X again and check your xorg.conf for errors."

TIA

---

### Post by nick_h on 2007-06-09
CTL-ALT F1 will get you to a console.  From there just *cd /etc/X11/* then see if you have a backup to restore.

If this fails you can always boot to recovery mode to get to a terminal.

---

### Post by Nythain on 2007-06-09
if you dont have a backup copy of the xorg.conf then you can delete your current one in the command line
```

sudo rm /etc/X11/xorg.conf

```
and make a new one
```

sudo dpkg-reconfigure xserver-xorg

```
answering everything as best you can, and using defaults on things you dont know should work out well and give you a clean new xorg.conf

---

### Post by gene74 on 2007-06-09
thanks

i tried 
sudo rm /etc/x11/xorg.conf; sudo cp /etc/x11/xorg.conf.backup /etc/x11/xorg.conf

i get a message that no file or directory
and no file (backup)

i boot off the live cd and its there

---

### Post by bodhi.zazen on 2007-06-09
Boot to your Ubuntu install.

In a terminal (Ctrl-Alt-F1 or Ctrl-Alt-F2) log in.

Then : ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This re-configures X the -phigh flag selects defaults (for everything but resolution) and will be easier.

Then re-start X : ```
sudo /etc/init.d/gdm restart
```

Next time, please back up system files before you edit them ;)

---

### Post by gene74 on 2007-06-09
thanks ill try that
the thing is i did back up the file
i booted off the live cd earlier and checked the  contents of the hard drive
i can see the both files  in /etc/x11

---

### Post by Nythain on 2007-06-09
found your problem, CAPITAL X

/etc/X11/    not /etc/x11

---

### Post by gene74 on 2007-06-09
well i tried everything  when i kept getting that no such file or directory ;)  ](*,)](*,)
thanks to nickh,  nythain and  bodhi.zazen =D>=D>
everything is back

---

