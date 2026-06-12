---
title: "how to put link to dektop in panel"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by sthapit on 2007-05-12
i just spent 15 minutes trying to put a link to my "home folder" (the thing you click on when you do Places -> Home Folder) on my panel haha.   Can someone help?

Speaking of which, is there a way to have the File browser hide hidden files always?  I like to have it in the "Tree" mode and I do "Control+H" to hide them, but each time I start the computer I have to do it again.

Thanks for any help!

---

### Post by starcraft.man on 2007-05-12
> **sthapit said:**
> i just spent 15 minutes trying to put a link to my "home folder" (the thing you click on when you do Places -> Home Folder) on my panel haha.   Can someone help?

Speaking of which, is there a way to have the File browser hide hidden files always?  I like to have it in the "Tree" mode and I do "Control+H" to hide them, but each time I start the computer I have to do it again.

Thanks for any help!

Just drag the home folder to your panel, it will stick to it. It will also go to desktop if you want it there.

If you want to hide the system files always, open nautilus (home folder is easy enough) then Edit > Preferences > show hidden and back up files, make sure that is unchecked.

Thats it, simple questions, have a nice day :)

---

### Post by canadianwriterman on 2007-05-12
If you are using Ubuntu with the Gnome desktop, just drag your home folder from the desktop onto the panel and it'll create a shortcut for you. For the Nautilus file browser, select File>Preferences>View and uncheck the show hidden files checkbox.

EDIT: Dang, you beat me to it starcraft.man!

---

### Post by bchaffin72 on 2007-05-12
Right click on task bar. Choose add to panel. Select Custom Application Launcher. For command, type nautilus. For icon, choose Gnome-home. That worked for me.

As to your second question I am not sure.

Edit: Everyone beat me to it.:)

---

### Post by Najand on 2007-05-12
1. Right Click on the panel
2. Select Add to panel
3. Select Custom Application Launcher
4. In the new window type:
> * Type: Application
* Name: Home Folder
* Command: nautilus --no-desktop
* Comment: Open your personal folder
5. Click on Icon
6. Select Home Icon at:
> /usr/share/icons/Human/48x48/places/gnome-fs-home.png

---

