---
title: "deluge not starting"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2008-02-21
I am using deluge, but recently deluge isen't starting. I click on it, and the thing comes up at the bottom saying starting deluge, but then nothing. I would like to continue downloading the files i am currently downloading if at all possible.

---

### Post by jan quark on 2008-02-21
try to run deluge through the terminal

are you getting any error message?

---

### Post by philinux on 2008-02-21
I've got mine set to minimise to notification area so all I see is it's icon there on starting it.

---

### Post by Falc7 on 2008-02-21
No error messages and it dosen't come up in the top right hand notification area

---

### Post by AndyCooll on 2008-02-21
The drastic measure is to delete the configuration folder which is a hidden folder in your home directory (/home/yourusername/.gconf/apps/deluge). Press CTRL+H when in Nautilus to reveal your hidden directories.

This will mean you'll lose any settings you've made manually and you'll have to re-input them. You won't lose your downloads, though Deluge will have to do a complete recheck of the files ...which can take awhile.

:cool:

---

### Post by Falc7 on 2008-02-21
what is nautilus and how do i start it?

---

### Post by AndyCooll on 2008-02-22
> **Falc7 said:**
> what is nautilus and how do i start it?

Apologies ...Nautilus is the name of the file manager (similar to Windows Explorer). So when you click Places > Home Folder what opens up is Nautilus.

:cool:

---

### Post by Falc7 on 2008-02-23
thanks for the help, i found the folder you meant, only problem is that it didn't have a deluge folder inside it.

---

### Post by Kosimo on 2008-02-23
> **Falc7 said:**
> thanks for the help, i found the folder you meant, only problem is that it didn't have a deluge folder inside it.

Go to your home folder:

Then press CONTROL + H  (It'll show the hidden files)

Then go down 'till you find the folders starting with a point (.)  

and find this rute

/.gconf /apps/deluge

---

### Post by Falc7 on 2008-02-23
Yep i found the hidden folder .gconfig, but there wasen't a folder, hidden or otherwise in here called deluge.

Should i uninstall deluge, and reinstall?

---

### Post by Kosimo on 2008-02-23
> **Falc7 said:**
> Yep i found the hidden folder .gconfig, but there wasen't a folder, hidden or otherwise in here called deluge.

Should i uninstall deluge, and reinstall?

try by open a terminal  and then write this:


sudo apt-get remove deluge



This will uninstall your deluge.

I recommend you to download the latest version from the official deluge website.

on here:  [http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)

then, get the Ubuntu package, it will simply install by making double click to the downloaded file.

---

### Post by mikewhatever on 2008-02-23
> **Falc7 said:**
> Yep i found the hidden folder .gconfig, but there wasen't a folder, hidden or otherwise in here called deluge.

Should i uninstall deluge, and reinstall?

Deluge settings are not in .gconf, but in .config/deluge, another hidden directory in your /home.

---

### Post by Falc7 on 2008-02-23
Ah yes you guys are right, i was looking in .gconfig, insead of .config
I tried deleting all the files, but that meant deluge didn't list all my downloads, which files should i leave in there so i can keep those?

---

### Post by wolfen69 on 2008-02-23
if you uninstall deluge and all settings, that will be fine. your partially downloaded files will still be there. just restart them and have them saved to the same folder. then it will check what you have and continue on.

---

