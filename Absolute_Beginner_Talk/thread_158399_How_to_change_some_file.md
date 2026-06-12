---
title: "How to change some file"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Pum on 2006-04-11
How to change some file, they are read only. I wont to change some text inside some file. Thank you.

---

### Post by Darkriser on 2006-04-11
type in console 'sudo gedit <filename>'

read here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Pum on 2006-04-11
Thank you for a quick answer . can I change the file only from the consoe?

---

### Post by Borniet on 2006-04-11
[QUOTE=Pum]How to change some file, they are read only. I wont to change some text inside some file. Thank you.[/QUOTE]

```
sudo gedit [textfile]
``` should work indeed. But if you just want to change the permissions so that the file is no longer read-only to you, you can use 
```
sudo chmod a+rw [textfile]
```
The meaning of this command is:
sudo: to issue the command as root
chmod: change the 'mode' or file permissions of a file. The command has the following attributes here:
a+rw [textfile]
where 'a' says you want to change this for all users
'+' says you want to add the permissions
'rw' says you you want the permissions 'read' and 'write' added
and [textfile] is the name of the file you want to do it to.

Hope this helps...

---

### Post by Borniet on 2006-04-11
[QUOTE=Pum]Thank you for a quick answer . can I change the file only from the consoe?[/QUOTE]
No, depending on which filemanager you use (Konqueror (in KDE), Nautilus (Gnome)) you will be able to do this as well, IF you use your filemanager as root (with sudo). Easiest way I think is thus via the console :-)

---

### Post by Borniet on 2006-04-11
[QUOTE=Pum]How to change some file, they are read only. I wont to change some text inside some file. Thank you.[/QUOTE]
BTW: Before I forget: do not use the chmod method to change system files! If you need to change those, use 'sudo gedit' or 'sudo kate' (on kubuntu). Also, make sure you first save a copy of the systemfile you are about to edit.

---

### Post by Pum on 2006-04-11
:D ok thank you all for an answers. How can I change the dirrectory in console to get file that I need to change? And where I can find all newbie console commands.

---

### Post by Darkriser on 2006-04-11
either use full path (e.g. sudo gedit /etc/X11/xorg.conf)
or use cd command (change directory) - cd /etc/X11 and then sudo gedit xorg.conf.

for command reference use google - there are LOT of pages for newbies (e.g. [http://www.linuxcommand.org/](http://www.linuxcommand.org/))

---

