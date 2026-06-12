---
title: "login problems"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Freeman163 on 2007-06-04
I usually use the dvorak keyboard layout, and ubuntu is set to it while running, but whenever I login, it recognizes it as qwerty, so i have to plug in my other keyboard. any idea why /how to fix? Thanks for your time

---

### Post by oilchangeguy on 2007-06-04
have you tried, system ,preferences, keyboard?

---

### Post by Freeman163 on 2007-06-04
yes, its all set up and running nicely after login, its only during login that i have the problem

---

### Post by Rocket2DMn on 2007-06-04
I think some keyboard info is declared in xorg.conf
let us know what you see in there relating to the keyboard

---

### Post by Freeman163 on 2007-06-04
err... how might i discover that information?

---

### Post by Rocket2DMn on 2007-06-04
in terminal: 
"sudo gedit /etc/X11/xorg.conf"
type in your password when prompted and check in the InputDevice sections.  You can post the whole file if you'd like, but we really just need the keyboard related info.

---

### Post by Freeman163 on 2007-06-04
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

that should be the section

---

### Post by Rocket2DMn on 2007-06-04
I'm not keyboard expert, but according to [http://www.doomtech.net/wiki/index.php/Dvorak_Simplified_Keyboard]("http://www.doomtech.net/wiki/index.php/Dvorak_Simplified_Keyboard")

> Option "XkbLayout" "us"
should be set to 
> Option "XkbLayout" "dvorak"

No guarantees, but good luck!

---

### Post by Freeman163 on 2007-06-04
nope, it doesnt work. thanks though

on an unrelated note, are there ms paint-esqe apps for ubuntu?

---

### Post by Rocket2DMn on 2007-06-04
well, you can try just googling the problem, surely somebody else out there has had that issue.  there are other boards like linuxforums.org that are good.
Happy hunting.

---

### Post by Freeman163 on 2007-06-04
alright, thanks anyway. ill post if i find anything here, for anyone else with the same issue, few as we dvorak users are

---

### Post by Freeman163 on 2007-06-04
ah, it appears a mistake was made!
the solution provided does work, but you must restart the computer entirely instead of merely logging out. Thanks for all your support!

---

