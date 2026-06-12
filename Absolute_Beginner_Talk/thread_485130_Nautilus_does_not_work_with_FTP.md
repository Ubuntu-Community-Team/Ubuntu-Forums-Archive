---
title: "Nautilus does not work with FTP????"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2007-06-26
When I tried to update my webpage I used the standard Gnome file viewer, Nautilius.  I typed the FTP address and it seemed to connect but nothing showed up on screen.  What other file browser would work similar to IE where you type http of ftp it just works?

I found a way of doing it with some Fireftp Mozilla plugin, but it is an extra step and the folder view does not give picture/file preview so it's a hassle.

Also, how to create a bookmark to a folder on desktop?  There is an option to add bookmarks in Nautilius but it's unnecessary step to open the file browser first and then clicking on bookmarks.

Thanx!!

---

### Post by phr0ze on 2007-06-26
Right click a folder and choose make link. Copy this new link file to the desktop.

Also, any bookmark is added automatically to the Places menu. You can just drag this off the places menu to the desktop.

---

### Post by bodhi.zazen on 2007-06-26
It is not what you want exactly, but I like gftp

---

### Post by Inxsible on 2007-06-26
> **bagrol1 said:**
> When I tried to update my webpage I used the standard Gnome file viewer, Nautilius. I typed the FTP address and it seemed to connect but nothing showed up on screen. What other file browser would work similar to IE where you type http of ftp it just works?
 
I found a way of doing it with some Fireftp Mozilla plugin, but it is an extra step and the folder view does not give picture/file preview so it's a hassle.
 
Also, how to create a bookmark to a folder on desktop? There is an option to add bookmarks in Nautilius but it's unnecessary step to open the file browser first and then clicking on bookmarks.
 
Thanx!!
 
Instead of creating a bookmark, you can create a launcher too. Right Click --> Create Launcher
 
Name the Command. Command will be ```
nautilus /pathToYourDirectory
```
Choose a nice icon for it and you are done.

---

### Post by eldepeche on 2007-06-26
I believe there is a "Connect to Server" entry in the Places menu. That should let you connect to FTP servers.

---

### Post by bagrol1 on 2007-06-27
I still have not got Nautilus to be able to access FTP correctly, but found out that Konqueror does the job fine.

My only gripe with Konqueror is that it does not remember the folder view settings, i.e., icon view for picture folders and tree for others.  Going to View-Mode and changing one type to another, changes the settings for all folders.

---

### Post by sudisk on 2007-07-02
Hello, I upgraded to feisty from edgy and the [COLOR="Red"]FTP[/COLOR] feature is broken in [COLOR="Red"]Nautilus[/COLOR] for me too. I did as bagrol1 and switched to Konqueror for my ftp works, though I'd rather not load KDE and Gnome in the same session.

Doesn't anyone have any clue about this?

---

### Post by TrioTorus on 2007-07-10
This problem still persist in Feisty. Anyone knows a workaround? Is there a bug report about this? I wish the gnome team would fully replace nautilus with thunar or similar. Nautilus seems to show too many hickups for production work unfortunately.

---

### Post by Golyadkin on 2007-07-10
Just use the "Connect to server" function, it works perfectly in Feisty.

---

