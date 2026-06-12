---
title: "How can I reset GNOME's Main Menu?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Sabretooth on 2007-09-07
While I went to fetch a drink, my friend went screwy with GNOME's Main Menu. Luckily, nothing's wrong in Places or System, but he managed to obliterate the Internet section from Applications. :(

I tried to Revert, but it didn't bring Internet back. He tried to drag the Internet to Other, because of which, I can see BitTorrent and Firefox in Other (Gaim's missing!) I've tried to bring them back, but adding all the apps back is a bit of a bore, and I'm facing probs with dragging entries from one section to another (I tried getting Firefox to a newly created Internet section, but it didn't work!)

So, is there any way to reset the Applications menu, do I have to reinstall some packages or something?

---

### Post by rsambuca on 2007-09-07
If you right-click the main menu, select "Edit Menus".  A window box will open up where you can select what you want to show up and in what order, etc.

---

### Post by aquavitae on 2007-09-07
You can reset the menu to default by deleting a file on your home drive.  Trouble is I'm not sure exactly which one - I generally use kde so I don't know how gnome stores its stuff.  But it should be something in ~/.gconf.  Hopefully it will be obvious what it is. Btw, you'll have to turn on "show hidden files" to see ~/.gconf

---

### Post by Sabretooth on 2007-09-07
Okay, after some snooping around, I've made my way to .gconf/apps/panel/objects/object_1. It has a file named "%gconf.xml". Contents below:

> <gconf>
<entry name="menu_path" mtime="1189144069" schema="/schemas/apps/panel/objects/menu_path"/>
<entry name="locked" mtime="1189144069" schema="/schemas/apps/panel/objects/locked"/>
<entry name="position" mtime="1189144069" schema="/schemas/apps/panel/objects/position" type="int" value="0">
        </entry>
&#8722;
	<entry name="object_type" mtime="1189144069" schema="/schemas/apps/panel/objects/object_type" type="string">
<stringvalue>menu-bar</stringvalue>
</entry>
<entry name="panel_right_stick" mtime="1189144069" schema="/schemas/apps/panel/objects/panel_right_stick" type="bool" value="false">
        </entry>
<entry name="use_menu_path" mtime="1189144069" schema="/schemas/apps/panel/objects/use_menu_path"/>
<entry name="launcher_location" mtime="1189144069" schema="/schemas/apps/panel/objects/launcher_location"/>
<entry name="custom_icon" mtime="1189144069" schema="/schemas/apps/panel/objects/custom_icon"/>
<entry name="tooltip" mtime="1189144069" schema="/schemas/apps/panel/objects/tooltip"/>
<entry name="action_type" mtime="1189144069" schema="/schemas/apps/panel/objects/action_type"/>
<entry name="use_custom_icon" mtime="1189144069" schema="/schemas/apps/panel/objects/use_custom_icon"/>
<entry name="attached_toplevel_id" mtime="1189144069" schema="/schemas/apps/panel/objects/attached_toplevel_id"/>
<entry name="bonobo_iid" mtime="1189144069" schema="/schemas/apps/panel/objects/bonobo_iid"/>
&#8722;
	<entry name="toplevel_id" mtime="1189144069" schema="/schemas/apps/panel/objects/toplevel_id" type="string">
<stringvalue>top_panel_screen0</stringvalue>
</entry>
</gconf>

So, I think it has something to do with the Menu, and this must be the file to delete. Is this it? Will I have to pull out my Ubuntu disk again if I delete this? ;)

---

### Post by banewman on 2007-09-07
I reset the menu entries from the control center or from system-preferences-main menu. Right clicking the icon for the main menu is a shorter way to get to it - instead of left click to open it, right click it. Then scroll to internet - click that and then in the right pane check firefox etc. :)

---

### Post by aquavitae on 2007-09-07
You can safely delete any config file in your home directory - if its missing linux will simply copy a new one from /usr.  This is basically what happens when you run a newly installed app.  E.g. install gimp, and on the first run it will create the folder ~/.gimp with a whole bunch of default settings in it.

Btw you could always juct move the file to your desktop.  If it turns out to be the wrong one, move it back.  You'll have to log out and back in again for anything to have any effect.

---

### Post by Sabretooth on 2007-09-07
Turns out that wasn't the right file. It just took off the Menu Bar from my panel, not the Main Menu. I have my Bar back, but looks like I'll need to hunt the Main Menu. I'm guessing it's not in Panel, but must be related to system. I'll go hunt ~/.gconf later, since I need to run right now.

Thanks guys, I'll return soon.

---

### Post by Sabretooth on 2007-09-07
Okay, I've deleted .gconf/desktop/gnome/applications/main-menu, but no effect. The folder is not there when I check back, but the Main Menu hasn't changed one bit. Open for suggestions again. :)

---

### Post by aquavitae on 2007-09-07
Try using grep (in a terminal) to search for something in the file. e.g. 
```
cd ~/.gconf
``` to change to the .gconf dir, followed by
```
grep -r "Applications" *
```
to find all files containing the text "Applications".
If you try it with the text of something unique in you menu you might find the file.  You could edit the menu, add an item called "this is a uniquely named item in my menu", save it, and then grep for "this is a uniquely named item in my menu".  There can't be too many files containing that!

---

### Post by rsambuca on 2007-09-07
Please re-read post number 2.

---

### Post by digitalbenji on 2007-09-07
I always just delete the entire .gnome directory, although you may lose other settings as well.

---

### Post by aquavitae on 2007-09-07
> **digitalbenji said:**
> I always just delete the entire **.gnome** directory, although you may lose other settings as well.Oh yes, It probably is ~/.gnome, not ~/.gconf!

---

### Post by Sabretooth on 2007-09-08
Yay! It worked!

The thing was actually in .config/menus. I deleted the whole menus folder. I think it included only edits to the main menu, because the contents of all the files inside the folder had my wrong menu. Now the folder's gone and my Main Menu is perfectly fine again!

@rsambuca: You probably didn't get my question right. Read my post again and try to piece together aquavitae's replies. :p

Thanks a bunch, everyone!

---

