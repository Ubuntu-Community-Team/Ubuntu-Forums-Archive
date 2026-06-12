---
title: "I screwed up my resolution"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Steve4774 on 2006-10-07
So I tried to get my resolution to be bigger, and I apparently did it incorrectly. I used:

```
sudo dpkg-reconfigure xserver-xorg
```

I went through that process, set it to 1600x1200 (which I now know is too high), And I can't even enter GNOME after I went through that. Is there any way to restore what I had before?

---

### Post by AndyCooll on 2006-10-07
You cannot restore your former settings if you didn't keep a backup copy of them.

However ...you have a couple of options:

1. Press ALT+F1 (or ALT+F2 etc) and logon to another "virtual" terminal and then rerun "sudo dpkg-reconfigure xserver-xorg". Indeed you can keep re-running it until you finally get a screen. When it comes to the graphics card section, it might be wise to select "vesa". This is a bog standard card that basically works with everything. If you get things working, _then_ you can consider further tweaks.

2. Press ALT+F1 and logon to another "virtual" terminal and manually edit the relevent file yourself by typing:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```

:cool:

---

### Post by Steve4774 on 2006-10-07
I believe I did make a backup copy, because it asked me if I wanted to when the reconfiguration started, if I remember correctly. How would I recover it?

---

### Post by rubbsdecvik on 2006-10-12
You can restore the backup this way

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

the first one "/etc/X11/xorg.conf_backup" is the backup copy, and the second one is the one that you are going to restore.  

the last part of the first section the 
```
xorg.conf_backup
```
is the name of the backup you created.  It may be something like this too 
```
xorg.conf.bak
```

Hope that helps

---

### Post by bodhi.zazen on 2006-10-12
To find the name of your backup:```
ls /etc/X11 | grep xorg
```

---

### Post by h4rdwire on 2006-10-12
Couldn't he jsut edit the xorg.conf file? in the resolution section save and reboot ?

---

