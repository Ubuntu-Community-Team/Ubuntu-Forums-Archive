---
title: "How to Show the Trash Bin on the Desktop in Ubuntu?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by neno on 2006-12-14
Can someone help me?
thanks...  >_<

---

### Post by BitTorrentBuddha on 2006-12-14
One way is to rename or remove the Desktop directory and then link .Trash to Desktop. To do this, first open nautilus as superuser: ```
sudo nautilus
``` then navigate to your home folder and rename or remove the "Desktop" directory (I simply renamed mine to Desktop2.)

Then, for the second part, linking .Trash to Desktop, run this command:```
ln -s .Trash/ ~/Desktop
``` Then, while viewing your desktop, press F5, you should see the contents of your trash.

---

### Post by kelbizzle on 2006-12-14
Open terminal and type:
```
sudo gconf-editor
```

then navigate to apps ->Nautilus ->Desktop, after that just click variable trash_icon_visible.

---

### Post by neno on 2006-12-14
> **BitTorrentBuddha said:**
> One way is to rename or remove the Desktop directory and then link .Trash to Desktop. To do this, first open nautilus as superuser: ```
sudo nautilus
``` then navigate to your home folder and rename or remove the "Desktop" directory (I simply renamed mine to Desktop2.)

Then, for the second part, linking .Trash to Desktop, run this command:```
ln -s .Trash/ ~/Desktop
``` Then, while viewing your desktop, press F5, you should see the contents of your trash.

thanks...
but I want to show the trash bin just like Windwos
have an Trash bin icon on the Desktop

---

### Post by sailor2001 on 2006-12-14
> **neno said:**
> thanks...
but I want to show the trash bin just like Windwos
have an Trash bin icon on the Desktop

right click the panel bar and and "add to panel" and click on the trash icon

---

### Post by ButteBlues on 2006-12-14
> **neno said:**
> thanks...
but I want to show the trash bin just like Windwos
have an Trash bin icon on the Desktop
Do what kelbizzle said; it's right.

---

### Post by PatrickMay16 on 2006-12-14
Kelbizzle is right, that is how to put the trashcan icon on the desktop.
> 
 	Open terminal and type:

sudo gconf-editor

then navigate to apps ->Nautilus ->Desktop, after that just click variable trash_icon_visible.


---

### Post by ButteBlues on 2006-12-14
Note: Sudo is not required for that command. :)

---

### Post by Bobtheknight on 2006-12-14
Woo woo, maybe you didn't notice, but trash is on the lower right-hand corner of your screen.  On the windows bar, beside the workspaces.  

It is on mine.

---

### Post by ButteBlues on 2006-12-14
That'd be the panel applet. It is possible to have an icon on the desktop as well. ;)

---

### Post by jpeddicord on 2006-12-14
Here is a screenie of GConf with the trash option selected, and proof of it (and other various icons) on my desktop. ;)

---

### Post by BitTorrentBuddha on 2006-12-14
Ahh, my method is completely different from what you are looking for I see.

---

### Post by bugz0r on 2006-12-17
Is there any way to change the Trash icon in properties. I can do it for every other icon but not the trash.

---

