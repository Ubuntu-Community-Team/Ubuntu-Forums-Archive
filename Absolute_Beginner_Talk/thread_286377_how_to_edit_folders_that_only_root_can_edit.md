---
title: "how to edit folders that only root can edit"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by willy1234x1 on 2006-10-27
so I'm trying to install the flashplayer 9 plugin on edgy and I find the /usr/lib/firefox/plugins but it tells me I don't have the permission to do so can I have quick explanation as to how to put the so file in the folder?

---

### Post by bulldog on 2006-10-27
Use sudo before you command,it gives you root permission for your command.

---

### Post by Tom_servo on 2006-10-27
Hi,
Use sudo in front of the command that should sort you out e.g.

sudo ./installer

I havent done the install myself but anything like that typically needs sudo to give permission to write to root owned files and directories.

---

### Post by JayTee on 2006-10-27
run gksudo nautilus. That'll give you a the gui file navigator with root priviledges. Be very very careful with it!!!!! That's the easy gui way.
or you can copy the file from the command line in a terminal using the cp command. i.e.
sudo cp ~./"pluginfilename.so" /usr/lib/firefox/plugins/"pluginfilename.so"

this assumes that your .so file is in the current folder. Otherwise if the file is currently in /home/yourusername/newfirefoxplugin
then you'd type:
sudo cp /home/yourusername/newfirefoxplugin/"pluginfilename".so /usr/lib/firefox/plugins/"pluginfilename.so"

---

### Post by ReaderRat on 2006-10-27
[How **sudo** Works](http://www.ubuntuforums.org/showthread.php?t=275605)

---

### Post by SirPecanGum on 2006-10-27
What about opening nautilus from the terminal with sudo: sudo nautilus

That will give you a root nautilus or use konqueror if you are in KDE.

Sorry... bit slow!

---

### Post by willy1234x1 on 2006-10-27
> **Tom_servo said:**
> Hi,
Use sudo in front of the command that should sort you out e.g.

sudo ./installer

I havent done the install myself but anything like that typically needs sudo to give permission to write to root owned files and directories.



it's not that it won't let me put a .so file in the folder and I want a quick way to get it in there since the flashplayer 7 plugin has no sound for me and it keeps telling me I don't have permission to move it into there

---

### Post by willy1234x1 on 2006-10-27
schweet I got it working it may be a beta but as soon as the full thing releases I'll do the same thanks guys

---

