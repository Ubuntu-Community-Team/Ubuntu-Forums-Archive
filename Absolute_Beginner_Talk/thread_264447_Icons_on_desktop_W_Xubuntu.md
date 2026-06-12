---
title: "Icons on desktop W/ Xubuntu"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Fooly Cooly on 2006-09-24
How can I put icons on desktop? Ex: Firefox Icon. I knew how to in Ubuntu, right clicking the icon in the menu and sending it to desktop. But that does not work in Xubuntu.

---

### Post by D10 on 2006-09-24
Add link to the application in the Desktop folder in your home directory.

---

### Post by Fooly Cooly on 2006-09-24
Im kinda new to ubuntu all together, just switched from XP Pro. How would you do that?

---

### Post by Wangsta on 2006-09-24
yeah, i'd like to know too.
the firefox icon it comes with is just a plain earth. how do i get it 1) with the fox on it and 2) an SVG instead of a pixely png?

---

### Post by chuckyp on 2006-09-24
Perhaps better fielded in the xubuntu forums?

---

### Post by nalmeth on 2006-09-24
Open the file manager (thunar), go to the Desktop directory, right-click, and hit create document -> empty file

paste this into the file
```
[Desktop Entry]
Comment=
Comment[en_US]=
Exec=firefox
GenericName=Browse the Web
GenericName[en_US]=Browse the Web
Icon=firefox
MimeType=
Name=Web Browser
Name[en_US]=Web Browser
Path=
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
```I know it seems kind of arcane, but I think the new version of thunar (not in the repositories) has improved in areas like this.

About the icon, you'll have to find a new icon on your own. It's easy, just google firefox, go to images, and select all small images. You'll find something nice. In this desktop file, enter the location of the new icon and you're set

---

### Post by Wangsta on 2006-09-24
woah, i totally dont understand. how any why would this change the firefox icon? and what am i supposed to save it as?

sorry, but is there really a seperate forum for xubuntu? i can't find it...

---

### Post by nalmeth on 2006-09-24
> **Wangsta said:**
> woah, i totally dont understand. how any why would this change the firefox icon? and what am i supposed to save it as?

sorry, but is there really a seperate forum for xubuntu? i can't find it...
That was for the original poster. But if you read the file carefully, look for:
ICON=firefox

It automatically looks in /usr/share/pixmaps. Copy your new icon there, and state the name without the extension.

ICON=newfirefox

---

### Post by Wangsta on 2006-09-26
> **chuckyp said:**
> Perhaps better fielded in the xubuntu forums?

IS there a xubuntu forum?

---

### Post by d4ndy on 2006-09-26
> IS there a xubuntu forum?

Well, there's [http://www.linuxforums.org/forum/ubuntu-help/60773-xubuntu.html](http://www.linuxforums.org/forum/ubuntu-help/60773-xubuntu.html), which is another linux forum.

A quick search hereabouts only found me [thread=177679]this[/thread] dead thread from last May.

But, if you're talking about re-iconizing the browser icon in the panel top-of-the-screen next to Applications, I found you can right-click/properties the icon, and third row down has a change-icon option. Show it the way to the icon you want (probably somewhere in usr/share/pixmaps?), and presto!

Good luck!

---

### Post by altonbr on 2006-10-08
And here is a link to the a post regarding replacing your Firefox and Thunderbird icons: [http://ubuntuforums.org/showthread.php?t=19919]("http://ubuntuforums.org/showthread.php?t=19919")

They say you can't ship Firefox with the icons because the license is not free. So use this script instead.

---

### Post by ruraltodd on 2006-10-08
> **Fooly Cooly said:**
> Im kinda new to ubuntu all together, just switched from XP Pro. How would you do that?

a newbie too but have computer opera evolution mail folders on desktop by just dragging from the panel so i put what i wanted on the panel then dragged it to the desktop - the only one that won't drag to desktop is the recycle bin which is ok on the panel - i have a total transform look like vista if you are interested i can send a capture to your email and the download for the transform changes icon looks panel bar wallpaper - hope this is helpful - ruraltodd

---

