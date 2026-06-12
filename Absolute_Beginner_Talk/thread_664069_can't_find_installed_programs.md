---
title: "can't find installed programs"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by planC on 2008-01-10
Today i installed 'korganizer, and can't find it anywhere. I then installed gimmie pim, that had disappeared too. Where do they go??? :confused:

---

### Post by Blutack on 2008-01-10
They not in Applications menu?

---

### Post by Rocket2DMn on 2008-01-10
Try opening a terminal and running
```
whereis *appname*
```
If that fails, run
```
locate *appname*
``` which will show all files and directories with that name in it.  
Obviously, use the program name in substitute for appname.

Normally programs end up in /usr/bin or ~/bin

---

### Post by planC on 2008-01-10
This is all i get,  :ian@ian-desktop:~$ whereis korganizer
korganizer: /usr/bin/korganizer /usr/share/man/man1/korganizer.1.gz
ian@ian-desktop:~$ locate korganizer
/usr/share/app-install/desktop/korganizer.desktop
/usr/share/app-install/icons/korganizer.png
ian@ian-desktop:~$
It's not on the desk top....:confused:

---

### Post by Rocket2DMn on 2008-01-10
The launcher for the program is at "/usr/bin/korganizer"
You can make a launcher on your desktop by rightclicking the desktop and selecting Create Launcher and using that path as the command.

---

### Post by PeterJS on 2008-01-10
which is usually more useful than whereis.

Files on linux systems are laid out according to the Filesystem Hierarchy Standard. Here's the complete dry description straight from the author's mouth:
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

A far shorter and more readable version can be found on wikipedia:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)

---

### Post by planC on 2008-01-10
Thank you , i managed to put korganizer on the desk top but it isn't a pim, so i will try kontact, that should work.   If all else fails i can always go to k-mart and buy a calender!:):)

---

### Post by geekchicohio on 2008-01-10
with Automatix2 you can choose to install the Debian Menu (I'm POSITIVE you can install this other ways, but if you happen to use Automatix, this'd be an easy way).
The Debian Menu is a great way to find your various programs.

---

### Post by ubuntu-freak on 2008-01-11
Why automatix? Ubuntu includes the Debian menu already. Right click on the apps menu, click edit menus, then tick the Debian entry to enable.
 
However, if your menu editor is broken (mine is) then install KDE's (yes it works with GNOME menus).
 
sudo apt-get install kmenuedit
 
Then launch it by pressing alt+f2 and type in kmenuedit. 
 
If it still doesn't show paste these commands in the terminal 

sudo apt-get install menu menu-xdg 

sudo update-menus
 
Nathan

---

### Post by esva on 2008-01-11
what do I do to install the gnome menu in ubuntu ? I asked it in another thread, sorry for that, I can't find my applications on the menu bar of the panel. When gnome started the panel had nothing on it, I put the main menu there and it shows no applications in it

---

### Post by ubuntu-freak on 2008-01-11
Try alt-f2 then type xterm or gnome-terminal. 

Then type 

sudo update-menus

If that doesn't work type

sudo apt-get --reinstall install ubuntu-desktop 
 
Then reboot for full effect.

Nathan

---

### Post by ubuntu-freak on 2008-01-11
> **planC said:**
> Thank you , i managed to put korganizer on the desk top but it isn't a pim, so i will try kontact, that should work.   If all else fails i can always go to k-mart and buy a calender!:):)

Do you run gnome or kde? You can create your own menu entries in both gnome and kde with kmenuedit. You can usually do it with gnomes default editor but it's broken.
 
Nathan

---

