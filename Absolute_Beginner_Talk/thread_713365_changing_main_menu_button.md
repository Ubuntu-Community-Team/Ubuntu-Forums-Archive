---
title: "changing main menu button"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by benjaminjames on 2008-03-02
hi all obviously a complete noob so i want to change the main menu button to one i have downloaded from gnome look i have saved it to my documents folder and i ran gconf editor and set to use custom icon but then i hit a wall i didnt know how to point it to my new icon i want to use i didnt see anywhere to put in the path name plus i was only following a step by step guide and have know idea how to do anything at the mo :) only been using 2 days so guys can anyone give me an idiots guide on how to change main menu icon? i have tried using the search tool on these forums but all the post i came across i either couldnt follow or they where of no help thanks all
btw im using 7.10

---

### Post by benjaminjames on 2008-03-02
. ok so i found another guide that showed me how to replace the original main menu icon in the human theme with my own but when i go to paste the new icon i want into the usr/share/icons/youricontheme/22×22/ i get the following message Error while copying to "/usr/share/...2x22/places" you do not have permission to write to this folder' how can i change this so that i have full permission top do this

---

### Post by Miller12 on 2008-03-02
I pretty sure you need to use
```
sudo gconf-editor
```
in the terminal

This is taken from TheRob on gnome-look:

Set the custom menu graphic, you need to open the Configuration Editor under the "System Tools" menu - or for you hardcore types, "gconf-editor" at the command line. Go to apps->panel->objects and you'll see a series of object_x subitems. Click through them until you find the one where the value for "object_type" is "menu-object". Check the "use_custom_icon" option and then set the "custom_icon" value to the path to your custom button graphic, i.e. "/home/username/Pictures/menu.png". The graphic should update immediately.

[edit] On second thought it might be gksudo but I am not at a Ubuntu machine right now to confirm that

---

