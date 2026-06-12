---
title: "Self made icon help"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by ArthurHeng on 2005-11-14
Hi huys, Im trying to make a custom icon. I made a tiny .png file and placed it in /usr/share/pixmaps , it works for desktop icons, but not for taskbar icons (the smaller shortcut icon on the "applications, places, system bar"), so I saved it as xpm format and it still doesnt work, it says something like "icon not found" when I tried to select my xpm icon. Please tell me the correct way of doing it. Thanks in advance.

---

### Post by xmastree on 2005-11-14
Could it be a permission thing? I made one, 48x48 pixels PNG format, saved in /usr/share/pixmaps and it works fine in the panel.

The permissions are 644

---

### Post by ArthurHeng on 2005-11-14
Permission? You mean file size?

---

### Post by xmastree on 2005-11-14
[QUOTE=ArthurHeng]Permission? You mean file size?[/QUOTE]

No, I mean the permissions which allow certain users to access the files.
Let's say your file is called ubuntu.png and it's in /usr/share/pixmaps
type this in a terminal
```
ls -l /usr/share/pixmaps/ubuntu.png
```The response should look like```
-rw-r--r--  1 root root 1197 2005-06-10 13:46 /usr/share/pixmaps/ubuntu.png
```See that -rw-r--r-- bit? That's the permissions. root is the owner of the file. It's kinda confusing for a newbie, but you'll get used to it. If yours is root -rw------- then only root can access the file. Change it by typing ```
sudo chmod 644 /usr/share/pixmaps/ubuntu.png
```

However, if it works as a desktop icon I suspect that this may not be the problem. What are the pixel dimensions of the file?

---

### Post by ArthurHeng on 2005-11-14
I changed all of their permissions, it works now! Thanks a lot! Btw, what does 644 do? I did a "chmod a+r" earlier but it doesnt help.

---

### Post by ArthurHeng on 2005-11-15
Can someone tell me what does chmod 644 and chmod 755 do? I tried checking but most of them just directly tell me to use it without telling its purpose. thanks in advance

---

### Post by Sendervictorius on 2005-11-15
Best to use Nautilus to browse to your file. Then right-click on the file, and choose properties. The "Permissions" tab shows the permissions, breaking them down into "Owner", "Group" and "Others". These are the users controlled by the file permissions. The "Tick-boxes shown in Naulilus translate into binary numbers corresponding to read, write, and execute. So Read + write + execute = 111 in binary = 7 in decimal. Confused? then best to set permissions with Nautilus, rather than from the command line.:)

So: 644 translates to Read + write for the owner, read for the group, and read for anyone else
755 translates to read, write nd execute for the owner, read and execute for the group and others.
The chmod notation of a+r is just an alternate way of changing permissions.

---

### Post by xmastree on 2005-11-16
[QUOTE=ArthurHeng]Can someone tell me what does chmod 644 and chmod 755 do?[/QUOTE]There's a good explanation here: [http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

