---
title: "Help getting Desktop out .Trash!!"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by gazzadtfan on 2008-03-15
Hi

I'm having problems with my Desktop being in my .Trash folder. I don't know how it happened but only noticed it after emptying my Deleted Items folder. It then took all my shortcuts off my desktop and placed a Desktop shortcut in my Deleted Items folder. It leaves all my hard drives icons however on the Desktop!

Any time I try to add a shortcut it comes up with the error message 'Files & Folders can only be moved into the Deleted items Folder'

It's path is /home/gary/.Trash/Desktop

I did try following a previous thread but there was no conclusion, apart from "You'll work it out yourself".  I have tried to delete and re-install Ubuntu-Desktop as was suggested but it made no difference.

Does anyone have any ideas?

gazzadtfan

---

### Post by FuturePilot on 2008-03-15
Try opening the Trash and moving the Desktop folder into your Home folder.

---

### Post by banewman on 2008-03-15
Have you tried using nautilus to browse to /home/gary/.Trash and right clicking the Desktop folder and selecting "cut" then going back to /home/gary and right clicking and selecting "paste"?
:)

---

### Post by gazzadtfan on 2008-03-15
Hi

I tried dragging the desktop from the trash to my home folder but it returned to the Deleted Items Folder. 

As a matter of interest I already have another folder named 'Desktop' in my home folder which has all my shortcut icons within it!!

I didn't have any luck using Nautilus as I got the following message:

"/root/Desktop" cannot be moved because you do not have permissions to change it or its parent folder."

Any other ideas?

gazzadtfan

---

### Post by glennric on 2008-03-15
Somehow you changed the directory where gnome is looking for your Desktop to be in the trash.  To fix this type
```
gedit ~/.config/user-dirs.dirs
```
Find the line 
```
XDG_DESKTOP_DIR="$HOME/...
```
It probably reads XDG_DESKTOP_DIR="$HOME/.Trash/Desktop"
Take out the .Trash

---

### Post by gazzadtfan on 2008-03-15
Hi glennric

your suggestion hit the nail on the head. Much appreciated.

Many thanks for your help.

gazzadtfan

---

### Post by disraeli on 2008-03-16
Worked great! Thanks!

---

### Post by rocksocke on 2008-03-21
had the same problem and solved it with the given solution!

thanks!

---

