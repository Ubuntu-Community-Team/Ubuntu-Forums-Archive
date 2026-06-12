---
title: "Program works but launcher does not?"
date: 2014-02-16
forum: Any Other OS
---

### Post by megazell2 on 2014-02-16
Hey,

I am using Linux Mint 15 - 32 Bit - Cinnamon.

I dl'ed and installed the program - Stencyl. It works when I got into the installation directory and click it. It works when I start it from terminal.

It does not seem to work when I create a launcher for it.

I double checked the launcher properities and .desktop file and everything seems to be in order but I am quite stumped as to why this program will not work via launcher.

Any tips and/or help would be greatly appericated.

Cheers,
Megazell

---

### Post by monkeybrain20122 on 2014-02-16
Well did you enable your .desktop file to be executed as a program?

---

### Post by deadflowr on 2014-02-16
Post what the launcher (.desktop) file says.

---

### Post by Bucky Ball on 2014-02-16
*Thread moved to **Other OS/Distro Support**.*

Linux Mint is not supported in the main support areas of this forum. Thanks and good luck.

---

### Post by megazell2 on 2014-02-17
> **monkeybrain20122 said:**
> Well did you enable your .desktop file to be executed as a program?

Yes I did.

> **deadflowr said:**
> Post what the launcher (.desktop) file says.

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/home/megazell/Games/Game Making Programs/Stencyl/games/Space Shooter/ios-icon.png
Name[en_US]=Stencyl
Exec="/home/megazell/Games/Game Making Programs/Stencyl/Stencyl"
Name=Stencyl
Icon=/home/megazell/Games/Game Making Programs/Stencyl/games/Space Shooter/ios-icon.png

---

### Post by deadflowr on 2014-02-17
Have you tried removing the top line?
Making the [Desktop Entry] line the top one.

---

### Post by megazell2 on 2014-02-18
> **deadflowr said:**
> Have you tried removing the top line?
Making the [Desktop Entry] line the top one.

Just did. Still not opening.

---

### Post by deadflowr on 2014-02-18
Maybe try breaking it down to the basics
from this
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/home/megazell/Games/Game Making Programs/Stencyl/games/Space Shooter/ios-icon.png
Name[en_US]=Stencyl
Exec="/home/megazell/Games/Game Making Programs/Stencyl/Stencyl"
Name=Stencyl
Icon=/home/megazell/Games/Game Making Programs/Stencyl/games/Space Shooter/ios-icon.png 				
```
to this
```
[Desktop Entry]
Name=Stencyl
Exec="/home/megazell/Games/Game Making Programs/Stencyl/Stencyl"
Icon=/home/megazell/Games/Game Making Programs/Stencyl/games/Space Shooter/ios-icon.png 				
Type=Application
```
That's all you actually need, see if the added crud was causing any issues.
I don't think it would, but you never know.
If anything, maybe add
Terminal=true
See what that does.

---

