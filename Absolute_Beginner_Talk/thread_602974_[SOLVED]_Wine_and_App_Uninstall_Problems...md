---
title: "[SOLVED] Wine and App Uninstall Problems.."
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by It_Was_Luck on 2007-11-04
Well i downloaded Wine, thinking if I don't like it I can just remove it. So I downloaded it and the first thing I got for it was iTunes, well the sound didn't even work so I figured I don't need wine to take up 100MB of space so i went to uninstall itunes (and quicktime) first so then i could uninstall wine but the uninstaller, whenever I ran it for itunes it was an installer! so it wouldn't uninstall so i thought I'll just get rid of wine. So i unistalled wine but i still have the folder in my applications list and itunes and quicktime are still there! so how do I remove them and uninstall them so they dont take up space on my already limited HD space computer?

---

### Post by houstonbofh on 2007-11-04
Manually delete the shortcuts, files, and the .wine directory in your home directory.

---

### Post by It_Was_Luck on 2007-11-04
I deleted the .wine directory but I don't know how to manually remove the shortcuts and stuff, I can't just right-click and press delete.

edit: well i did a search of my whole filesystem for "wine" and I got a ton of stuff so i went to delete it all and it says access dined. its in the usr/share/ folder...

---

### Post by Maestro23 on 2007-11-04
> **It_Was_Luck said:**
> I deleted the .wine directory but I don't know how to manually remove the shortcuts and stuff, I can't just right-click and press delete.

edit: well i did a search of my whole filesystem for "wine" and I got a ton of stuff so i went to delete it all and it says access dined. its in the usr/share/ folder...

**/usr** is owned by **root**.  You need root privileges to edit/delete/change anything in there.  Use **sudo** in command line or open Nautilus with **gksudo nautilus**.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by It_Was_Luck on 2007-11-04
Okay so how (after ive logged in as a root in the terminal) do I delete those files?

---

### Post by markharding557 on 2007-11-04
type nautilus on the command line and it will load up and you can delete your files.
be very careful though while using nautilus as root

---

### Post by daengbo on 2007-11-04
Before you delete files manually in the system area (always a bad idea for a new user), go to System -> Administration -> Synaptic Package manager.

Supply your password In the left pane, click to view packages by "Status"  and choose the "Not installed (residual config)" section. You'll find Wine in there.

Click on the square next to the wine package and choose "Mark for Complete Removal." This will remove all the configuration files which aren't removed by default (so you don't have to set everything up again if you reinstall). You won't have those system files anymore.

Next, for your menu, open Places -> Home and in the View menu, choose to "Show hidden files." Enter the .config/menus/applications-merged area and delete anything that starts with "wine." Your wine menu entry should be gone now.

Best of luck with your new Ubuntu.

p.s. Rhythmbox is a good replacement for iTunes and has the bonus of being the default player in Ubuntu. If you don't like RB, I understand Songbird is excellent.

---

### Post by It_Was_Luck on 2007-11-04
Worked great thank you...

---

