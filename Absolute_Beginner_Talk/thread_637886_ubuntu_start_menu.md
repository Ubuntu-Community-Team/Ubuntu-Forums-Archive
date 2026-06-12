---
title: "ubuntu start menu"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by chips24 on 2007-12-11
how do you change the icon for the start menu

---

### Post by CaptainInsaneO on 2007-12-11
There is no start menu in Ubuntu, therefore there is no icon to change. Sorry. :(

---

### Post by philinux on 2007-12-11
If he means the icon next to Applications then yes you can.

[http://www.pendrivelinux.com/2007/10/19/changing-the-ubuntu-start-menu-panel-icon/](http://www.pendrivelinux.com/2007/10/19/changing-the-ubuntu-start-menu-panel-icon/)

---

### Post by chips24 on 2007-12-11
how do you change the apperence of the menu that pops up when u press the menu icon?

---

### Post by PhoenixP3K on 2007-12-11
> **CaptainInsaneO said:**
> There is no start menu in Ubuntu, therefore there is no icon to change. Sorry. :(
What do you mean no start menu? You can add a "main menu" to the applet bar. I was desperate to save some space. I know, I looks like the layout you have in XP and Vista :( Can you blame someone against productivity?

---

### Post by CaptainInsaneO on 2007-12-11
Sorry I was unaware.

Talk about beating a dead horse.

---

### Post by chips24 on 2007-12-17
how do you change the popup menu from the start menu?

---

### Post by nowshining on 2007-12-17
if u mean add/removing program icons/folders, adding folders/removing them, right click on top of the menu of any name and select edit, :)

if u'd like to change to a single menu icon only right click any blank area of the taskbar/panel and select add to panel find (if i remember correctly) main menu, and place it anywhere u want it, create a new panel add/remove icons there too :) u can put em' anywhere u want em to, to remove the places, system, applications default menu, right click anywhere on it and  select remove from panel.

if u want to move the panel to the bottom just drag it to the bottom.


to move it into another place, just select the menu item icon/name in the editing of the menus and drag it into the desired folder, u'll get a copy and to hide a specific icon/shortcut just unheck it. :) To delete an menu item, right click on it and select delete, to remove a folder make sure u select the top main folder where the arrow points down example, to delete the internet folder select Applications at top and find the folder and right click and delete. If u'd like to return to the default menus and if u make a mistake click the button at bottom entitled revert.

---

### Post by kahrytan on 2007-12-17
> **chips24 said:**
> how do you change the popup menu from the start menu?

If you want a start menu like Linux Mint Menu,
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=51127&d=1195830118[/IMG]

 then check out this [forum posting ]("http://ubuntuforums.org/showthread.php?t=621000") ([http://ubuntuforums.org/showthread.php?t=621000](http://ubuntuforums.org/showthread.php?t=621000))

---

### Post by nowshining on 2007-12-17
also a note from that webpage on changing the icons, u don't have to kill the gnome-panel and u don't have to put it into that main folder u can put it into any folder..

make an icon or get one, put it in a static place

open up system tools --> configuration editor, if not then alt+f2 and type gconf-editor

find /apps/panel/objects/

find one named menu-object on the left pane side by object_type

scroll down check mark use_custom_icon

scroll up find custom_icon and double click it and in the bottom input the location to ur new icon incl. the file extension. click ok and now it should be changed, exit out of the gconf-editor and ur done.

thanks kahrytan i as well will check out that post. oh and the icon itself will auto size itself so no need to worry about the size, but make it small for size and RAM sake. :P

---

### Post by wiscoteiger on 2007-12-18
Thanks that really helped me out :D

---

### Post by nowshining on 2007-12-18
welp guys i tried out the linux mint menu - okay at first and all amazing then get boring and i switched back to the ol' one i had.

---

