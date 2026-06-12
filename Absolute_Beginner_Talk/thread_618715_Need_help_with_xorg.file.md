---
title: "Need help with xorg.file"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-11-20
I really need some help here. 

One of the first thing I did after I had installed Ubuntu was to make a backup of the xorg.file with the command:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

I got problems with the resolution/Hertz and needed to reinstall the backup, and did so with the command; 
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

I learned this from a guide once(and wrote it down). But it didn't help at all, each time I start I have to manually change the settings, and looking at the xorg.file shows me a safemode file. Why are not the orginal file there?

Second;
 I use a keyboard layout for Norway, but it started to change back to us(so I cant use the keyboard). I went to System > Preferences >Keyboard  where I had to change it back to no, but next time I rebooted Ubuntu it went back to us. Then I changed the «us», in xorg.file, to «no» and it was back to the correct layout. But now, when restarting Ubuntu I get a error message that there is a conflict with gnome settings and xorg.fiel? I don't understand it.

Edit: I have also tried "sudo dpkg-reconfigure xserver-xorg " but I dont know the answers to all the questions I get...

---

### Post by Dr Small on 2007-11-20
After you restored the backup, did you restart X ?
CTRL + ALT + SHIFT + BACKSPACE

Dr Small

---

### Post by MegaJim on 2007-11-20
It is possible that bulletproof X is modifying your xorg.conf file automatically.

For future reference, it is wise to name backups in a descriptive and unique manner, for example xorg.conf.todaysdate-presomechange.bak just to be sure you don't accidentally overwrite it (or some other process).

If you did indeed backup your xorg.conf you can compare that file to the current one and check whats going on, cp'ing the file adds a new file, but does not remove the old one, so your backup should still be there.

---

### Post by _sAm_ on 2007-11-20
Dr Small: Yes, and I also tried to restart Ubuntu.

MegaJim: 
Thanks for the advice, I will do that if I make more then one backup. 

The backup is there, I have checked with Nautilus in /etc/X11/ where both xorg.file and xorg.file_backup are(they are very different when I look at them in gedit). I did also open the backup file as root(gksu nautilus then just copy), and then I pasted it over the xorg.file; to get the same content back as before, restarted X(Alt +Ctrl+Delete) and got a black screen.... 

Is it possible for me to remove the bulletproof X future, its only making this harder for me. Right now I don't know what is happening to keyboard settings nor the screen settings.

---

### Post by _sAm_ on 2007-11-21
I tried again with:
```
sudo dpkg-reconfigure -phigh xserver xorg
```, and now it works. Bulletproof X is all but "bulletproof", dos not work at all on my pc:-/ 

But I still really want to know why the backup didnt work?

---

### Post by MegaJim on 2007-11-21
You could be really mean and deny all write permissions to your xorg.conf if it keeps happening.

---

### Post by Aquilastudio.com on 2007-11-21
sudo dpkg-reconfigure -phigh xserver xorg

and follow the directions.

Trust me. Been there.:guitar:

---

