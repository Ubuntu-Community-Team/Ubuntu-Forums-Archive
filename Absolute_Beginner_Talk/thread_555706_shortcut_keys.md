---
title: "shortcut keys"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by johnfarrow on 2007-09-20
How could I make a shortcut key combo to launch an Item from "Applications. Accessories"

---

### Post by olejorgen on 2007-09-20
You might want to try and search. Hint: the forum search sucks. If you want to use it, do advanced search on titles only. Else use google with site:ubuntuforums.org.

I'd recommend **xbindkeys**, but it can also be done with gnome directly

---

### Post by ncappel1 on 2007-09-20
Another method is to run the Configuration editor from applications->system tools ->configuration editor. 
if it is not in your menu run gconf-editor into a terminal.

then navigate to apps->metacity->global keybindings. there you will see "run command 1, 2, 3, etc." simply click on one of them and change the value to be the keys you want to press to activate the command. then edit the corresponding command in apps->metacity->Keybinding commands to have the name of the program you want to run.

is this clear?

note: to use the control and alt keys you have to label them as <Control><Alt>. so if you want a key binding to be, ctrl, alt, c, you will have to simply enter <Control><Alt>c
also: the arrow keys are up, down, left, right. Super_L is usually the "windows" key, and F1-12 are F1-F12

---

### Post by johnfarrow on 2007-09-20
its clear up to this part....."edit the corresponding command in apps->metacity->Keybinding commands to have the name of the program you want to run".

I put in <Control><Alt>g for gThumb Image Viewer.  What I put in the keybinding command block?

---

### Post by ncappel1 on 2007-09-21
I should clarify, if you enter in apps->metacity>global_keybindings and enter for example "<Alt>u" under "run command 1," then at this point you have mapped alt + u to run the command that you have entered into apps->metacity->keybinding_commands, under "command 1" (which could be any command you want, like the name of the program you want to run). 

does this make sense?

---

### Post by johnfarrow on 2007-09-22
Yes  it does.  And Thank You for your assistance.  However I can't seem to find the  right data to enter for Command_1.  When I Just enter the name of the program (gThumb Image Viewer), it doesn't work.  I guess I need to figure out the "Path" of the program and try that.:)

---

### Post by ncappel1 on 2007-09-22
I think the command for that program is just "gthumb" try that and see if it works.

---

### Post by johnfarrow on 2007-09-22
Hey!  That worked!  Thanks a million.

---

### Post by ncappel1 on 2007-09-22
cool beans, remember to mark the thread as "solved"

n

---

