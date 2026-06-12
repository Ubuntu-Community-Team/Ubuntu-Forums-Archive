---
title: "[SOLVED] Kubuntu: shortcut to home on desktop"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by altonbr on 2006-09-26
I've made a shortcut on the desktop for my sister using "Create New..." >> "Link to Location (URL)" but how do you put the HOME shortcut on the desktop like you can in Gnome through gconf-editor?

Konqueror can't seem to do it either.

---

### Post by aysiu on 2006-09-26
You can create a launcher for the command: ```
konqueror --profile filemanagement
``` or the command ```
konqueror ~/
``` You could probably also just drag the home directory to the desktop and select **link here**.

---

### Post by Jucato on 2006-09-26
In the Link to location (URL) field, enter "~" or "home:/" (I prefer the ~). "~" is a sort of shortcut your (current user's) home folder.

---

### Post by altonbr on 2006-09-30
I don't seem to understand. I already have a URL Launcher set.. I'm trying to make an icon that says "Home" or "UserName" on the decktop like Gnome has in Ubuntu. (The computer icon... or hard drive icon... looks much better then a file that says "UserName")

Also, how do you place the trash can on the desktop?

The lack of right-clicking options in Kubuntu is VERY frustrating.
(I right click on the Trash Can, and it thinks I'm talking about the panel... and click on the Trash Can... see no options, so I go to properties, and all that dialogue contains are permissions and a calculator to find the size it is taking up... why can it not say "place on desktop"... and same with the Home icon.)

---

### Post by aysiu on 2006-09-30
Go to /home

Find the /home/altonbr folder and drag it to the desktop. Then select **link here**. There--you have a launcher.

Here's how you can put a trash on your desktop:
[http://wiki.kde.org/tiki-index.php?page=Trash#Trash_desktop_file](http://wiki.kde.org/tiki-index.php?page=Trash#Trash_desktop_file)

---

### Post by deeptingler on 2006-10-14
what altonbr is trying to say is that he has already created the link on the desktop but he doesnt want the icon to show a folder, but rather an icon of "home" eg house

---

### Post by altonbr on 2007-07-05
I don't use Kubuntu anymore... has this been fixed?

---

