---
title: "Importing Bookmarks from Win to Ubuntu"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by newbie59 on 2007-03-10
Since I use Firefox as my browser in Ubuntu, can I import the bookmark file from Firefox in Windows to Firefox in Ubuntu?

---

### Post by steven8 on 2007-03-10
Yep.

If you have a FAT32 partition set up as swap, then you can export your bookmarks as an HTML file, save in the swap, and import them into Firefox in Ubuntu.

Or, export them to a disk and import them from the disk.

---

### Post by newbie59 on 2007-03-11
I'm still very new so saving to disk and importing is the way to go.
Thanks!!

---

### Post by ADH on 2007-07-22
I normally use eComStation as my OS, and the versions of Firefox and Seamonkey for OS/2.  I also have a Windows XP partition on NTFS, and I use the Win versions of Firefox and Seamonkey (more plugins available than for OS/2 versions, so I use these when I want to see something I couldn't using the OS/2 version.)  I recently was finally able to successfully install Ubuntu 7.04 onto my slave drive, so I'd like to get the bookmarks and stuff into Ubuntu's Firefox.

I have a Fat16 partition on my master drive which can be seen by both eCS and XP.  I copy my bookmarks and password files from eCS Firefox to that partition, and, when I boot to XP, I use a freeware file manager (like Norton Commander) to copy those files to the proper directories for the XP browsers to find them.  Linux doesn't have directory structure like eCS and XP, so I have no idea how to find where the bookmark and password files belong (I'd also like to set a text file on the Fat16 partition as my home page, which it is for the other OS' browsers, and don't know how to do that - I know nothing of Linux.)  How would I do these things?

Also, Firefox has been updated.  I looked at the Preferences, and it won't let me check the box to automatically look for Firefox updates, and I can't find a command from Firefox's menu to do it.  So how do I update Firefox?

Thanks as always for any help.

---

### Post by ADH on 2007-07-22
The Fat16 partition is /hda6, according to Gnome Commander.  The XP partition is /hda6.

Any way Firefox can find these files, save for the home page, from the XP partition?

---

### Post by ADH on 2007-07-22
I got the home page set up.  It is preceded /media/hda6/ before the filename.

---

### Post by zekopeko on 2007-07-22
here is a crazy, crazy idea:

use Foxmarks addon for Firefox. register at their site install the plugin from [https://addons.mozilla.org/en-US/firefox/addon/2410](https://addons.mozilla.org/en-US/firefox/addon/2410) on both win and ubuntu firefox and just syncronize them :D

---

### Post by ADH on 2007-07-23
I'll check it out.  That sounds like it will deal with the bookmarks, but not the passwords.

---

### Post by sacherjj on 2007-07-23
FoxMarks is great.  I use two Ubuntu systems and three Windows systems.  All 5 of my Firefox installs have synchronized bookmarks.  It works great.  Don't know about passwords.  I never save those on most sites.

---

### Post by aysiu on 2007-07-23
You can do even better than just the bookmarks. You can copy the entirety of your Firefox settings (history, passwords, themes, extensions, bookmarks) from Windows to Ubuntu. Copy 

C:\Document and Settings\*username*\**Application Data**\Mozilla 

to 

/home/*username*/**.mozilla**

The italicized part is your username. The bold parts are hidden folders.

---

### Post by por100pre1 on 2007-07-23
> **aysiu said:**
> You can do even better than just the bookmarks. You can copy the entirety of your Firefox settings (history, passwords, themes, extensions, bookmarks) from Windows to Ubuntu. Copy 

C:\Document and Settings\*username*\**Application Data**\Mozilla 

to 

/home/*username*/**.mozilla**

The italicized part is your username. The bold parts are hidden folders.

It's a good idea but not all files are 100% compatible... I know because I have done that.

---

### Post by asmoore82 on 2007-07-23
> **aysiu said:**
> You can do even better than just the bookmarks. You can copy the entirety of your Firefox settings (history, passwords, themes, extensions, bookmarks) from Windows to Ubuntu. Copy 

C:\Document and Settings\*username*\**Application Data**\Mozilla 

to 

/home/*username*/**.mozilla**

The italicized part is your username. The bold parts are hidden folders.

you could also just "Import" in firefox and browse ^^ there and pick up the "bookmarks.htm"
also, I think the folder for firefox settings changed from "mozilla" to "firefox" at version 2
but you could probably figure that out once you get past that nasty, hidden "App Data" stuff.

---

### Post by gw90se on 2007-07-23
You can also use Google Browser Sync. I use it between 4 boxes and haven't lost anything.

---

