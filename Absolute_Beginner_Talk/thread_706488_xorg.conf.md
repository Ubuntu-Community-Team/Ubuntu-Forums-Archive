---
title: "xorg.conf"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by peakshysteria on 2008-02-24
Can anyone tell me how to go back to a backup of an previous xorg.conf?? I'm sure i did take a backup. But how do i go back to it??

---

### Post by bwhite82 on 2008-02-24
Simply rename the backup to the correct name: xorg.conf and make sure its in: /etc/X11/
Its usually labeled something like xorg.conf.bak or xorg.conf.old, etc.

To rename, from the CLI:
> 
sudo rename xorg.conf.old xorg.conf

Edit: Backups are usually in the same directory: /etc/X11
You can locate them if they're not:

> sudo locate xorg.conf.old

---

### Post by dabang on 2008-02-24
I f you have a backup, copy it to
```
/etc/X11/xorg.conf
```
and restart X. (Maybe make a backup of your current xorg.conf, too....)

---

### Post by peakshysteria on 2008-02-24
> **Soldierboy said:**
> Simply rename the backup to the correct name: xorg.conf and make sure its in: /etc/X11/
Its usually labeled something like xorg.conf.bak or xorg.conf.old, etc.

To rename, from the CLI:


Edit: Backups are usually in the same directory: /etc/X11
You can locate them if they're not:

So if the backup is called xorg.conf.bak it's just: sudo rename xorg.conf.bak xorg.conf?

Or else i can rebuild with sudo dpkg-reconfigure xserver-xorg. But is the previous backup still there if i rebuild?

This is off course because i have an Ati X700 card. And have checked the driver in the restricted drivers manager. And set the screen to the correct 1280 x 1024 resolution. But when i reboot the resolution is all f***** again. And compiz ain't working no more. And as far as i can see the river isn't loaded even though the driver is checked and green in the restricted drivers manager. So i need to start from scratch again (and do i have to do something else than revert to a backup xorg (or rebuild?)).

Or maybe someone could tell me how to get the driver to load? I've followed several howtos and none of them have worked for me (or i'm doing something wrong).

---

### Post by radiocognition on 2008-02-24
reconfigure xserver-xorg will not overwrite your .bak file - I am assuming you made the backup yourself right?  I learned after my own first graphics disaster to always keep backups of xorg.conf

---

### Post by bwhite82 on 2008-02-24
> So if the backup is called xorg.conf.bak it's just: sudo rename xorg.conf.bak xorg.conf?

Correct. Thats assuming both files are in the same directory.

---

### Post by peakshysteria on 2008-02-26
sudo rename xorg.conf.bak xorg.conf gives me the cryptic:

Bareword "xorg" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "conf" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "bak" not allowed while "strict subs" in use at (eval 1) line 1.

Kinda new to linux so not sure what this means :(

---

### Post by herbster on 2008-02-26
I think the easiest route is first off:

```
 cd /etc/X11
ls
```

Run those commands and paste the output.

---

### Post by zvacet on 2008-02-26
If you followed herbster advice and run these commands and find out that you have xorg.conf and xorg.conf.bak in X11 then

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

