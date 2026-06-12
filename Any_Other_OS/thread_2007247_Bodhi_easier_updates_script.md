---
title: "Bodhi easier updates script"
date: 2012-06-20
forum: Any Other OS
---

### Post by black veils on 2012-06-20
if you want to keep the system light by doing software updates through the terminal, but want to make it easier, you could do the following.

_[SIZE=3][COLOR=DarkSlateBlue]**create a script**[/COLOR][/SIZE]_

open a text editor, paste this in

```
#!/bin/bash

sudo apt-get update && sudo apt-get upgrade (or dist-upgrade)
```edit the command to your liking.

save with the extension .sh, for example **updates.sh**

right-click the file, and make it executable.

put the file in  **/home/username/.local/share/applications**


_[SIZE=3][COLOR=DarkSlateBlue]**create a launcher**[/COLOR][/SIZE]_[SIZE=3]
[/SIZE] 
this will act like any other application menu entry, which you can create shortcuts and launchers from.

open your text editor again, paste this in

```
[Desktop Entry]
Name=Software Updates
Type=Application
Exec=xterm -hold -e /path/to/script.sh
Icon=/path/to/icon
StartupNotify=false
Terminal=false
Categories=System;
```edit the lines starting **Exec** and **Icon** to the correct paths, you may also want to change **Name** and **Categories**.

save with the extension .desktop, for example **Software Updates.desktop**

put the file in  [B]/home/username/.local/share/applications


[/B]now you can create a launcher, with a specified icon, it will open the terminal, ask for your password, and then run those commands. system icons are located at **/usr/share/icons**

---

