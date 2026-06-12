---
title: "keyboard shortcuts in gedit messed up"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by caughran on 2007-11-05
Somehow, I've changed the gedit new file key. Control+n, or control+shift+n, do not create a new document. The file menu shows V in the shortcut columns, which is unlikely and doesn't work either.

How can I change this back?

---

### Post by spupy on 2007-11-05
In the settings menu in GNOME, in the control panel named "Menus & Toolbars", there is an option called "Editable menu shortcuts". When it is enabled, you can change the menu shortcuts in gtk programs. You probably enabled it and changed the shortcuts by mistake.   To change them back, in gedit, open the "File" menu (for example), point the mouse to the menu line in question and press the shortcut you want to be assigned to that menu entry. But first make sure that "Editable menu shortcuts" in "Menus & Toolbars" is enabled. Even if you disable it, changed shortcuts will remain changed.

---

### Post by caughran on 2007-11-05
[INDENT]"In the settings menu in GNOME, in the control panel named "Menus & Toolbars", there is an option called "Editable menu shortcuts". When it is enabled, you can change the menu shortcuts in gtk programs. You probably enabled it and changed the shortcuts by mistake. To change them back, in gedit, open the "File" menu (for example), point the mouse to the menu line in question and press the shortcut you want to be assigned to that menu entry. But first make sure that "Editable menu shortcuts" in "Menus & Toolbars" is enabled. Even if you disable it, changed shortcuts will remain changed."[/INDENT]

Some problems -
[LIST]
[*]The program sometimes says alt+A is a new document, sometimes V. When it says V, nothing aside from alt+F,N or the toolbar creates a new document. 
[*]I haven't noticed the problem in other applications; is the fix above for all applications?
[*]Under system/preferences, there is a "main menu" program, which only edits menus, a keyboard preferences which deals with layouts, etc., and a Keyboard Shortcuts program that deals with global problems like launching programs, etc.
[*]All of which is rather confusing.
[/LIST]
This is not a critical item, but it would be nice to resolve it.

---

### Post by spupy on 2007-11-05
> **caughran said:**
> 
[*]I haven't noticed the problem in other applications; is the fix above for all applications?

No, you must change all shortcuts by hand. But if that is the case, most probably only a couple of shortcuts are messed up. 
> **caughran said:**
> 
[*]Under system/preferences, there is a "main menu" program, which only edits menus, a keyboard preferences which deals with layouts, etc., and a Keyboard Shortcuts program that deals with global problems like launching programs, etc.
The program is called "gnome-ui-properties". I don't know where in GNOME you can find it, i use only GNOMEs control panel, not gnome itself.

---

### Post by caughran on 2007-11-05
Thanks for your effort.

---

### Post by caughran on 2007-12-25
there is a file, [FONT="Courier New"]/home/jim/.gnome2/accels/gedit[/FONT], which contains the shortcut keys. I edited it, hoping it would change the keys. Instead, it seems to be a file generated to show what the keys are. (For what?)

It contains the entries which are messed up:
[FONT="Courier New"](gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/FileNew" "v")[/FONT]

and so forth. All the lines for keys not messed are preceded by ; to comment them out.

As soon as I close gedit and reopen, the file is replaced, as it was before.

sudo gedit brings up a gedit with the proper keys, so somewhere in my area, there is a configuration file with the improper keys. Where?

I'd like to revert to the original keys. Does anyone know how to change them?

---

### Post by caughran on 2008-01-14
Solved. gedit acts weirdly. If I open a menu, then type a key or combination which does not appear on the menu, the highlighted item gets that key as its shortcut.

Weird. Do other gnome apps act this way?

---

