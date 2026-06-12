---
title: "editing xorg.conf"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-14
I started using XFce, it's great, but in order to configure hebrew writing to work the I need to edit a few lines in the xorg.conf file.

I go into the terminal, 
> su josh
password:******

> gedit /etc/x11/xorg.conf

It comes up with an empty file, as if the file doesn't exist.
When I go manually to the folder I can open the file, but obviously I can't edit it.

I tried copying the contents of the file I found manually and pasting it in the empty file it had come up with, but it doesn't save.

I thought maybe it was because I didn't create a backup to the xorg.conf file, as I've done with the souces.list file. So I tried

> cp /etc/x11/xorg.conf /etc/x11/xorg.conf_backup
It says
> cp: cannot stat `/etc/x11/xorg.conf': No such file or directory


I tried doing the same with "sudo" before it, it also didn't work.

what else can I try? I really want to use XFce, but I can't without hebrew...

Thanks,
Josh:)

---

### Post by Prefader on 2006-04-14
That's a capital "X" . . .

gedit /etc/X11/xorg.conf

Don't bonk your head too much over it, I make this sort of mistake *all* the time.

---

### Post by fng on 2006-04-14
In a linux filesystem, all files and directories are case sensitive.
A file called joe ins't the same as a file called JoE.  They are both 2 different files.

You are trying to edit the file /etc/x11/xorg.conf. The directory /etc/x11 doesn't exist. It's /etc/**X**11 (with a capital x).

try :
```
gedit /etc/X11/xorg.conf
```

---

### Post by Caligula on 2006-04-14
How stupid could I have been??
anyway, I figured that out already, thanks anyway...
Everything works now, I using XFce and it's great!:D

---

