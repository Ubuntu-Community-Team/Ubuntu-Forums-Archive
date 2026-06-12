---
title: "how do i remove wine?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by -=Viper=- on 2007-07-27
Ok well i have deleted the .wine folder and i thought that would get rid of the wine folder on my applications tab.  It is still there though so i am going crazy.  Can someone tell me how to fix it?  Its ok if i cant cause then ill just do a fresh install :lolflag: but i really dont wana make ANOTHER festy disk cause all of mine are out on loan :(

---

### Post by earobinson on 2007-07-27
```
 sudo apt-get remove wine
``` or you can use synaptic and remove it using the gui!

---

### Post by kngunn on 2007-07-27
Did you install via apt-get?  If so, just 

sudo apt-get remove wine

Does that work?

If you just want to remove the Wine entry from your applications menu you can also use System | Preferences | Main Menu to remove it.

---

### Post by Mornedhel on 2007-07-27
Note that earobinson's method is the standard way.

We do *not* remove applications by deleting folders here, we don't.

---

### Post by qamelian on 2007-07-27
Right-click on the Applications menu and select Edit Menu. In the menu editor, drill down to the entries in the wine folder. RIght click on the entries and delete them When all entries have been deleted, the wine folder will no longer appear on your menu.

---

### Post by earobinson on 2007-07-27
> **Mornedhel said:**
> Note that earobinson's method is the standard way.

We do *not* remove applications by deleting folders here, we don't.
All deleating a fold (in your home directory) does is to remove your preferences file.

---

### Post by qamelian on 2007-07-27
> **Mornedhel said:**
> Note that earobinson's method is the standard way.

We do *not* remove applications by deleting folders here, we don't.

You do if you want to get rid of the programs you installed in wine. Uninstalling wine through any of the package managers still leaves the .wine folder containing any Windows apps you've installed in you home folder. To completely remove wine, you need to delete this folder.

---

### Post by Mornedhel on 2007-07-27
Ah, misread the OP.

My apologies.

If you want to remove the applications installed with Wine, removing .wine is indeed the way to go. Although there's now a "Wine Software Uninstaller".

I was thinking of removing Wine itself. Some newcomers expect that application installation/deletion is still done the Windows way (aka moving files to trash when the uninstaller doesn't work, and sometimes even when it does).

---

### Post by designwiz on 2007-07-27
I found this really easy for me hope it works for you

Uninstalling Wine Applications

Open up a terminal window and type "uninstaller" - this will open up a program similar to Windows' "add/remove programs" control panel, allowing you to uninstall applications from a Wine installation. Running uninstall programs directly via Wine should also work normally. Alternatively, you could also simply delete the folder of the application. However, as when done in Windows, this method will be "unclean" and will not remove the program's configuration from the Wine registry like using an uninstaller will. 

After uninstalling all wine apps then 
sudo apt-get remove wine

---

