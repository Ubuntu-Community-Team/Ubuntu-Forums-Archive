---
title: "&quot;Move to Trash&quot; keyboard shortcut?"
date: 2010-05-05
forum: Apple Hardware Users
---

### Post by Jheric on 2010-05-05
Aluminum Macobook 5,1, on Ubuntu 10.04

I'm quite happy with my set up now... there's really just one issue that's been nagging at me. "Move to Trash"

I would greatly like a keyboard shortcut for this... but unfortunately, there is no "delete" button on the mac keyboard (well... there IS, but it functions as backspace).

I would like to set up a keyboard shortcut, but I don't know what the command is to "move to trash" as opposed to simply removing a file. Anyone know how I can do this? I just want to get ctrl-del (I have command mapped to ctrl) to move files to trash like in OS X.

---

### Post by paulinchen on 2010-05-05
The keyboard shortcut for the Delete button is function + backspace. 


If you like to have another shortcut, the easiest way should be to write a script, in which you move the current file to desktop
(something like: mv {file} ~/.local/share/Trash ...)
And then add this script to a shorcut you like at the Control Center.

---

