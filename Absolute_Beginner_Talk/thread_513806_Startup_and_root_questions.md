---
title: "Startup and root questions"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by digital006 on 2007-07-30
When I start Ubuntu up I want to mount drives automatically, how do I do this? I can't seem to find the fstab file to edit.

Also I'm using Wicd to connect to the internet but it doesn't connect automatically is there a way of doing this at startup.

Finally I'm trying to migrate my firefox installation from WinXP to Ubuntu, I've mounted the drive but it won't copy the files accross, I've tried doing this as my user (has root priveledges) to no luck, I then tried to log in to root but my password wasn't recognised even though it is correct.

Any help is greatly appreciated.

Cheers,
Mike

---

### Post by Vague on 2007-07-30
Not sure about the other two, but I can answer your question about root.  The root account is disabled by default in Ubuntu.  It's recommended that you don't enable it.  You can gain root privileges by using the "sudo" command.  More on that here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Edit:  Oh yeah, I actually kinda do know the first one.  Your fstab is located at /etc/fstab

---

### Post by kevinlyfellow on 2007-07-30
> **digital006 said:**
> When I start Ubuntu up I want to mount drives automatically, how do I do this? I can't seem to find the fstab file to edit.


your fstab is in etc
```
sudo gedit /etc/fstab
```

Here's a quick guide to the file
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Automounting will depend on the filesystem.  So what types of filesystem to you want to automount?

---

### Post by john8791 on 2007-07-30
> **digital006 said:**
> When I start Ubuntu up I want to mount drives automatically, how do I do this? I can't seem to find the fstab file to edit.

Also I'm using Wicd to connect to the internet but it doesn't connect automatically is there a way of doing this at startup.

Finally I'm trying to migrate my firefox installation from WinXP to Ubuntu, I've mounted the drive but it won't copy the files accross, I've tried doing this as my user (has root priveledges) to no luck, I then tried to log in to root but my password wasn't recognised even though it is correct.

Any help is greatly appreciated.

Cheers,
Mike

You can edit the fstab file with "sudo nano /etc/fstab".  If your talking about mounting Windows NTFS volumes, an easy way is to install Automatix2 from:
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Automatix is a GUI interface to install all sorts of things not included in Ubuntu  like media CODECS.  It also has a script to install the ntfs-3g driver for NTFS read/write support.  It automatically adds lines to your /etc/fstab file.  I would make a backup first though in case something goes wrong, ie. "sudo cp /etc/fstab /etc/fstab.backup" or something like that.

What I did for Firefox to make my life easier was to install the "Foxmarks" add-on.  Rather than messing with copying your profile (bookmarks, etc) from XP to Linux,  Foxmarks stores your bookmarks on it's server and keeps them synchronized every time you open and close your browser. 

As far as your internet problem, I'm not familiar with Wicd.  Are you working with a dektop computyer or a laptop?   My desktop has a Netgear Wg311t pci wireless card and Ubuntu installed the correct driver on installation.  Have you done an "iwconfig" to see if your card has been detected?

---

### Post by imdano on 2007-07-31
If wicd starts automatically, you can make it connect automatically through wireless but checking the "automatically connect to this network" box in the entry for the wireless network you want to automatically connect to.  If it's wired, you'll have to get version 1.3.3 (if you're not using it already), and then you can either set wicd to automatically connect with a default wired profile or choose a profile each time it detects a wired connection.

If wicd doesn't start up with your computer, go to System->Preferences->Sessions.  Click the New button, and make an entry called Wicd with the command /opt/wicd/tray.py.

---

### Post by digital006 on 2007-07-31
Thank you so much! I finally have a working Linux system which is slowly replacing my install of WinXP!

---

