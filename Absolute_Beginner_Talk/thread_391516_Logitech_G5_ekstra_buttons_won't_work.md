---
title: "Logitech G5 ekstra buttons won't work"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by KriZo on 2007-03-23
Hi i have a problem with my Logitech G5 mouse, every thing is working except the thumbutton, I have google for at solution but that didn't help me. I found a guide the said i should write something in my xorg.conf file so i tried, but nothing happened. Heres what i typed in:

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "evdev"
	Option "CorePointer"
	Option "Name" "Logitech USB Gaming Mouse"
	Option "ZAxisMapping" "4 5 6 7"
	Option "Emulate3Buttons" "false"
EndSection


does anybody have a solution for my problem?

---

### Post by toecutter on 2007-03-23
Just copy and paste this info in: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Activate_side-mouse-buttons_in_FireFox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Activate_side-mouse-buttons_in_FireFox)

---

